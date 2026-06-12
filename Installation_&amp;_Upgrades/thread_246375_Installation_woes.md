---
title: "Installation woes"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by cluke on 2006-08-29
Having heard good things about Ubuntu, I decided to try it out, but I have had a nightmare with the install.

First, I downloaded the live CD and had a play with it. I like it, so tried to install on a partition on the clean slave hard drive (with windows on the main). The installer crashed, around 80% at configuring system locales. I tried again, tried to surf whilst the install was going, the installer hung. Tried again, it crashed again. Tried picking a different locale (London instead of Dublin this time), it got past 80% but still ultimately crashed.

OK, try the text mode installer. Did a cd check, then ran the install. Failed saying I had a corrupt file (the kernel of all things). Try again, new disk. Failed at a different point.
Managed to install in OEM mode. Booted me to a shell with numerous errors. I did the adduser thing rebooted. Dumped me to a shell with numerous errors. Hmm.. shouldn't I be seeing a GUI here?

I decided to try the Live install again. It crashes. I give up and go to Windows XP. Grub error 15, boot fails. In a cold sweat, i go back to the Ubuntu text install option. It fails again half way through, but allows me to reinstall Grub so it can now at least boot XP. I can also boot to the Ubuntu log-in screen, but it doesn't recognise the user name i created.

I am totally behind what Ubuntu is trying to do, but I think you guys really need to work on the install process to make it as friendly as possible. This is the first exposure a lot of people will have to Linux and if it as painful as mine, I think you are more likely to put people off!

If anyone needs more details to maybe track down problems, I will help if I can! But the errors seemed quite random.
I have a slightly oldish AMD based PC, with a Nvidia 6200, nothing weird.

---

### Post by wpshooter on 2006-08-29
Cluke:

Please see my post here:

[http://www.ubuntuforums.org/showthread.php?t=246192](http://www.ubuntuforums.org/showthread.php?t=246192)

Any thoughts ?

---

### Post by cluke on 2006-08-29
I have to admit, I at first suspected my CD drive as well, but I burned multiple copies at the slowest speed with the Nero verify data check on, and also I have had no problems with CD burnt in the past, so I think I can rule that out...

---

### Post by lando on 2006-08-29
I've having same hang-up issues on install.  I can't get past 47%

---

### Post by wpshooter on 2006-08-29
> **lando said:**
> I've having same hang-up issues on install.  I can't get past 47%

Lando:

Please note that mine does **NOT** hang.

It **always completes** the install.

My question is why it takes it 3 to 4 minutes to do the file copying on one install.  

And then if I decide to go back and do the install over again it might take 15 to 20 minutes to do the same file copying portion of the install.

If it is doing the exact same installation to the exact same hardware system, shouldn't this copy process always be roughly equal each time ???

Has anyone else ran across this ???

Thanks.

---

### Post by spamolamah on 2006-09-07
Hi, this is an uncommon but repeatable problem. I have exactly the same symptoms as you. I never got around to fixing the problem and moved on to just using the i386 version.

If you want, can you compare what similar hardware you have to my post. Maybe we have a bad cpu stepping or some common hardware that is buggy. (This also happens in AMD64  Edgy)

[http://www.ubuntuforums.org/showthread.php?t=187372]("http://www.ubuntuforums.org/showthread.php?t=187372")

There are also other people with the same issues as us. I really should get a null modem cable and post the kernel panic.

Here is the post where someone has a kernel panic and reboot on rebuilding the locales
[http://www.ubuntuforums.org/showthread.php?t=83315]("http://www.ubuntuforums.org/showthread.php?t=83315")

---

