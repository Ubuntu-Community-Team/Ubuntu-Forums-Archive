---
title: "Intrepid Ibex: a lot of REGRESSIONS!"
date: 2008-07-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by grigio on 2008-07-26
I tested alpha3 live cd on a non-recent pc an I have a lot of regressions compared to Hardy Heron or Gutsy alpha/beta.

In brief:
- network-admin package not install (why?)
- devices mounted twice
- boot splash screen broken
- sound doesn't work out of the box
- a resolution changing make the settings-daemon crash
- nvidia: recornized 71xx instead of 96xx and 96xx is broken
- bluetooth accept files by anyone without user interaction

[http://grigio.org/ubuntu_8_10_intrepid_ibex_preview](http://grigio.org/ubuntu_8_10_intrepid_ibex_preview)

Which bugs are useful to report?

---

### Post by xens on 2008-07-26
Let's have a look to launchpad if it's not reported then open a new  bug report. I have the same problem with the mounting of media's (usb stick, cdrom, ...) [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/251991](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/251991)

---

### Post by mc4100 on 2008-07-26
> **grigio said:**
> 
- network-admin package not install (why?)

I'm using NM 0.7, which works perfect for me (with no "network-admin")
> 
- devices mounted twice

Confirmed. I see "DBus error org.gtk.Private.RemoteVolumeMonitor.NotFound: The given mount was not found"
> 
- boot splash screen broken

Yep, it works fine sometimes and others, I see weird artifacts like the progress-bar appearing multiple times (just like your screenshot)
> 
- sound doesn't work out of the box

Technically it does work... only through the pc speaker ;)
It's easily fixed:
[http://ubuntuforums.org/showpost.php?p=5299675&postcount=13](http://ubuntuforums.org/showpost.php?p=5299675&postcount=13), and any other issues (stuttering etc,) can also be fixed using this guide:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
> 
- a resolution changing make the settings-daemon crash

I really don't want to try this :/

Finally, I'd like to add the fact that choosing shut-down only logs the user out.

But apart from these issues, it's really quite stable.

---

### Post by BackwardsDown on 2008-07-26
> - a resolution changing make the settings-daemon crash 

Same here

---

### Post by SunnyRabbiera on 2008-07-26
This is why its an alpha.

---

### Post by syko21 on 2008-07-26
The double mount thing happened to me on an upgrade, did you upgrade or clean install?

---

### Post by Joeb454 on 2008-07-26
> **SunnyRabbiera said:**
> This is why its an alpha.

+1 some features won't be working yet. Hence it may appear to be "going backwards" shall we say;)

---

### Post by grigio on 2008-07-26
> **syko21 said:**
> The double mount thing happened to me on an upgrade, did you upgrade or clean install?

livecd

---

### Post by grigio on 2008-07-26
> **Joeb454 said:**
> +1 some features won't be working yet. Hence it may appear to be "going backwards" shall we say;)

Yes it's an alpha, but we are talking about basic features that exists since **24** releases ago.. not new stuff

---

### Post by Joeb454 on 2008-07-26
24 releases?

I didn't know there was that many...

Joking aside :)

I think that sometimes certain features won't work due to dependencies etc. which may be broken. In turn this could affect the program/feature you're claiming is broken

---

### Post by ronacc on 2008-07-26
that is the reason for alphas and betas , a change or addition in one place affects other things ( sometimes unintended ones ) thats what we are here to find .

---

### Post by Nullack on 2008-07-26
Anyone using the Alpha as I see it has a responsibility to:

1. Make detailed observations anytime something happens that isnt what the user expects
2. Raise new bugs detailing the condition or looking at existing bugs that cover it and commenting in those where it adds value to the existing bug report
3. Track the commits and re-test anytime packages are changed involving the bug.

We need to be bug report driven in our culture. To me this is our only hope for realising the potential of Ubuntu.

---

### Post by Gina on 2008-07-27
Well said! :)

---

### Post by DizzyTech on 2008-07-27
Remember that a major feature of Intrepid is the massive import from Debian, so there are a lot of broken dependencies and messed-up configuration files.

---

### Post by z0idberg on 2008-07-27
> **DizzyTech said:**
> Remember that a major feature of Intrepid is the massive import from Debian, so there are a lot of broken dependencies and messed-up configuration files.
I reported the "devices mounted twice" too, and found it was a duplicate of a much, much older bug... Anyway, DizzyTech's comment makes me think... I suppose there is some point in the release cycle when massive Debian merge ceases to happen (as planets realign and some guy deep in the jungle with a scary mask and the ability to talk to trees performs a special dance)... 

To me, it would seem to make sense if, after the merge is finished, there would be time for the developers to do the obvious configuration stuff, fix the things they know must be fixed (and know **how to** fix) and only then people start reporting bugs (I like this sentence, it has a kind of german multi-level quality to it!). 

Cause now, you get the feeling that massive Debian merge occurs, then millions of bugs are reported and sorted while the developers sit and read the bug reports and think to themselves "I **know** this doesn't work, I haven't even gotten started configuring this version of the app for Ubuntu." And a lot of bug hunting and sorting and researching was wasted and there wasn't much rejoicing at all.

But then again, maybe (most likely) it just has to work this way (as I do belive someone, at some point in history, actually **thought** about this process and found it was good). :)

---

### Post by Frak on 2008-07-27
When working with dynamite, be sure to bring your hard hat.

---

### Post by Joeb454 on 2008-07-27
I always make sure I bring my anti-explosive clothes, it helps to stop me exploding if the dynamite does ;)

---

### Post by Gina on 2008-07-27
I find Intrepid is gradually getting better :)  And there are various minor new features all over the place.  OK so new bugs appear - name of the game!  It's showing great promise.

---

### Post by grigio on 2008-07-28
> **z0idberg said:**
> I reported the "devices mounted twice" too, and found it was a duplicate of a much, much older bug... Anyway, DizzyTech's comment makes me think... I suppose there is some point in the release cycle when massive Debian merge ceases to happen (as planets realign and some guy deep in the jungle with a scary mask and the ability to talk to trees performs a special dance)... 

To me, it would seem to make sense if, after the merge is finished, there would be time for the developers to do the obvious configuration stuff, fix the things they know must be fixed (and know **how to** fix) and only then people start reporting bugs (I like this sentence, it has a kind of german multi-level quality to it!). 

Cause now, you get the feeling that massive Debian merge occurs, then millions of bugs are reported and sorted while the developers sit and read the bug reports and think to themselves "I **know** this doesn't work, I haven't even gotten started configuring this version of the app for Ubuntu." And a lot of bug hunting and sorting and researching was wasted and there wasn't much rejoicing at all.

But then again, maybe (most likely) it just has to work this way (as I do belive someone, at some point in history, actually **thought** about this process and found it was good). :)

If Ubuntu is still importing the package base from Debian is useless to report bugs now... I'll start to report the bugs from the first beta

---

