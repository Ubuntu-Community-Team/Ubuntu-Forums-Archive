---
title: "How on earth will these bugs get fixed by tomorrow?"
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-10-29
[https://bugs.launchpad.net/ubuntu/intrepid/+bugs](https://bugs.launchpad.net/ubuntu/intrepid/+bugs)

---

### Post by inportb on 2008-10-29
I don't think they will :)

---

### Post by rbmorse on 2008-10-29
Not all of them will. 

All software ships with open issues, or it doesn't ship at all. Just a fact of life.

---

### Post by Choad on 2008-10-29
> **rbmorse said:**
> Not all of them will. 

All software ships with open issues, or it doesn't ship at all. Just a fact of life.
that's why you get so many people dieing because of crashes in computerised medical equipment.

</sarcasm>

---

### Post by inportb on 2008-10-29
Sarcasm or not, it's true :lolflag:

---

### Post by jfernyhough on 2008-10-29
Oh, oh! And aircraft crashing in mid-air because air traffic control systems freeze! And shuttles landing in the Pacific because control computers run NT SP 7 and get viruses from laptops! Wait, what were we talking about again?

Oh, yeah. It's a cost-benefit thing. Seeing as 90% of software can be released 90% complete there's no benefit to filling in the 10% before release. As long as the bugs aren't show-stoppers they can be addressed later.

---

### Post by Seq on 2008-10-29
If you delay for those bugs linked above, more will be found during that time, and the software will grow out of date, at which point you update and re-start the whole debug procedure.

Medical systems have had bugs in the past (a few notable fatal ones). As stated above, there is a cost/benifit ratio that needs to be considered. For the price of $MedicalDevice, they can afford to do significantly more testing. Also consider that $MedicalDevice's focus will be substantially more narrow than a general purpose operating system.

More important is how bugs are handled. For example, I'm willing to bet that if $MedicalDevice fails or acts improperly, it fails "gracefully" by not decapitating, launching, injecting, etc. I don't see many critical bugs (just two). Not bad for a general purpose OS with a six-month development period.

---

### Post by Kow on 2008-10-29
If Ubuntu shipped with 0 open issues then we'd be debian. Nothing against debian because they have their own philosophy which they follow perfectly, but I do not think it is in Ubuntu's best interest to delay Intrepid 3 years. 3 years from now GNOME 3.0 will be out just as we're releasing a distribution with 2.24. What you are asking for requires perfection on the part of developers, whom are human like everyone else.

---

### Post by philinux on 2008-10-29
> **Kow said:**
> What you are asking for requires perfection on the part of developers, whom are human like everyone else.

I wasn't asking for the release to be delayed or zero bugs. I was curious when I saw the list that some were critical/high importance.

---

### Post by dabl on 2008-10-29
Two things can be true at the same time.  :)

1. Software is never finished.  Never.  Sometimes people just stop working on it.

2. Very few software bugs* are "critical", in terms of human safety. Most are just annoyances.  :lolflag:



* A lot of them would be better characterized as "missing enhancements that I'd like to have".

---

### Post by UbuWu on 2008-10-29
This is the list of bugs targeted to be fixed before release:

[https://bugs.launchpad.net/ubuntu/+milestone/ubuntu-8.10](https://bugs.launchpad.net/ubuntu/+milestone/ubuntu-8.10)

Most of them are fixed, the ones still open probably won't make it.

---

### Post by Choad on 2008-10-29
> **Seq said:**
> If you delay for those bugs linked above, more will be found during that time, and the software will grow out of date, at which point you update and re-start the whole debug procedure.

Medical systems have had bugs in the past (a few notable fatal ones). As stated above, there is a cost/benifit ratio that needs to be considered. For the price of $MedicalDevice, they can afford to do significantly more testing. Also consider that $MedicalDevice's focus will be substantially more narrow than a general purpose operating system.

More important is how bugs are handled. For example, I'm willing to bet that if $MedicalDevice fails or acts improperly, it fails "gracefully" by not decapitating, launching, injecting, etc. I don't see many critical bugs (just two). Not bad for a general purpose OS with a six-month development period.
i actually didn't know of those fatal cases, so my example wasn't great. but still, they are about as perfect as software gets, and have a 99.99999% reliability rate.

i did know the rest tho :) was just making a point.

---

### Post by malleus74 on 2008-10-29
I'm willing to try Intrepid today if they'll get the atheros 5007EG wireless working with it.

---

### Post by Perpetual on 2008-10-29
It boggles me that a [regression]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247") that prevents a lot of HP users from using 8.10 is marked Medium Importance.  I have used the last 5 Ubuntu releases and now can not because of a regression that is only semi important.  What about all of the new users that Ubuntu/Canonical wants to bring from Windows that will not be able to even boot the livecd?

/frustrated

---

### Post by inportb on 2008-10-29
Of course you would perceive the problem to be much bigger than it really is, since you are directly affected by it. Nobody can blame you for amplifying the importance of the problem. However, the development team aims for the greatest good for the greatest number.

---

