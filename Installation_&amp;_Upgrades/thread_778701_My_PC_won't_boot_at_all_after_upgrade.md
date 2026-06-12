---
title: "My PC won't boot at all after upgrade"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by piva on 2008-05-02
Hi, 

I've already searched the forums and have not found any similar problems...

I'm an Ubuntu user for a few years, and was really excited with Hardy coming out. So, last night, I dist-upgraded my desktop computer from 7.10 to Hardy. I left it doing all the install and went to bed. This morning, everything was done, it seemed it didn't get any errors, so I've restarted to complete the install. 

It happens that when I turn the computer on, I get a screen with green stripes, before the motherboard splashscreen, before BIOS screen, before the grub menu, before I can try to do anything. Eventually the green screen turns to a black screen and nothing happens.

Has anyone seen a similar problem? Or at least have any suggestions on how to start working around this?

Notes: 
I have a Radeon X800 (Someone posted somewhere that had boot problems with an ati video card).
The green stripes screen looks like what you get when you have a messed up xorg.conf .

Thanks in advance.

---

### Post by bobnutfield on 2008-05-02
Hello

Sorry you are having trouble with your upgrade.  If this is happening immediately after you switch on the power, even before the post-up screen, then your hard drive is not yet engaged and it is not anything to do with Hardy.  I had a similar issue a while back and it turned out to be a failing video card.  Try removing the card and reinserting it.  That worked initially for me, but eventually the card totally failed.

Hope this helps.

Bob

---

### Post by piva on 2008-05-02
Thanks, I'll try checking my hardware connections when I get home. It just seemed really weird that everything was working fine until I restarted the system after the dist-upgrade.

There is no way Ubuntu modified hardware, such as BIOS or video card settings right?

---

### Post by weedwacker on 2008-05-02
> **piva said:**
> Thanks, I'll try checking my hardware connections when I get home. It just seemed really weird that everything was working fine until I restarted the system after the dist-upgrade.

There is no way Ubuntu modified hardware, such as BIOS or video card settings right?

Another possibility is that the video card fan (if your card has one) is dead.  I had a similar problem and it was a non-functioning fan on the video card.

Good luck with this.

---

