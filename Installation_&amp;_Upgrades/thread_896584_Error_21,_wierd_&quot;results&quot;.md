---
title: "Error 21, wierd &quot;results&quot;"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by gmcalabr on 2008-08-21
Hey all,
I'm pretty new here and don't know too much about Linux.

I've been having Grub startup error 17/error 21's depending on the hardware that I'm plugging in.  I've been looking at suggestions from all other posts on this subject, but none of them seem to portain to my problem...

After an update and a file transfer from my brother's possibly virus infected external hard drive, I restarted Unbuntu and began getting grub loading errors.  The live cd worked only once (any of my three, including an old copy of Knoppix), and now will not load past a low-graphics mode error and a few more lines of text, so live cd's seem to be out of the question.

Current situation: boot my computer, "Loading Grub 1.5...error 17 (21)"  Now, I'm running a raided sata Windows partition as the secondary and an old IDE as the primary Linux drive.  However, when the linux drive is plugged in, I get error 17.  When I don't, I (semi) logically get error 21.  However, I still get grub loading errors when no harddrives or any other storage devices (including sata and usb) are present.  Nothing more can be done once the computer reaches this point, and the computer will still reach this error and stop even when the only hard drives are Windows drives.

In checking my bios, everything as far as existing drives and boot order are correct, and I've tried every combination of drives and orders, nothing works.

Again, live cd's don't get me anywhere because they never load the GUI.  I've tried getting to the point in the loading where all processes stop and hitting ctrl+alt+f7, but the GUI never loads.  I can use f1 to access a command line, however I think that I'm only exploring the cd and not a hard drive, and I can't figure out how to change that/disable grub/etc.

My Windows Vista disc also can't find anything wrong with the boot (presumably because the problem exists on the mobo/other drive).

Can anyone help me?  Sorry for the long email; I figure I've gotta get everything I know out now because I have limited access to computers.

---

### Post by maybeway36 on 2008-08-21
[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")
With luck, you'll be able to boot Ubuntu with this. There are both CD and floppy versions.

---