### Post by kansasnoob on 2008-10-29
> **philinux said:**
> [https://bugs.launchpad.net/ubuntu/intrepid/+bugs](https://bugs.launchpad.net/ubuntu/intrepid/+bugs)

I have only three complaints:

(1)The CD eject problem. That seems like a huge issue to me!

(2)Regression in HPLIP. The new GUI is great, but the same printer that worked out-of-box in Gutsy and Hardy required the download of HPLIP's newest driver to get it working.

(3)The recurrent update error (just annoying).

Final analysis: it's worth the hassle!

---

### Post by kansasnoob on 2008-10-29
We should also keep in mind that Hardy is LTS, so if you have Hardy running well, just leave it be for a while.

Remember we're talking a six month release cycle! Gutsy is good till April 09! Hardy is good for a gazillion years!

---

### Post by OrangeCrate on 2008-10-29
> **philinux said:**
> [https://bugs.launchpad.net/ubuntu/intrepid/+bugs](https://bugs.launchpad.net/ubuntu/intrepid/+bugs)

They won't. But, that's why we have updates.

---

### Post by OrangeCrate on 2008-10-29
> **kansasnoob said:**
> I have only three complaints:

(1)The CD eject problem. **That seems like a huge issue to me!**

(2)Regression in HPLIP. The new GUI is great, but the same printer that worked out-of-box in Gutsy and Hardy required the download of HPLIP's newest driver to get it working.

(3)The recurrent update error (just annoying).

Final analysis: it's worth the hassle!

Just let it open and close, and then open it manually. Works for me, until it's fixed.

---

### Post by kansasnoob on 2008-10-29
> **OrangeCrate said:**
> Just let it open and close, and then open it manually. Works for me, until it's fixed.

That doesn't work for me! It also interferes with some very basic functions in Brasero and K3B but there's a work-around. Look at my post #27 here:

[http://ubuntuforums.org/showthread.php?t=942553&page=3](http://ubuntuforums.org/showthread.php?t=942553&page=3)

I've tried it on 3 fresh installs and it works fine!

---

### Post by blakamin on 2008-10-29
> **malleus74 said:**
> I'm willing to try Intrepid today if they'll get the atheros 5007EG wireless working with it.

Funny thing was it worked for me from alpha 5  up until the RC....  that sort of *insert-swear-of-choice-here* is why Ubuntu isn't really going forward well enough to become mainstream... sad.
Hell, neither of my computers remember running apps (one a 3y/o desktop, the other a 8month/o laptop) and one wont even shut down without crashing! Funny that they both experienced no probs in 8.04.

---

### Post by chrisccoulson on 2008-10-30
> **Perpetual said:**
> It boggles me that a [regression]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247") that prevents a lot of HP users from using 8.10 is marked Medium Importance.  I have used the last 5 Ubuntu releases and now can not because of a regression that is only semi important.  What about all of the new users that Ubuntu/Canonical wants to bring from Windows that will not be able to even boot the livecd?

/frustrated

I added an ubuntu-release-notes task for your bug so we can (hopefully) get it mentioned in the release notes, as this won't be fixed for the final release.

---

### Post by jerrylamos on 2008-10-30
> **inportb said:**
> Of course you would perceive the problem to be much bigger than it really is, since you are directly affected by it. Nobody can blame you for amplifying the importance of the problem. However, the development team aims for the greatest good for the greatest number.

Good luck.  Any number of us get frozen tight by compiz "playing fancy tricks with graphics hardware and drivers" as you can see from scanning the posts for the last two months for "locked up"  "black screen" "orange screen" "won't load desktop" "won't boot" "killed by update" on and on.  I got all of those.  Since the computer freezes tight, it's very difficult for the ordinary user to tell what happened.  Ubuntu just doesn't work for them.  

Being a glutton for punishment I spent weeks plowing thru posts and logs and error messages to figure out I could fix it all by booting in rescue mode and sudo apt-get remove compiz, bug 259385.  I can't imagine an ordinary user doing that.

Rational fix:  make compiz OFF by default if you really want the "greatest good for the greatest number".

Jerry

---

### Post by Choad on 2008-10-30
> **jerrylamos said:**
> Good luck.  Any number of us get frozen tight by compiz "playing fancy tricks with graphics hardware and drivers" as you can see from scanning the posts for the last two months for "locked up"  "black screen" "orange screen" "won't load desktop" "won't boot" "killed by update" on and on.  I got all of those.  Since the computer freezes tight, it's very difficult for the ordinary user to tell what happened.  Ubuntu just doesn't work for them.  

Being a glutton for punishment I spent weeks plowing thru posts and logs and error messages to figure out I could fix it all by booting in rescue mode and sudo apt-get remove compiz, bug 259385.  I can't imagine an ordinary user doing that.

Rational fix:  make compiz OFF by default if you really want the "greatest good for the greatest number".

Jerry
ctrl+alt+print screen+k

you're welcome :)

---

### Post by inportb on 2008-10-30
> **jerrylamos said:**
> Rational fix:  make compiz OFF by default if you really want the "greatest good for the greatest number".

Or just use KDE, whose compositor owns Compiz in stability :)

---

### Post by Gina on 2008-10-30
> **jerrylamos said:**
> Rational fix:  make compiz OFF by default if you really want the "greatest good for the greatest number".+1 I hate fancy effects anyway - I just want an OS the works!  But by all means make it clear how you turn it on for those that do like fancy effects :)

---

