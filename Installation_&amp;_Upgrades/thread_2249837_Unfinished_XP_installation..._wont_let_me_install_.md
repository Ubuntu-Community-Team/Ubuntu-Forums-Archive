---
title: "Unfinished XP installation... wont let me install Ubunto"
date: 2014-10-24
forum: Installation &amp; Upgrades
---

### Post by brian20 on 2014-10-24
Just inherited a gaming tower from a friend, when I try to turn it on it requires the Windows XP service pack 3 disk.... I want to install Ubunto, however i created a boot disk, wont pick up, created a jump drive boot disk, wont pick up...  Always goes back to Windows XP service pack 3 disk request.   None of the F12 options respond to the disks... anyone have any advice?

---

### Post by JKyleOKC on 2014-10-24
You may have to get into the BIOS setup screen and change the "boot order" so that it looks at the CD/DVD drive or USB ports first. Getting into BIOS varies from one make of machine to another but usually there's a VERY brief display immediately when you turn power on that tells how to get there. On HP and Compaq machines it's often function key F10. On my older Win98SE systems it was DEL on one and F2 on the other (both were custom builds, but had different brands of BIOS ROM chips on them).

---

### Post by brian20 on 2014-10-24
Thanks JKyleOKC, that got me a little farther, but now it acts like its going to prep to load and says:

Loading operating system...
Boot from CD/DVD :
Boot from CD/DVD :

then goes right back to trying to load windows XP...

---

### Post by JKyleOKC on 2014-10-26
That makes me suspect that the CD isn't being recognized as bootable. That used to be a frequent problem; the programs to burn CDs defaulted to simply copying the files from inside the ISO image, rather than just copying the entire image. You had to find the option to "burn image" or "make bootable" and that hid in various menus, varying from one burner program to the next. This is something you might check.

Another possibility is that the ISO file itself was corrupted during download, making it unusable. You can check for both these problems by attempting to boot from the CD in a Windows machine; it won't touch the hard disk until you tell it to, so no damage to the Windows system is likely. If it does boot, you should see an option to test the CD/DVD on the initial menu. If the Windows madhine just boots normally into Windows and then displays the files on the CD/DVD, you have the first problem.

Getting started the first time is often a bit of a hassle since so many things can go wrong and it's difficult to diagnose from a distance. Hang in there and we'll probably get you going.

I'm having some relatively minor surgery tomorrow so may be away from the forums for a day or two, but someone else should pick up if these suggestions don't get you a bit farther down the yellow brick road...

---

### Post by Bucky Ball on 2014-10-26
Yes, how did you create the install media? Did you copy the ISO or did you burn a disk image? You need to do the latter to make it bootable.

You can use something like Universal USB Installer on Windows if that's what you're using for a bootable USB.

---

