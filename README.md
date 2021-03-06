# Reactive polyglot

**`R.`** [(Ramda)](http://ramdajs.com/0.19.1/index.html) stands for standard functional toolkit.

## Operators

Current ordering is subjective: from most common operators to less common.<br/>
Operator counterparts are not expected to be fully equivalent.<br/>
"Kinda the same" is the current definition.

Presence of operator is not "good" as well as abscence is not "bad".<br/> 
Every decision has it's own benefits and drawbacks.
Remember, that we're trying to make analogies over systems which were be designed
with different goals / philosophies in mind.

### Create

Create stream from non-stream values.

<table>
<tr>
  <th>Elm</th>
  <th>KefirJS</th>
  <th>MostJS</th>
  <th>RxJS</th>
  <th>XStream</th>
</tr>
<tr>
  <td><code>Signal.constant</code></td>
  <td><code>constant</code></td>
  <td><code>of / just</code></td>
  <td><code>just</code></td>
  <td><code>of</code></td>
</tr>
<tr>
  <td>?</td>
  <td><code>– (sequentially)</code></td>
  <td><code>– (from)</code></td>
  <td><code>of</code></td>
  <td><code>of</code></td>
</tr>
<tr>
  <td>?</td>
  <td><code>– (sequentially)</code></td>
  <td><code>from</code></td>
  <td><code>from</code></td>
  <td>?</td>
</tr>
<tr>
  <td>?</td>
  <td><code>fromEvents</code></td>
  <td><code>fromEvent</code></td>
  <td><code>fromEvent</code></td>
  <td><code>fromEvent</code></td>
</tr>
<tr>
  <td>?</td>
  <td><code>fromPromise</code></td>
  <td><code>fromPromise</code></td>
  <td><code>fromPromise</code></td>
  <td><code>fromPromise</code></td>
</tr>
<tr>
  <td><code>Time.every</code></td>
  <td><code>interval</code></td>
  <td><code>periodic</code></td>
  <td><code>interval + map</code></td>
  <td><code>periodic</code></td>
</tr>
<tr>
  <td><code>–</code></td>
  <td><code>repeat</code></td>
  <td><code>of + R.range</code></td>
  <td><code>repeat</code></td>
  <td><code>of + R.range</code></td>
</tr>
<tr>
  <td><code>–</code></td>
  <td><code>?</code></td>
  <td><code>iterate</code></td>
  <td><code>generate</code></td>
  <td>?</td>
</tr>
<tr>
  <td><code>–</code></td>
  <td><code>?</code></td>
  <td><code>generate</code></td>
  <td><code>generate</code></td>
  <td>?</td>
</tr>
</table>

### Mapper

Modify events one to one.

<table>
<tr>
  <th>Elm</th>
  <th>KefirJS</th>
  <th>MostJS</th>
  <th>RxJS</th>
  <th>XStream</th>
</tr>
<tr>
  <td><code>Signal.map</code></td>
  <td><code>map</code></td>
  <td><code>map</code></td>
  <td><code>map</code></td>
  <td><code>map</code></td>
</tr>
<tr>
  <td><code>– (Signal.map)</code></td>
  <td><code>– (map)</code></td>
  <td><code>constant</code></td>
  <td><code>mapTo</code></td>
  <td><code>mapTo</code></td>
</tr>
<tr>
  <td><code>Time.delay</code></td>
  <td><code>delay</code></td>
  <td><code>delay</code></td>
  <td><code>delay</code></td>
  <td><code>combine(delay(500))</code></td>
</tr>
<tr>
  <td><code>Time.timestamp</code></td>
  <td><code>– (map)</code></td>
  <td><code>timestamp</code></td>
  <td><code>timestamp</code></td>
  <td><code>– (map)</code></td>
</tr>
</table>

### Transforms

Modify events * to *.

<table>
<tr>
  <th>Elm</th>
  <th>MostJS</th>
  <th>RxJS</th>
  <th>XStream</th>
</tr>
<tr>
  <td><code>Signal.foldp</code></td>
  <td><code>scan</code></td>
  <td><code>scan</code></td>
  <td><code>fold</code></td>
</tr>
<tr>
  <td><code>– (Signal.filterMap)</code></td>
  <td><code>chain / flatMap</code></td>
  <td><code>flatMap</code></td>
  <td><code>map + flattenConcurrently</code></td>
</tr>
<tr>
  <td><code>?</code></td>
  <td><code>map + switch</code></td>
  <td><code>switchMap / flatMapLatest</code></td>
  <td><code>map + flatten</code></td>
</tr>
<tr>
  <td>?</td>
  <td><code>concatMap</code></td>
  <td><code>concatMap</code></td>
  <td><code>flattenSequentially</code></td>
</tr>
<tr>
  <td>?</td>
  <td><code>join</code></td>
  <td><code>mergeAll</code></td>
  <td><code>flatten</code></td>
</tr>
<tr>
  <td><code>foldp + map</code></td>
  <td><code>loop</code></td>
  <td><code>scan + map</code></td>
  <td><code>scan + map</code></td>
</tr>
<tr>
  <td>?</td>
  <td><code>– (<a href="bufferWithCount.md">custom</a>)</code></td>
  <td><code>bufferWithCount</code></td>
  <td>?</td>
</tr>
</table>

### Filters

Skip events by predicate or signal.

<table>
<tr>
  <th>Elm</th>
  <th>MostJS</th>
  <th>RxJS</th>
  <th>XStream</th>
</tr>
<tr>
  <td><code>Signal.filter</code></td>
  <td><code>filter</code></td>
  <td><code>filter</code></td>
  <td><code>filter</code></td>
</tr>
<tr>
  <td><code>Signal.dropRepeats</code></td>
  <td><code>skipRepeats</code></td>
  <td><code>distinctUntilChanged</code></td>
  <td><code>dropRepeats</code></td>
</tr>
<tr>
  <td>?</td>
  <td><code>skipRepeatsWith</code></td>
  <td><code>– (scan)</code></td>
  <td><code>dropRepeats</code></td>
</tr>
<tr>
  <td>?</td>
  <td><code>skip</code></td>
  <td><code>skip</code></td>
  <td><code>drop</code></td>
</tr>
<tr>
  <td>?</td>
  <td><code>take</code></td>
  <td><code>take</code></td>
  <td><code>take</code></td>
</tr>
<tr>
  <td>?</td>
  <td><code>slice</code></td>
  <td><code>skip + take</code></td>
  <td><code>drop + take</code></td>
</tr>
<tr>
  <td>?</td>
  <td><code>skipWhile</code></td>
  <td><code>skipWhile</code></td>
  <td><code>fold + filter + map</code></td>
</tr>
<tr>
  <td>?</td>
  <td><code>takeWhile</code></td>
  <td><code>takeWhile</code></td>
  <td><code>filter + endWhen</code></td>
</tr>
<tr>
  <td>?</td>
  <td><code>since / skipUntil</code></td>
  <td><code>skipUntil</code></td>
  <td><code>fold + filter + map</code></td>
</tr>
<tr>
  <td>?</td>
  <td><code>until / takeUntil</code></td>
  <td><code>takeUntil</code></td>
  <td><code>filter + endWhen</code></td>
</tr>
<tr>
  <td>?</td>
  <td><code>during</code></td>
  <td><code>window + take(1)</code></td>
  <td>?</td>
</tr>
</table>

### Combinators

Combine multiple streams into single.

<table>
<tr>
  <th>Elm</th>
  <th>MostJS</th>
  <th>RxJS</th>
  <th>XStream</th>
</tr>
<tr>
  <td><code>Signal.merge / Signal.mergeMany</code></td>
  <td><code>merge</code></td>
  <td><code>merge</code></td>
  <td><code>merge</code></td>
</tr>
<tr>
  <td><code>Signal.map2 / Signal.map3...</code></td>
  <td><code>combine</code></td>
  <td><code>combineLatest</code></td>
  <td><code>combine</code></td>
</tr>
<tr>
  <td><code>Signal.sampleOn</code></td>
  <td><code>sample</code></td>
  <td><code>withLatestFrom</code></td>
  <td>?</td>
</tr>
<tr>
  <td><code>Signal.sampleOn + Time.every</code></td>
  <td><code>sampleWith</code></td>
  <td><code>sample</code></td>
  <td>?</td>
</tr>
<tr>
  <td>?</td>
  <td><code>zip</code></td>
  <td><code>zip</code></td>
  <td>?</td>
</tr>
<tr>
  <td>?</td>
  <td><code>concat</code></td>
  <td><code>concat</code></td>
  <td>?</td>
</tr>
<tr>
  <td>?</td>
  <td><code>ap</code></td>
  <td><code>combineLatest</code></td>
  <td>?</td>
</tr>
</table>

### Side effects 

Produce side effect for every event.

<table>
<tr>
  <th>MostJS</th>
  <th>RxJS</th>
  <th>XStream</th>
</tr>
<tr>
  <td><code>tap</code></td>
  <td><code>do / tap</code></td>
  <td><code>debug</code></td>
</tr>
</table>

### Ending

Operators which target **end** event somehow.

<table>
<tr>
  <th>MostJS</th>
  <th>RxJS</th>
  <th>XStream</th>
</tr>
<tr>
  <td><code>empty</code></td>
  <td><code>empty</code></td>
  <td><code>empty</code></td>
</tr>
<tr>
  <td><code>never</code></td>
  <td><code>never</code></td>
  <td><code>never</code></td>
</tr>
<tr>
  <td><code>continueWith</code></td>
  <td><code>?</code></td>
  <td><code>concat</code></td>
</tr>
</table>

### Concurrency

<table>
<tr>
  <th>MostJS</th>
  <th>RxJS</th>
</tr>
<tr>
  <td><code>– (<a href="https://github.com/ivan-kleshnin/reactive-polyglot/wiki/race">custom</a>)</code></td>
  <td><code>amb / race</code></td>
</tr>
</table>

### History

<table>
<tr>
  <th>MostJS</th>
  <th>RxJS</th>
</tr>
<tr>
  <td colspan="2"><code>– (<a href="history.md">custom</a>)</code></td>
</tr>
</table>

### Design diffs

#### RxJS

1. Three primitives: `Observer`, `Observable`, `Subject`. 
2. Observables end on error.
3. Provides API to handle errors.
3. Does not provide API to handle ending.

#### KefirJS

1. Two primitives: `Stream` and `Property`. Properties have "current value" notion.
2. Observables does not end on error (by default).
3. Provides API to handle errors.
4. Provides API to handle ending.

#### MostJS

1. One primitive: `Stream`.
2. Separate packages for [subject-like](https://github.com/TylorS/most-subject) and [property-like](https://github.com/mostjs/hold https://github.com/mostjs/hold) primitives.
3. Provides API to handle errors.
4. Provides API to handle ending.

#### Common

RxJS does not emit initial `scan` value as event (use `startWith` for that).

```js
Rx.Observable.interval(100).map(x => 1)
  .scan(add, 0);
  .subscribe(console.log); // 1--2--3--...

Most.periodic(100, 1)
  .scan(add, 0);
  .observe(console.log); // 0--1--2--3--...
```

### Found docs / API quirks

#### MostJS 

`startWith` vs `sampleWith` vs `continueWith` + `recoverWith` vs `skipRepeatsWith`<br/>
(val vs none vs func vs stream)

`tap` is listed in "Transform" section.

#### RxJS

`startWith` is listed in "Combine" section.

`mergeAll` is listed in "Combine" section.

`distinct` is not listed in "Filtering" section.

`takeUntil` is not listed in "Filtering" section.

`just` / `return` should be deprecated in favor of `of`.

`fromArray` should be deprecated in favor of `from`.

### Links

[bacon-vs-kefir](https://github.com/rpominov/kefir/blob/master/bacon-vs-kefir-api.md) – BaconJS vs KefirJS API comparison

[dataflows](https://github.com/ivan-kleshnin/dataflows) – web arch. dataflow comparison

[stream-conversions](https://github.com/TylorS/stream-conversions) – tool for cross-library stream conversions

### Additional Read

https://github.com/cujojs/most/issues/171

https://twitter.com/rpominov/status/689566111734599683

https://github.com/zenparsing/es-observable/issues/66
