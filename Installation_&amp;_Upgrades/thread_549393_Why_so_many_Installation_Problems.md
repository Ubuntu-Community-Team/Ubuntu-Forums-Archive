---
title: "Why so many Installation Problems"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by hongkongdew on 2007-09-12
Now having experienced Ubuntu ( It wouldn't install, base system unable 
to install, 5.10 ubuntu, joy joy ), and after reading over so many problems with installation, I have one question. Why is Ubuntu(all linux??) so difficult to install?

Just curious,
-Dew

---

### Post by AstarothCY on 2007-09-12
I haven't had any problems installing, but upgrading from Edgy to Feisty is making my life a living hell right now (see relevant thread).

---

### Post by Steveway on 2007-09-12
5.10 is about 2 years old.
You'd better try a recent release.

---

### Post by kellemes on 2007-09-12
You're talking about installing a os, this isn't supose to be easy.. most users will never install there os themselfs.

---

### Post by dabl on 2007-09-12
> **hongkongdew said:**
> 

 Why is Ubuntu(all linux??) so difficult to install?



One guy's opinion:  It isn't.  It just seems like it to folks who only know how to install Windows.  I installed Gutsy Tribe 5, including modifying Envy and getting my Nvidia driver installed, in about 45 minutes last weekend. You can't do that with any version of Windows. :popcorn:

---

### Post by Pumalite on 2007-09-12
Hey dabl. me too.

---

### Post by Darth_Zim on 2007-09-12
> **hongkongdew said:**
> Now having experienced Ubuntu ( It wouldn't install, base system unable 
to install, 5.10 ubuntu, joy joy ), and after reading over so many problems with installation, I have one question. Why is Ubuntu(all linux??) so difficult to install?

Just curious,
-Dew

I hear what you're saying hongkong, I've been fighting with ubuntu (7.04) for about a week now trying to get it to install. I somehow got it to install this one time (didn't do anything differently), but the OS blew up after two reboots, and then just wouldn't boot. Even from the CD I just got dumped into busybox.

I then tried a completely fresh HD in there, same thing - after I select 'install' on the ubuntu CD, after the 'casper' messages it hovers on the 'ubuntu' bootup logo for a while then just dumps me to busybox with an unintelligible error message about tty not being possible.

It wasn't like this in the early days - I remember ages ago I had a redhat installation which went perfectly and even dual booted with windows. It worked first time too!

---

### Post by dabl on 2007-09-12
@Darth -- download and burn an "Alternate Install" CD -- it gives you a lot more visibility and control over the process.  If you're working with a laptop, you might need to use some of the "noapic" and "nolapic" and "noacpi" options to deal with the power-saving stuff.

Search the Forum on your hardware model, and probably others have dealt with it already.

 :)

---

