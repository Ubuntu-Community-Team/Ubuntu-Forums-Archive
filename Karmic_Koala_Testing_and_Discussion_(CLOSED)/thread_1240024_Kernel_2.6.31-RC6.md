---
title: "Kernel 2.6.31-RC6"
date: 2009-08-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by plun on 2009-08-14
Is available.

> DateThu, 13 Aug 2009 16:37:33 -0700 (PDT)

From  Linus Torvalds <>

Subject  Linux 2.6.31-rc6

Hmm. Lots of small fixes all over, spread out fairly evenly (50% drivers,
and roughly 10% each in arch, fs, kernel, tools/perf, "rest"). And things
do seem to be calming down, because outside of some further i915
displayport patches and a couple of perf-counter patches, almost all of
them are pretty dang small.

[ Which brings up git hint of the day, in case you want to see how to
get a feel for the size of the patches. Do something like:

git log v2.6.31-rc5.. --abbrev-commit --no-merges --pretty=oneline --shortstat

which shows the commit as a oneliner (with a shortened commit SHA),
followed by a numerical linelount of the diff. And all ignoring merges,
of course.

You'll see a lot of small one-liners etc, and it's fairly easy to pick
out the bigger ones either visually or with some trivial scripting ]

There's nothing hugely interesting there, although I'm personally
gratified by the fact that I have a few more commits than usual. Even if
they are all really small, it makes me feel useful

There's the NULL pointer fix that was already talked up on Slashdot, but
quite frankly, assuming we got all the "you can't map things at zero"
issues fixed from the last scare, that one hopefully wasn't quite as bad
as it could have been.
[ What was perhaps an interesting (if trivial) detail is that if it
hadn't been for vendor-sec apparently leaking like a sieve, we'd have
delayed the fix until the next -rc due to trying to be polite to
vendors.

So this may be one of the few time I'm actually happy about vendor-sec
(even if it's because it failed to work the way it's supposed to ,
since I heartily dislike embargoes. ]

Other than that? I suspect the Shortlog (below) gives a rough feel for the
kinds of things there are. The regression list has hopefully shrunk a bit
more (and it already looked much better as of -rc5 than it did earlier),
and so I suspect we're on target for a 2.6.31 release after -rc8 or so.

Please give it a good testing, update any regressions you notice (whether
they've changed status or not), and have fun,

Linus

[http://lkml.org/lkml/2009/8/13/549](http://lkml.org/lkml/2009/8/13/549)



Build ready at Ubuntu Mainline

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc6/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc6/)


--

---

### Post by plun on 2009-08-14
Karmic version uploaded (a big one)

[https://lists.ubuntu.com/archives/karmic-changes/2009-August/006208.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/006208.html)

---

### Post by rudenko_ruslan on 2009-08-14
Nice. I hope that I will get this update next morning. Thank you very much for info.

---

### Post by dino99 on 2009-08-15
Does it resolve this big problem:

Linux NULL pointer dereference due to incorrect proto_ops initializations 

[http://archives.neohapsis.com/archives/fulldisclosure/2009-08/0174.html](http://archives.neohapsis.com/archives/fulldisclosure/2009-08/0174.html)

---

### Post by plun on 2009-08-15
> **dino99 said:**
> Does it resolve this big problem:

Linux NULL pointer dereference due to incorrect proto_ops initializations 

[http://archives.neohapsis.com/archives/fulldisclosure/2009-08/0174.html](http://archives.neohapsis.com/archives/fulldisclosure/2009-08/0174.html)

Yes according to what Linus writes...

> 
There's the NULL pointer fix that was already talked up on Slashdot, but
quite frankly, assuming we got all the "you can't map things at zero"
issues fixed from the last scare, that one hopefully wasn't quite as bad
as it could have been.
[ What was perhaps an interesting (if trivial) detail is that if it
hadn't been for vendor-sec apparently leaking like a sieve, we'd have
delayed the fix until the next -rc due to trying to be polite to
vendors.

---

### Post by dino99 on 2009-08-15
Thanks Plun,
As the real problem is due to gcc, we have to wait they give us an updated release

---

### Post by plun on 2009-08-17
Metapackage uploaded for karmic

> linux-meta (2.6.31.6.17) karmic; urgency=low

  * Karmic ABI 6
  * Removed armel/imx51

[https://lists.ubuntu.com/archives/karmic-changes/2009-August/006406.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/006406.html)




No problems for me....

---

### Post by rudenko_ruslan on 2009-08-17
> **plun said:**
> No problems for me....
Yup, updated kernel few minutes ago, no problems here too.

---

### Post by dino99 on 2009-08-17
yes now it is complete.
curiously, only 31 kernel is updated, not 28 yet.

---

### Post by slakkie on 2009-08-17
I have problems with this kernel, FF3.5 and Flash. Once flash is loaded, the playback(of flash movie) is slow, and completely shuts down FF.

Booted back to .5 kernel, will continue testing later today.

---

