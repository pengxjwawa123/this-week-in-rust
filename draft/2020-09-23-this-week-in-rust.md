Title: This Week in Rust 357
Number: 357
Date: 2020-09-23
Category: This Week in Rust

Hello and welcome to another issue of *This Week in Rust*!
[Rust](http://rust-lang.org) is a systems language pursuing the trifecta: safety, concurrency, and speed.
This is a weekly summary of its progress and community.
Want something mentioned? Tweet us at [@ThisWeekInRust](https://twitter.com/ThisWeekInRust) or [send us a pull request](https://github.com/emberian/this-week-in-rust).
Want to get involved? [We love contributions](https://github.com/rust-lang/rust/blob/master/CONTRIBUTING.md).

*This Week in Rust* is openly developed [on GitHub](https://github.com/emberian/this-week-in-rust).
If you find any errors in this week's issue, [please submit a PR](https://github.com/emberian/this-week-in-rust/pulls).

# Updates from Rust Community

No newsletters this week.

### Official

### Tooling

### Observations/Thoughts

* [Async Iteration Semantics](https://blog.yoshuawuyts.com/async-iteration/)
* [Porting EBU-R128 audio loudness analysis from C to Rust](https://coaxion.net/blog/2020/09/porting-ebu-r128-audio-loudness-analysis-from-c-to-rust/)
* [Potential improvements for Rust embedded abstractions](https://tweedegolf.nl/blog/42/potential-improvements-for-rust-embedded-abstractions)
* [I started to learn Rust](https://jean.manguy.eu/post/i-started-to-learn-rust/)
* [Rust in Science and ever-changing requirements](https://amanjeev.com/blog/rust-in-science-and-ever-changing-requirements)

### Learn Standard Rust
* [TL;DR Rust](https://christine.website/blog/TLDR-rust-2020-09-19)
* [Variables And Mutability In Rust](https://edfloreshz.blog/variables-and-mutability)

### Learn More Rust
* [Dynamic Iterators](https://hole.tuziwo.info/dyn-iterator.html)
* [Low-Level Academy](https://lowlvl.org/)
* [Writing an HTTP(S) Tunnel in Rust with tokio.](https://medium.com/@xnuter/writing-a-modern-http-s-tunnel-in-rust-56e70d898700)
* [Down the Yak Hole of TLS](https://blog.drogue.io/yak-hole-of-tls/)

### Project Updates

### Miscellaneous

* [Porting PineTime Watch Face from C to Rust On RIOT with LVGL](https://lupyuen.github.io/pinetime-rust-riot/articles/watch_face)

# Call for Blog Posts

The Rust Core Team wants input from the community!
If you haven't already, [read the official blog](https://blog.rust-lang.org/2020/09/03/Planning-2021-Roadmap.html) and submit a blog post - it will show up here!
Here are the wonderful submissions since the call for blog posts:

# Crate of the Week

This week's crate is [gitoxide](https://github.com/Byron/gitoxide), an idiomatic, modern, lean, fast, safe & pure Rust implementation of git.

Thanks again to [Vlad Frolov](https://users.rust-lang.org/t/crate-of-the-week/2704/812) for the suggestion!

[Submit your suggestions and votes for next week][submit_crate]!

[submit_crate]: https://users.rust-lang.org/t/crate-of-the-week/2704

# Call for Participation

Always wanted to contribute to open-source projects but didn't know where to start?
Every week we highlight some tasks from the Rust community for you to pick and get started!

Some of these tasks may also have mentors available, visit the task page for more information.

If you are a Rust project owner and are looking for contributors, please submit tasks [here][guidelines].

[guidelines]: https://users.rust-lang.org/t/twir-call-for-participation/4821

# Updates from Rust Core

336 pull requests were [merged in the last week][merged]

[merged]: https://github.com/search?q=is%3Apr+org%3Arust-lang+is%3Amerged+merged%3A2020-09-07..2020-09-14

* [add rust-dev component to support rustc development](https://github.com/rust-lang/rust/pull/76332)
* [properly encode spans with a dummy location and non-root `SyntaxContext`](https://github.com/rust-lang/rust/pull/76658)
* [add `const_item_mutation` lint](https://github.com/rust-lang/rust/pull/75573)
* [more structured suggestions for boxed trait objects instead of impl Trait on non-coerceable tail expressions](https://github.com/rust-lang/rust/pull/75608)
* [add help note when using type in place of const](https://github.com/rust-lang/rust/pull/75611)
* [do not promote `&mut` of a non-ZST ever](https://github.com/rust-lang/rust/pull/75585)
* [chalk: simplify lowering](https://github.com/rust-lang/chalk/pull/602)
* [inliner: emit storage markers for introduced arg temporaries](https://github.com/rust-lang/rust/pull/76123)
* [enable the `SimplifyArmIdentity` MIR optimization at `mir-opt-level=1`](https://github.com/rust-lang/rust/pull/76308)
* [stabilize `doc_alias`](https://github.com/rust-lang/rust/pull/75740)
* [stabilize `core::future::`{`pending`,`ready`}](https://github.com/rust-lang/rust/pull/74328)
* [add saturating methods for `Duration`](https://github.com/rust-lang/rust/pull/76114)
* [add `slice::array_chunks_mut`](https://github.com/rust-lang/rust/pull/75021)
* [eliminate mut reference UB in `Drop` impl for `Rc<T>`](https://github.com/rust-lang/rust/pull/76530)
* [`BTreeMap` mutable iterators should not take any reference to visited nodes during iteration](https://github.com/rust-lang/rust/pull/73971)
* [`BTreeMap`: move up reference to map's root from `NodeRef`](https://github.com/rust-lang/rust/pull/74437)
* [add `drain_filter` method to `HashMap` and `HashSet`](https://github.com/rust-lang/rust/pull/76458)
* [arch: AVX512F](https://github.com/rust-lang/stdarch/pull/896)
* [add `MaybeUninit::assume_init_drop`](https://github.com/rust-lang/rust/pull/76484)
* [remove internal and unstable `MaybeUninit::UNINIT`](https://github.com/rust-lang/rust/pull/76527)
* [cargo: fix non-determinism with new feature resolver](https://github.com/rust-lang/cargo/pull/8701)

## Rust Compiler Performance Triage

* [2020-09-21](https://github.com/rust-lang/rustc-perf/blob/master/triage/2020-09-21.md):
  2 Regressions, 5 Improvements, 4 Mixed

This was the first week of semi-automated perf triage, and thank goodness:
There was a lot going on. Most regressions are either quite small or already
have a fix published.

[#72412](https://github.com/rust-lang/rust/issues/72412) is probably the most
interesting case. It fixes a pathological problem involving nested closures by
adding cycle detection to what seems to be a relatively hot part of the code.
As a result, most users will see a slight [compile-time
regression](https://perf.rust-lang.org/compare.html?start=2c69266c0697b0c0b34abea62cba1a1d3c59c90c&end=fdc3405c20122fd0f077f5a77addabc873f20e4c&stat=task-clock)
for their crates.

See the [full report](https://github.com/rust-lang/rustc-perf/blob/master/triage/2020-09-21.md) for more.

## Approved RFCs

Changes to Rust follow the Rust [RFC (request for comments) process](https://github.com/rust-lang/rfcs#rust-rfcs). These
are the RFCs that were approved for implementation this week:

* [[RFC]: Portable SIMD Libs Project Group](https://github.com/rust-lang/rfcs/pull/2977)
* [Establish a new error handling project group](https://github.com/rust-lang/rfcs/pull/2965)

## Final Comment Period

Every week [the team](https://www.rust-lang.org/team.html) announces the
'final comment period' for RFCs and key PRs which are reaching a
decision. Express your opinions now.

### [RFCs](https://github.com/rust-lang/rfcs/labels/final-comment-period)
* [Get type of an arbitrary expression](https://github.com/rust-lang/rfcs/pull/2706)
* [Add generalized arity tuples](https://github.com/rust-lang/rfcs/pull/2702)

### [Tracking Issues & PRs](https://github.com/rust-lang/rust/labels/final-comment-period)

* [disposition: merge][Make RawFd implement the RawFd traits](https://github.com/rust-lang/rust/pull/76969)
* [disposition: merge][Permit uninhabited enums to cast into ints](https://github.com/rust-lang/rust/pull/76199)
* [disposition: merge][Stabilize move_ref_pattern](https://github.com/rust-lang/rust/pull/76119)
* [disposition: merge][Write manifest for MAJOR.MINOR channel to enable rustup convenience](https://github.com/rust-lang/rust/pull/76107)
* [disposition: merge][Explicitly document the size guarantees that Option makes.](https://github.com/rust-lang/rust/pull/75454)
* [disposition: merge][Stabilize intra-doc links](https://github.com/rust-lang/rust/pull/74430)
* [disposition: merge][Add PartialEq impls for Vec <-> slice](https://github.com/rust-lang/rust/pull/74194)
* [disposition: merge][target-feature 1.1: should closures inherit target-feature annotations?](https://github.com/rust-lang/rust/issues/73631)
* [disposition: merge][might_permit_raw_init: also check aggregate fields](https://github.com/rust-lang/rust/pull/71274)

## New RFCs

* [RFC 2582: fix implicit auto-deref of raw pointers](https://github.com/rust-lang/rfcs/pull/2987)
* [Stable Rustdoc URLs](https://github.com/rust-lang/rfcs/pull/2988)

# Upcoming Events

### Online
* [September 29. Dallas, TX, US - Dallas Rust - Last Tuesday](https://www.meetup.com/Dallas-Rust/events/jqxqwrybcmbmc/)
* [October 1. Berlin, DE - Berline.rs - Rust Hack and Learn](https://www.meetup.com/opentechschool-berlin/events/txcprrybcnbcb/)

### Asia Pacific
* [October 5. Auckland, NZ - Rust AKL - Rust meetup](https://www.meetup.com/rust-akl/events/266876708/)

If you are running a Rust event please add it to the [calendar] to get
it mentioned here. Please remember to add a link to the event too.
Email the [Rust Community Team][community] for access.

[calendar]: https://www.google.com/calendar/embed?src=apd9vmbc22egenmtu5l6c5jbfc%40group.calendar.google.com
[community]: mailto:community-team@rust-lang.org

# Rust Jobs

* [Backend Engineer, Kraken Futures - Rust at Kraken (London, UK, EU)](https://jobs.lever.co/kraken/fe1e07f4-6d7c-4f65-9a8f-27cf3b3fd2b1)
* [Backend / Quant Developer at Kraken (Remote EU)](https://jobs.lever.co/kraken/9d9cc4b5-ef5f-40bd-b785-9acf9164aa74)
* [Senior Software Development Engineer - AWS EC2 at Amazon (Arlington, VA, US)](https://www.amazon.jobs/en/jobs/1273617/senior-software-development-engineer-aws-ec2)
* [Wasm Compiler Engineer at Parity (Berlin, DE, London, UK, Remote)](https://www.parity.io/apply/?gh_jid=4170712003)

*Tweet us at [@ThisWeekInRust](https://twitter.com/ThisWeekInRust) to get your job offers listed here!*

# Quote of the Week

> When you have a lifetime `<'a>` on a struct, that lifetime denotes references to values stored *outside* of the struct. If you try to store a reference that points inside the struct rather than outside, you will run into a compiler error when the compiler notices you **lied** to it.

- [Alice Ryhl on rust-users](https://users.rust-lang.org/t/how-to-resolve-error-e0499-cannot-borrow-as-mutable-more-than-once-at-a-time-in-this-case/48815/3)

Thanks to [Tom Phinney](https://users.rust-lang.org/t/twir-quote-of-the-week/328/939) for the suggestion!

[Please submit quotes and vote for next week!](https://users.rust-lang.org/t/twir-quote-of-the-week/328)

*This Week in Rust is edited by: [nellshamrell](https://github.com/nellshamrell), [llogiq](https://github.com/llogiq), and [cdmistman](https://github.com/cdmistman).*

<small>[Discuss on r/rust](https://www.reddit.com/r/rust/comments/iu3ge0/this_week_in_rust_356/)</small>