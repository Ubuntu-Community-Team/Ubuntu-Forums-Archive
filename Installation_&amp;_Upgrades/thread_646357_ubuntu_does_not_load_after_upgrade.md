---
title: "ubuntu does not load after upgrade"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by D45 on 2007-12-21
I have upgrade from 6.06 LT to 6.10    works fine
then  from 6.10 to 7.04   after this  when I restart  ubuntu stucks at loading screen.

what to do now .
Any one has solution?
I could not find any on this forum.



My system:
P4 2.4 Ghz   
Intel 845 chipset 
Nvidia 5600xt  graphics card (PCI version )
1.25 gb RAM

Win XP SP2  on 40 gb HDD
80 gb HDD  (10 gb parted for ubuntu)

Edit:  Problem found
When switched to nvidia it does not load
But on onboard graphics it works fine 

I have clean Installed 7.10 gives same problem

---

### Post by PmDematagoda on 2007-12-21
What do you see when you try and load Ubuntu in Recovery Mode?

---

### Post by D45 on 2007-12-21
> **PmDematagoda said:**
> What do you see when you try and load Ubuntu in Recovery Mode?


when I try recovery mode it stuck at   this

[53.648983] [<c02dda37>] do_page_fault + 0x3a7/0x600
[53.649073] [<c02dd690>] do_page_fault + 0x0/0x600
[53.649189] [<c010311b>] work_notifysig + 0x13/0x18
[53.649328]  =================

---

### Post by D45 on 2007-12-22
no one has solution?
no replies?
I thought  I will get bunch of replies.
But nothing . only one reply
If I dont get solution I have to dump ubuntu

---

### Post by PmDematagoda on 2007-12-22
I think your problem is an unsuccessful upgrade, a big factor in this can be because you  shifted all the way from 6.06 to 7.04 and there are a good number of differences between the two which could  be causing the problem you are having right now.

I suggest that you reinstall Ubuntu since you would have much better luck with it than trying to fix the broken upgrade.

---

### Post by D45 on 2007-12-23
Can I directly install latest version?
What I have to do for that?
Do I need to uninstall previous version?

In short I need easy method?

---

### Post by LinuxGuy1234 on 2007-12-23
> **D45 said:**
> Can I directly install latest version?
What I have to do for that?
Do I need to uninstall previous version?

In short I need easy method?

[Download the ISO here.]("http://www.ubuntu.com/")

Burn it to a CD and reboot with it. Choose to "Start or install Ubuntu".
Double-click on Install and follow the directions and reboot.

---

### Post by D45 on 2007-12-23
will it replace previous version??

---

### Post by PmDematagoda on 2007-12-23
Yes it will.

---

### Post by D45 on 2007-12-23
Thank you for quik reply.
I will try that

---

### Post by D45 on 2007-12-25
> **PmDematagoda said:**
> I think your problem is an unsuccessful upgrade, a big factor in this can be because you  shifted all the way from 6.06 to 7.04 and there are a good number of differences between the two which could  be causing the problem you are having right now.

I suggest that you reinstall Ubuntu since you would have much better luck with it than trying to fix the broken upgrade.

BTW till I download and burn new ubuntu


I want to know how to  fix this broken upgrade

---

### Post by PmDematagoda on 2007-12-25
Unfortunately I don't think you can fix the upgrade at all, the error message is rather cryptic and I do not know what is causing the issue. But if you wish to wait, someone else might come along and provide a solution, but I do not have much hope about it.

---

### Post by LinuxGuy1234 on 2007-12-27
> **D45 said:**
> BTW till I download and burn new ubuntu


I want to know how to  fix this broken upgrade

Now, I understand that an upgrade to 6.10 is not painful, but how did you upgrade? (GUI way or command line way, which causes problems)

Now your upgrade to 7.04 is painful. I'll see if problem happens in a chroot.

BTW, it's late at night (10 PM), so I will do the chroot case tomorrow.

---

### Post by D45 on 2007-12-28
GUI way

---

### Post by D45 on 2008-01-27
I HAVE UPGRADED TO 7.10 .  Same appears again.
But I figure out that problem is Nvidia 

when switch to onboard graphics it works fine .
But with Nivida it does not load

---

