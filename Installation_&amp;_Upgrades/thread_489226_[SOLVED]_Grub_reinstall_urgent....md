---
title: "[SOLVED] Grub reinstall: urgent..."
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by opossumjack on 2007-07-01
Hi... My primary hard-disk is going to die... but I installed the boot partition and GRUB on it....

any Idea on how can I reinstall GRUB on another partition without reinstallng anything on my computer? 

Is there a way I can deactivate my boot partition on primary HD and install it on another HD?

I need a solution because I have important datas on my Computer and I need them... :(

Thanks in advance...

---

### Post by Levander on 2007-07-01
Not exactly sure why you wanna do what you say you wanna do.  Are these important "datas" also on the primary hard disk?  

If not, will booting from the LiveCD accomplish, and then mounting the partitions that have the important datas onto that filesystem accomplish what you want to accomplish?

On what partition are the important datas on now?  Where is this partition mounted?

---

### Post by opossumjack on 2007-07-01
the datas I need are on another partition... and I managed to get them via Live-cd...

But I have my computer down yet.... if I can't move my boot partition on another HD....

All I want to do is change the primary Hd with a new one and reinstall GRUB for example on the linux partition... that is not on my primary HD, but on a secondary SCSI HD...

---

### Post by Levander on 2007-07-01
Is this other partition that has the datas on the same hard disk?  If so, you need to back them up onto something external, like a CD, DVD, or even another hard disk.

You could try to figure out how to do a full backup, but if the drive is already failing, taxing the hard disk by trying to read the whole thing to back it up probably won't work.  You'll probably get read errors.

The easiest thing to do would be to backup your important datas, reinstall Ubuntu, and restore your datas from backup.

This, unless your boot partition is the only thing on this failing disk.  Which is kind of an odd configuration.

Do you already have another hard disk you could install Ubuntu on?  If not, of course you need to buy one.

If it is the case that all you have on the failing disk is the boot partition, here's the best looking HOWTO I just found on the wiki for installing grub.  I'm assuming you want grub on the master boot record because you are not using another boot manager.  The guide is for if a Windows install has overwritten the MBR, but the same thing applies for your situation, where the MBR has been "overwritten" because the hard disk failed:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Before you follow that guide though, I think you'll need the hard disks in your system already attached like you want them end up attached.  E.g., you'll want to remve the failing hard disk.

---

