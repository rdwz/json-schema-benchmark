# json-schema-benchmark
Performance benchmark for Node.js JSON-schema validators.

Also tests against [official JSON-schema test suite](https://github.com/json-schema/JSON-Schema-Test-Suite) and checks
for validators that cause side-effects on schema or data.

[Contribute to these benchmarks](https://github.com/ebdrup/json-schema-benchmark/blob/master/CONTRIBUTING.md)

# Performance

![performance](https://chart.googleapis.com/chart?chxt=x,y&cht=bhs&chco=76A4FB&chls=2.0&chbh=62,4,1&chs=600x416&chxl=-1:|@exodus&#x2F;schemasafe|ajv|is-my-json-valid|z-schema|@cfworker&#x2F;json-schema|jsonschema&chd=t:100,82.3,53,4.3,2.3,0.7)

|Validator|Relative speed|Number of test runs per second|
|---------|:------------:|:----------------------------:|
|[`@exodus/schemasafe`](https://github.com/ExodusMovement/schemasafe)|100%|40604 (± 0.1%)|
|[`ajv`](https://github.com/ajv-validator/ajv)|82.3%|33428 (± 0.56%)|
|[`is-my-json-valid`](https://github.com/mafintosh/is-my-json-valid#readme)|53%|21527 (± 0.11%)|
|[`z-schema`](https://github.com/zaggino/z-schema)|4.3%|1752 (± 0.72%)|
|[`@cfworker/json-schema`](https://github.com/cfworker/cfworker/tree/master/packages/json-schema/README.md)|2.3%|929 (± 1.5%)|
|[`jsonschema`](https://github.com/tdegrunt/jsonschema#readme)|0.7%|294 (± 1.09%)|

235 tests are run in each test run.

Validators tested: [`json-schema-validator-generator (1.1.11)`](https://github.com/danwang/json-schema-validator-generator), [`is-my-json-valid (2.20.5)`](https://github.com/mafintosh/is-my-json-valid#readme), [`jsen (0.6.6)`](https://github.com/bugventure/jsen), [`ajv (6.12.6)`](https://github.com/ajv-validator/ajv), [`themis (1.1.6)`](https://github.com/playlyfe/themis), [`z-schema (5.0.0)`](https://github.com/zaggino/z-schema), [`jjv (1.0.2)`](https://github.com/acornejo/jjv), [`djv (2.1.3-alpha.0)`](https://github.com/korzio/djv#readme), [`skeemas (1.2.5)`](https://github.com/Prestaul/skeemas#readme), [`schemasaurus (0.7.8)`](https://github.com/AlexeyGrishin/schemasaurus), [`jsck (0.3.2)`](https://github.com/pandastrike/jsck#readme), [`jassi (0.1.2)`](https://github.com/iclanzan/jassi), [`JSV (4.0.2)`](http://github.com/garycourt/JSV), [`request-validator (0.3.3)`](https://github.com/bugventure/request-validator), [`json-gate (0.8.23)`](https://github.com/oferei/json-gate#readme), [`json-model (0.2.24)`](https://github.com/geraintluff/json-model), [`tv4 (1.3.0)`](https://github.com/geraintluff/tv4), [`jsonschema (1.4.0)`](https://github.com/tdegrunt/jsonschema#readme), [`revalidator (0.3.1)`](https://github.com/flatiron/revalidator), [`json-schema-library (4.1.4)`](https://github.com/sagold/json-schema-library), [`@exodus/schemasafe (1.0.0-rc.3)`](https://github.com/ExodusMovement/schemasafe), [`@cfworker/json-schema (1.6.3)`](https://github.com/cfworker/cfworker/tree/master/packages/json-schema/README.md), 

(validators not in the results above where excluded because of failing tests - see below for details)

[`@exodus/schemasafe`](https://github.com/ExodusMovement/schemasafe) is currently the fastest JSON-schema validator out there.

The fastest validator has 100%, the rest a lower score relative to the fastest.
If a validator has a score of 5% that means that it's speed is 5% of the fastest,
meaning that it's 20 times slower than the fastest.

# Test failure summary

This test suite uses the [official JSON-schema test suite](https://github.com/json-schema/JSON-Schema-Test-Suite).

If a validator does not pass a test in the official test suite, it will show up in these results.

![failing tests](https://chart.googleapis.com/chart?chxt=x,y&cht=bhs&chco=76A4FB&chls=2.0&chbh=14,4,1&chs=600x416&chxl=-1:|@exodus&#x2F;schemasafe|jsonschema|@cfworker&#x2F;json-schema|ajv|z-schema|is-my-json-valid|jsen|json-schema-library|jsck|themis|tv4|skeemas|schemasaurus|request-validator|djv|jassi|jjv|json-schema-validator-generator|json-model|JSV|json-gate|revalidator&chd=t:9,14,15,21,22,27,38,38,55,59,70,76,77,81,87,87,88,92,124,145,229,297&chxr=0,0,297&chds=0,297)

|Validator|Number of failing tests (click for details)|
|---------|-----------------------|
|[`@exodus/schemasafe`](https://github.com/ExodusMovement/schemasafe)|[9](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/@exodus&#x2F;schemasafe.md)|
|[`jsonschema`](https://github.com/tdegrunt/jsonschema#readme)|[14](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/jsonschema.md)|
|[`@cfworker/json-schema`](https://github.com/cfworker/cfworker/tree/master/packages/json-schema/README.md)|[15](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/@cfworker&#x2F;json-schema.md)|
|[`ajv`](https://github.com/ajv-validator/ajv)|[21](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/ajv.md)|
|[`z-schema`](https://github.com/zaggino/z-schema)|[22](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/z-schema.md)|
|[`is-my-json-valid`](https://github.com/mafintosh/is-my-json-valid#readme)|[27](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/is-my-json-valid.md)|
|[`jsen`](https://github.com/bugventure/jsen)|[38](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/jsen.md)|
|[`json-schema-library`](https://github.com/sagold/json-schema-library)|[38](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/json-schema-library.md)|
|[`jsck`](https://github.com/pandastrike/jsck#readme)|[55](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/jsck.md)|
|[`themis`](https://github.com/playlyfe/themis)|[59](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/themis.md)|
|[`tv4`](https://github.com/geraintluff/tv4)|[70](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/tv4.md)|
|[`skeemas`](https://github.com/Prestaul/skeemas#readme)|[76](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/skeemas.md)|
|[`schemasaurus`](https://github.com/AlexeyGrishin/schemasaurus)|[77](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/schemasaurus.md)|
|[`request-validator`](https://github.com/bugventure/request-validator)|[81](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/request-validator.md)|
|[`djv`](https://github.com/korzio/djv#readme)|[87](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/djv.md)|
|[`jassi`](https://github.com/iclanzan/jassi)|[87](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/jassi.md)|
|[`jjv`](https://github.com/acornejo/jjv)|[88](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/jjv.md)|
|[`json-schema-validator-generator`](https://github.com/danwang/json-schema-validator-generator)|[92](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/json-schema-validator-generator.md)|
|[`json-model`](https://github.com/geraintluff/json-model)|[124](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/json-model.md)|
|[`JSV`](http://github.com/garycourt/JSV)|[145](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/JSV.md)|
|[`json-gate`](https://github.com/oferei/json-gate#readme)|[229](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/json-gate.md)|
|[`revalidator`](https://github.com/flatiron/revalidator)|[297](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/revalidator.md)|

Some validators have deliberately chosen not to support parts of the spec. Go to the homepage of the validator to learn if
that is the case for these tests.

# Side-effects summary

Number of tests that caused side-effects. The schema or data was altered by the validator.

|Validator|Number of side-effects (BAD)|
|---------|----------------------------|
|[`tv4`](https://github.com/geraintluff/tv4)|[13](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/tv4-side-effects.md)|
|[`revalidator`](https://github.com/flatiron/revalidator)|[645](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/revalidator-side-effects.md)|
|[`json-model`](https://github.com/geraintluff/json-model)|[668](https://github.com/ebdrup/json-schema-benchmark/blob/master/reports/json-model-side-effects.md)|

Validators not in the list have no side-effects on data or schemas.

# Features of validators

Note that these benchmarks and tests do not take into account other more advanced features of the validators. I encourage
you to take a look at each validator if you are looking for special features.

# Benchmarks by validator authors and others

Several of the validators have build benchmarks themselves. They are
more detailed then the benchmarks provided above.

[Benchmarks owned by themis](https://cdn.rawgit.com/playlyfe/themis/master/benchmark/results.html)

[Benchmarks owned by z-schema](https://rawgit.com/zaggino/z-schema/master/benchmark/results.html)

[Benchmarks owned by jsck](https://github.com/pandastrike/jsck/blob/master/doc/benchmarks.md)

There is also a [benchmark suite](https://github.com/Sembiance/cosmicrealms.com/tree/master/sandbox/benchmark-of-node-dot-js-json-validation-modules-part-3)
by cosmicrealms.

# License
MIT
