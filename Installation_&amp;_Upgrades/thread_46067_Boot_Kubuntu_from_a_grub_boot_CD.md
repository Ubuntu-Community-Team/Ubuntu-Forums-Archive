---
title: "Boot Kubuntu from a grub boot CD"
date: 2005-07-03
forum: Installation &amp; Upgrades
---

### Post by datu on 2005-07-03
OK here goes . . . Im an intermediate MSWndows users with very little knowledge of Linux as a whole. So anything that comes close to the same opeartion as Windows is appealing to me. I am familar with the command line in windows but not for linux. After trying some different linux distros over the years off and on (More off then on) i tried Kubuntu and i like it.

Having that said, i tried to install Mandrake i believe in a dual boot system with WinXP using GRUB. long story short my MBR was corrupted and i lost everything, Grrr vowing never ever again to install linux. But curiosity killed the cat and here i am again.

What I have done was installed Kubuntu to an external USB 2.0 6GB HD with no probs at all, but when i got to the install GRUB part, i skipped it and went straight to the finish setup. It asked me if i want to make a boot disk , my problem is i dont have a floppy drive and would like to boot from my CD Rom drive with out installing nothing into my MBR which is occupied by WinXP at the moment.

I poked around Google and found some stuff about GRUB.iso and what not but its all done from within Linux itself and im not very comfortable with that right now.

Basically what i would like to do is, instead of making a boot disk, i want a boot cd. Mkae sense? Or point me in the right direction?

Forgive me if this is a stupid post but i didnt see it anywhere else on the forums. Thnx.

---

### Post by mingus on 2005-07-03
[I]I poked around Google and found some stuff about GRUB.iso and what not but its all done from within Linux itself and im not very comfortable with that right now.

Or point me in the right direction?[/I]

*I have done was installed Kubuntu to an external USB 2.0 6GB HD*

Theoretically possible outside of Linux, but not feasible.  Here is a post that enabled one user to create it from within Linux:
[http://www.linuxquestions.org/questions/history/336446](http://www.linuxquestions.org/questions/history/336446)
Other than creating a coaster, I can't see any risks.  BTW, K3B will burn the .iso just fine; you don't need a commercial product like Nero to do that.

If you cannot boot into Kubuntu now, here is how you can easily get in to do this with a Live-CD:
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)
Or you can get into Kubuntu from you install CD, although a bit more complex.

I assume you cannot set the USB device as bootable in your BIOS?  If it does, you can install grub to the boot sector of the USB disk, boot from it, and dual-boot W$ from there.

*Having that said, i tried to install Mandrake i believe in a dual boot system with WinXP using GRUB. long story short my MBR was corrupted and i lost everything,*

Sorry about that.  Restoring the W$ MBR is simple if one has XP media or can boot from floppy.  It is also easy (with the Linux dd command) to create a backup copy of the XP MBR; same command can restore it.

---

### Post by datu on 2005-07-03
Thanx for the reply mingus, alot of info there for me to digest although i did already view that forum post ulinked to. Couldn't make much sense of it, im still a Linux N00b and not giving up windows. hahaa

I think in the end that this is all a little more then i can chew right now, i need something alot easier. Since a couple failures with GRUB and MSWindows im just not willing to use it as my dual booter.

I guess ill just stick to Live CDs since i upgraded to 1GB of Ram, but i appreciate ur help. Thnx a Mil.

---

