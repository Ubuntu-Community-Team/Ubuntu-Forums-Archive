---
title: "Test strategy or test plan"
date: 2009-05-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Martijn van Es on 2009-05-22
Hey folks,
Is there a test strategy or test plan we use to test 9.10?

---

### Post by super.rad on 2009-05-22
Strategy is use it and if you find bugs report them :p

---

### Post by Martijn van Es on 2009-05-22
As far as I know that isn't the best strategy when you try to find as many bugs possible in a short period of time. There are how many 500? updated packages? How do we know what packages are tested and what are not?

Lets say 50 people already went through Open Office and nobody tried Pidgin would it make sense if person 51 would also test open office or would we want a plan so person 51 would know he should be working on pidgin?

---

### Post by super.rad on 2009-05-22
As far as I know there is no strategy or test plan, everyone just uses it and reports any bugs they come across

---

### Post by Slug71 on 2009-05-22
> **super.rad said:**
> As far as I know there is no strategy or test plan, everyone just uses it and reports any bugs they come across

This.

---

### Post by Martijn van Es on 2009-05-22
[https://lists.ubuntu.com/archives/karmic-changes/2009-May/thread.html](https://lists.ubuntu.com/archives/karmic-changes/2009-May/thread.html)

These are the Karmic changes for May. I have installed and tested Drapes, it works as expected.

There are 1228 other packages and we should test those as well. Without a plan that will never work.

---

### Post by cykotiktek on 2009-05-22
It has worked for this many releases why not this one?

---

### Post by Martijn van Es on 2009-05-22
It will also work for this release I am sure it will.

Having a plan could help in these ways:
* Find bugs in critical packages early in the development cycle so they are known and corrected before cosmetic and other less urgent bugs.
* Using a plan will give information on what is and what isn't tested before the release will be made available to the world. With that information it is possible to calculate where the risks are.

I think by using a plan the quality of the release will be known before it is released and that will make the quality of the release better.

---

### Post by Reiger on 2009-05-22
Are we on Debian import freeze yet, then? Until that time any test plan is somewhat over done. :P

---

### Post by ktp on 2009-05-22
> **Martijn van Es said:**
> It will also work for this release I am sure it will.

Having a plan could help in these ways:
* Find bugs in critical packages early in the development cycle so they are known and corrected before cosmetic and other less urgent bugs.
* Using a plan will give information on what is and what isn't tested before the release will be made available to the world. With that information it is possible to calculate where the risks are.

I think by using a plan the quality of the release will be known before it is released and that will make the quality of the release better.

Sounds like a good idea..can you come up with test plan/strategy and maybe put it up on the wiki?

[https://wiki.ubuntu.com/Testing](https://wiki.ubuntu.com/Testing)

Might be hard to verify that test plan was executed since so many people are involved but if you want to help in the area then might want to talk with Ubutnu QA team.

---

### Post by Martijn van Es on 2009-05-23
Hi ktp,

I will look into that wiki. The QA team might be what i am looking for in testing. Thanx!

---

### Post by Nullack on 2009-05-23
There is no limit to the test types you could do - for example:

1. Performance testing
2. Functional testing
3. Integration testing

Or some other methods:

4. Static analysis of code
5. Security tests
6. Helping with the automated test suite for Ubuntu or specific upstream projects

etcetc

---

### Post by TrueTom on 2009-05-23
Since the rate of bug finding is already higher than the rate of bug fixing, increasing the number of known bugs won't increase the quality of the product. You could argue that finding more critical bugs will help to better allocate resources but this doesn't hold true in practise. For example, the IrDA support in Ubuntu is broken for months now (read: a complete class of hardware is unusable), there exists a five line patch but no one cares to release updated packages.

---

### Post by xebian on 2009-05-23
Talking about bugs, was the bug 'ubuntero' been resolved?  The question was it proper (or PC) to call one as such instead of 'ubuntera', or '...nistas' or '...nistos', or blah blah.  Or is this a bug?:p

---

### Post by Nullack on 2009-05-23
> **TrueTom said:**
> Since the rate of bug finding is already higher than the rate of bug fixing, increasing the number of known bugs won't increase the quality of the product. You could argue that finding more critical bugs will help to better allocate resources but this doesn't hold true in practise. For example, the IrDA support in Ubuntu is broken for months now (read: a complete class of hardware is unusable), there exists a five line patch but no one cares to release updated packages.

I agree, and I also disagree with this post. Yes not all bugs will get attention. However, taking the view not to raise bugs because it might not get worked on is silly. Its better to take the risk, invest your time in good faith and hope the bug will get attention. If it doesnt, theres ways to attract attention - figuring out if its upstream or distro specific, forums, mailing lists etcetc.

---

### Post by taavikko on 2009-05-23
> **Martijn van Es said:**
> As far as I know that isn't the best strategy when you try to find as many bugs possible in a short period of time. There are how many 500? updated packages? How do we know what packages are tested and what are not?

Lets say 50 people already went through Open Office and nobody tried Pidgin would it make sense if person 51 would also test open office or would we want a plan so person 51 would know he should be working on pidgin?

I wouldn't test things in this way. Although it might be suitable for finding those bugs.

But we all have our own usage patterns, and should continue to use the system for that, and when hitting a bug, report it.

any other method takes the fun out of it.

---

### Post by ktp on 2009-05-23
> **TrueTom said:**
> Since the rate of bug finding is already higher than the rate of bug fixing, increasing the number of known bugs won't increase the quality of the product. You could argue that finding more critical bugs will help to better allocate resources but this doesn't hold true in practise. For example, the IrDA support in Ubuntu is broken for months now (read: a complete class of hardware is unusable), there exists a five line patch but no one cares to release updated packages.

This is true...I know rdesktop took a patch which was bad and introduce a regression during 8.10 and another one or two line fix/patch is available but no one want to merge it.  I guess this is happening and I am not happy about it but this should not stop in writing up new bugs.  I think everyone should also help in filtering/closing dup bugs because I am sure there are many of those too.

---

### Post by TrueTom on 2009-05-23
> **Nullack said:**
> I agree, and I also disagree with this post. Yes not all bugs will get attention. However, taking the view not to raise bugs because it might not get worked on is silly. Its better to take the risk, invest your time in good faith and hope the bug will get attention. If it doesnt, theres ways to attract attention - figuring out if its upstream or distro specific, forums, mailing lists etcetc.

I'm not saying you shouldn't file bugs, I'm just saying that trying to improve the quality of Ubuntu through more testing won't work. The same problem exits with malls for example. You can try to increase the output of customers by increasing the input of them (e.g. by an ad campaign). This usually doesn't work if you don't change the slow part of your system.

---

### Post by ranch hand on 2009-05-23
There are only so many people to work on bugs and they haveto rate them (how many reports and on what systems) and then someone has to have time to work on them.  If bugs are not reported they will never be addressed.

I, personally, think that the devs do a great job of addressing bugs that effect the largest bunch of folks.

As linux in general supports more hardware the possibilities for bugs increases because you can develope more complex apps.

---

