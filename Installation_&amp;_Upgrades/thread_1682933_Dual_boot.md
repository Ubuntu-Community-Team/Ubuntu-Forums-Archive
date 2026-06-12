---
title: "Dual boot"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by johnfrankjr on 2011-02-06
I have Ubuntu installed inside of Windows 7. I'd like to make Ubuntu the default OS to boot into if I don't select anything on boot up. How do I go about doing that?

---

### Post by kansasnoob on 2011-02-06
I don't know but look at this link before you start fiddling with the Wubi bootloader:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by bcbc on 2011-02-06
There's a post in that thread that talks about boot settings. You can go to "startup & recovery" settings in windows and change the default - just don't set the timeout to zero - or you can't boot windows.

---

### Post by johnfrankjr on 2011-02-07
> **bcbc said:**
> There's a post in that thread that talks about boot settings. You can go to "startup & recovery" settings in windows and change the default - just don't set the timeout to zero - or you can't boot windows.

And if I did put zero and couldn't boot windows now what would I do  to get back into windws?

---

### Post by bcbc on 2011-02-07
Since I haven't experienced this personally (I have XP) - I'll can just pass on what I've heard from others in that situation. 

You're supposed to be able to press F8 and this should popup the boot manager. This is reported to not work. I'd try this anyway (start hitting F8 early)

You're also supposed to be able to use the command line tool bcdedit.exe to change the timeout (after booting to a windows 7 repair prompt). However reports say this doesn't work either. Again, I'd try this.

Instead [someone reported]("http://ubuntuforums.org/showthread.php?t=1665002") using bootrec.exe /fixmgr fixed the problem (but also removed the wubi entry).

So that's what I know. If you are in this situation - then feedback is appreciated so we can pass along what works and what doesn't.

PS if you need help adding an entry for Ubuntu back later - see this [http://ubuntuforums.org/showpost.php?p=10431659&postcount=182](http://ubuntuforums.org/showpost.php?p=10431659&postcount=182)

---

### Post by Mark Phelps on 2011-02-07
I generally advise folks NOT to mess around with the MS Windows BCD using command line entries.  One minor mistake, and you have an unbootable PC!

Safest way to do this would be the following:
1) Download and install EasyBCD (into Win7) from NeoSmart Technologies
2) Open EasyBCD and use the option to change the default OS to Ubuntu.

When you restart, as long as you don't press a key, it will boot into Ubuntu instead of Win7.

---

### Post by bcbc on 2011-02-07
> **Mark Phelps said:**
> I generally advise folks NOT to mess around with the MS Windows BCD using command line entries.  One minor mistake, and you have an unbootable PC!

Safest way to do this would be the following:
1) Download and install EasyBCD (into Win7) from NeoSmart Technologies
2) Open EasyBCD and use the option to change the default OS to Ubuntu.

When you restart, as long as you don't press a key, it will boot into Ubuntu instead of Win7.
Well you don't need bcdedit or easybcd to change the default. Or the timeout. That's the problem because Windows makes it too easy to get yourself into this mess. It's getting out of it that's the problem - and bcdedit seems to be the only way.

Can you use easybcd to change the timeout from a rescue disk?

---

### Post by johnfrankjr on 2011-02-07
> **bcbc said:**
> Well you don't need bcdedit or easybcd to change the default. Or the timeout. That's the problem because Windows makes it too easy to get yourself into this mess. It's getting out of it that's the problem - and bcdedit seems to be the only way.

Can you use easybcd to change the timeout from a rescue disk?

Yea, I changed it to zero thinking it would go straight into Ubuntu. I would do a fresh install and start over but I don't have the Windows 7 cd anymore. I tried to hit F8 and get into the recovery partition but it won't let me.

---

### Post by bcbc on 2011-02-07
> **johnfrankjr said:**
> Yea, I changed it to zero thinking it would go straight into Ubuntu. I would do a fresh install and start over but I don't have the Windows 7 cd anymore. I tried to hit F8 and get into the recovery partition but it won't let me.
You don't want to do a fresh install - that's overkill. You can download a windows repair CD and burn it from Ubuntu.

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

In the meantime avoid running updates on Ubuntu until you get Windows back up and running.

---

