---
title: "Dual-boot Windows 7 &amp; Ubuntu 14"
date: 2015-03-15
forum: Installation &amp; Upgrades
---

### Post by Shadius on 2015-03-15
Hi everybody,

I'm trying to dual-boot Ubuntu with a Windows 7 PC, but the Live CD won't boot, it just hangs after I choose "**Install Ubuntu**" or any other option.  What can I try?

---

### Post by fantab on 2015-03-15
More info about your machine... Tell us more to understand what is going on....
Sometimes a bad burn or a faulty downloaded .iso can create such problems.
If Windows is Hibernating you will need to disable that and shut down Windows properly.

---

### Post by Mark Phelps on 2015-03-15
You shouldn't just blindly force an installation of Ubuntu on an untried PC -- you don't know how well it will work, if at all.  You should boot from the install media and choose the Try option -- to see how well it detects the hardware and loads the right drivers.  Any problems you then find can be researched before you do the installation.

---

### Post by Shadius on 2015-03-15
I've installed Ubuntu on this PC previously.  However, I had to put in a new hard drive in it and then installed Windows 7 Professional on it.  Now when trying to install Ubuntu 14.04, it gets to the "Try Ubuntu" and other options screen, but when I choose any option, nothing happens.

---

### Post by Shadius on 2015-04-05
Bump

---

### Post by Mark Phelps on 2015-04-06
I've read that 14.04 has installation problems, so they pulled the downloads.  At this point, you should be trying 14.10.

---

### Post by leunam12 on 2015-04-06
Backup your hard drive first. Make sure that nothing has changed in BIOS that would prevent Live system from booting up. Make sure that you have a properly downloaded ISO (check the MD5SUM). Burn a bootable USB stick; pull the RAM out and re-insert it, and try booting from USB. I work with a lot of computers and on some systems CD's (DVD) don't boot at all, while on other systems USB sticks don't boot but CD's do. Some distributions boot better from CD, others from USB stick. On my current computer that I use at home the only distro that I can boot from DVD is clonezilla; all others fail and I have to boot them from USB. I don't know why this is so.

---

