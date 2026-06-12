---
title: "Is persistent USB available for installed Ubuntu?"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by sanicki on 2007-01-05
I am investigating Ubuntu to replace XP in my workplace. I would like to give my users the ability to carry their OS home with them instead of their laptop (LiveCD with persistence in USB pen drive) but I don't want to sacrifice speed when they're in-office and I haven't seen any posts on whether that would preclude OS updates.

My main question though is: Is it possible to have Ubuntu installed on the hard drive but still utilizing a pen drive for persistence? I would like to have an office build of Ubuntu that is installed on every machine here and a stack of the same build as LiveCDs for folks to take home. Then their USB pen drive becomes their life.

(A secondary concern is pen drive writes, but I figure I can minimize this by having users save their docs via FTP for example. But I'm also curious if the pen drive could be set up to essentially redirect Ubuntu to look for profile information in an online repository. Anyone ever try anything like that?)

Thanks in advance for any thoughts/advice,
Scott

"The more original a discovery, the more obvious it seems afterwards." -Arthur Koestler

---

### Post by earobinson on 2007-01-05
if you use dsl they could have the whole os on the pendrive

---

### Post by sanicki on 2007-01-05
I have considered DSL, but my understanding is that booting from a USB isn't supported by all BIOS. Then there's the speed of in-office USB, plus I may be able to get the users to accept OpenOffice but not the DSL alts so there'd be more customizations to be done, also I can sell the idea of moving to Linux to the CEO because he's such a Google fan.

That and (I probably should have mentioned this at the start) I'm new to the Linux world myself so I'd rather stick to the leading distro.

---

### Post by sanicki on 2007-01-05
I also did some brief reading on the now-obsolete SLAX [webconfig]("http://www.slax.org/webconfig.php"). Is there anything like that for Ubuntu or Ubuntu LiveCD?

"If at first the idea is not absurd, then there is no hope for it." Albert Einstein

---

### Post by confused57 on 2007-01-05
Could this work?:

[https://help.ubuntu.com/community/LiveCDPersistence?highlight=%28persistence%29](https://help.ubuntu.com/community/LiveCDPersistence?highlight=%28persistence%29)

---

### Post by sanicki on 2007-01-05
I've already got a LiveCD with persistence set up. Works just fine. But my concerns are:
1) Speed. LiveCD is slower than installed Ubuntu so I want it installed on office machines. But once installed I don't know if I can still carry profile info around on a USB Stick.
2) Divergence. Does the LiveCD check for OS upgrades (and if it does I imaging they're saved to the USB Stick too...see #3)? Provided I get past #1, would a USB Stick created using a static LiveCD still work on an installed Ubuntu that's been regularly upgraded?
3) USB Stick writes. You only get so many. I'd hate to put my users lives on them and see them start failing quickly.

"If the world should blow itself up, the last audible voice would be that of an expert saying it can't be done." -Peter Ustinov

---