### Post by Darth_Zim on 2007-09-12
> **Darth_Zim said:**
> I hear what you're saying hongkong, I've been fighting with ubuntu (7.04) for about a week now trying to get it to install. I somehow got it to install this one time (didn't do anything differently), but the OS blew up after two reboots, and then just wouldn't boot. Even from the CD I just got dumped into busybox.

I then tried a completely fresh HD in there, same thing - after I select 'install' on the ubuntu CD, after the 'casper' messages it hovers on the 'ubuntu' bootup logo for a while then just dumps me to busybox with an unintelligible error message about tty not being possible.

It wasn't like this in the early days - I remember ages ago I had a redhat installation which went perfectly and even dual booted with windows. It worked first time too!

EDIT: I managed to find a fix - if you're getting this problem check out the thread titled:

'SOLUTION TO /bin/sh: can't access tty; job control turned off' by 'dhannyboy79'.

it seems that just adding 'boot=top' to the boot params on the install screen will get you working if you have this problem ... I guess these things are meant to test us!

---

### Post by Pumalite on 2007-09-12
If the error message would have been spelled out from the beginning; this would have been solved in one or two posts. Is not the OS that doesn't work; is that people need to be detailed in the exposition of their problem.

---

### Post by ACOpsEngr on 2007-09-13
I think the key here is that it's just so different.

The majority of people know Windows and that's it.  And while Windows limits the user in a lot of ways, most users don't care because they don't know they are being limited.  And there is nothing wrong with that.  I mean, seriously, if your just browsing the web and sending an email here or there, what's the difference?

I'm brand new to Linux as of two days ago.  But I'd heard for a long time how great it was and since I just bought a new Vista laptop I thought I'd wipe out my XP desktop (that I barely use anymore) and give Linux a whirl.  I didn't dual boot XP and Ubuntu.  I nuked XP.

And I definitely had a few problems installing, despite the fact that I followed the instructions exactly.  And when I had problems with this or that, I was able to go to the web and find people with solutions, but the solutions were cryptic.  Clear as day to the author, but confusing as hell to me (the Windows user).  Luckily, I do use UNIX (not LINUX) at work quite a bit  (I'm an engineer) so the terminal as easier for me to grasp that I imagine it would be for average Joe windows user.

But the average Joe user has never seen Linux, or Unix, or even DOS.  They've never done anything from the command line.  You could say open the terminal and they'd say, "What's the terminal?"  Might sound trivial to us but to them it's a big deal.  Maybe too much of a hassle when they've got better things to do then try to figure out what the hell is going wrong with their computer.

I do agree that I could have gone more smoothly.  And perhaps some of the tutorials could have been a little clearer.  But all in all I'm happy with the way it turned out.  Of course, I still have my Vista laptop open right next to me.

I write a lot of code every day for work - small scripts and large scale projects - DOS/UNIX/WINDOWS, VB.NET, Visual Fortran 10, Matlab, etc.  So when I get home I'm not that interested in doing much other than the occassional surfing/emailing - not too dissimilar from the average user.  So I've got Linux (Ubuntu)...  and my biggest question is...  now what?

And I think this may be the biggest issue for Linux advocates.  What (other that it being free) does Linux really offer the average Joe user that is compelling enough to get them out of their comfort zone.  And I don't mean compelling to the power user.  I mean compelling to Average Joe.  For me it was pure curiosity.  I've got it, it seems to work okay, but now what?

---

### Post by mikewhatever on 2007-09-13
> **hongkongdew said:**
> Now having experienced Ubuntu ( It wouldn't install, base system unable 
to install, 5.10 ubuntu, joy joy ), and after reading over so many problems with installation, I have one question. Why is Ubuntu(all linux??) so difficult to install?

Just curious,
-Dew

Do not know why you have problems installing. What are they? Some reasons may be suggested, 5.10 is old, your hardware is not supported, the downloaded iso is corrupted. Did it help?
Off the record, I've installed 6.10 and 7.04, and both got finished in 20 minutes without any issues.

---

### Post by Pumalite on 2007-09-13
> **ACOpsEngr said:**
> I think the key here is that it's just so different.

The majority of people know Windows and that's it.  And while Windows limits the user in a lot of ways, most users don't care because they don't know they are being limited.  And there is nothing wrong with that.  I mean, seriously, if your just browsing the web and sending an email here or there, what's the difference?

I'm brand new to Linux as of two days ago.  But I'd heard for a long time how great it was and since I just bought a new Vista laptop I thought I'd wipe out my XP desktop (that I barely use anymore) and give Linux a whirl.  I didn't dual boot XP and Ubuntu.  I nuked XP.

And I definitely had a few problems installing, despite the fact that I followed the instructions exactly.  And when I had problems with this or that, I was able to go to the web and find people with solutions, but the solutions were cryptic.  Clear as day to the author, but confusing as hell to me (the Windows user).  Luckily, I do use UNIX (not LINUX) at work quite a bit  (I'm an engineer) so the terminal as easier for me to grasp that I imagine it would be for average Joe windows user.

But the average Joe user has never seen Linux, or Unix, or even DOS.  They've never done anything from the command line.  You could say open the terminal and they'd say, "What's the terminal?"  Might sound trivial to us but to them it's a big deal.  Maybe too much of a hassle when they've got better things to do then try to figure out what the hell is going wrong with their computer.

I do agree that I could have gone more smoothly.  And perhaps some of the tutorials could have been a little clearer.  But all in all I'm happy with the way it turned out.  Of course, I still have my Vista laptop open right next to me.

I write a lot of code every day for work - small scripts and large scale projects - DOS/UNIX/WINDOWS, VB.NET, Visual Fortran 10, Matlab, etc.  So when I get home I'm not that interested in doing much other than the occassional surfing/emailing - not too dissimilar from the average user.  So I've got Linux (Ubuntu)...  and my biggest question is...  now what?

And I think this may be the biggest issue for Linux advocates.  What (other that it being free) does Linux really offer the average Joe user that is compelling enough to get them out of their comfort zone.  And I don't mean compelling to the power user.  I mean compelling to Average Joe.  For me it was pure curiosity.  I've got it, it seems to work okay, but now what?

I think Linux for me is most of all a way of life, a different philosophy behind the concept. Besides being able to do anything I want with the system and to have much more control over everything, compared to Windows, it's just that I don't like being held hostage to a system. It takes a while to find your way; it was just recently that I was a newbie, and I will continue to be one in many ways; the payoff is big. As a matter of fact I think one should never stop being a newbie; it's the only way to continue learning.

---

