---
title: "Grub Error 17 Still!"
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by mcrane on 2005-11-13
I got zero responses to my other thread (posted 2 or 3 days ago). I probably gave too much detail. That seems to discourage responses for some reason. :)

I try to dump windows every 6-12 months, but there's always something. This time it's a psychotic bootloader. I'm open to any suggestions on how to procede...

Here's the situation. Ubuntu is installed on the second HD on a promise (PCI) fasttrack66 controller (because I have no free IDE ports on the motherboard). After the install reboot I get grub error 17. Booting from a utilty CD which allows me to chain to the HD bootloader results in a perfectly working grub menu. I boot the CD, choose menu item one (boot hard drive) and, voila, a nice menu which allows me to boot ubuntu or xp. This baffles me.

This morning I booted into XP and copied my MBR too the HD and added an entry for that (C:\linux.bin) to boot.ini, then restored the MS MBR hoping the MS bootloader might succeed in chaining to grub as my boot CD does. No luck. Grub error 17 when the MS loader loads C:\linux.bin.

My menu.lst looks good and agrees with device.map. If it were a problem with those I would think that grub would fail even when I chained from my boot cd, but I don't know that much about how grub works.

According to the error 17 description it seems that grub is unable to read the filesystem on the designated HD (in my case (HD3,0) - /dev/hdg1).

I have reinstalled grub several times, btw, just for good measure.

I'm sure I could solve this problem by repartitioning my first HD and putting my linux partition there, but being forced to do that seems so microsoft. It would also require the moving of a lot of data and maybe a defrag. Considering the other niggling linux issues, I'd probably just pack it in and wait another year for the next great linux hope.

I've gone and provided too much info again, I know. I just can't help myself.  :razz:

Edit: Just noticed this post:
[http://ubuntuforums.org/showpost.php?p=472609&postcount=29]("http://ubuntuforums.org/showpost.php?p=472609&postcount=29")
Maybe Grub just can't deal with some PCI IDE controllers?

---

### Post by yesplease on 2005-11-14
A quick search on google shows that promise provides a linux driver for the fasttrack controller since 2000. I expect is it out of the beta phase by now.

I have no experience with this controller, but I would be surprised if it is not included in Ubuntu.

Also [http://ubuntuforums.org/showthread.php?t=85277&highlight=grub+map](http://ubuntuforums.org/showthread.php?t=85277&highlight=grub+map) might help. Windows likes to be on the first patrtion on the first disk and you can let it believe it is with the map option.

"I'm sure I could solve this problem by repartitioning my first HD and putting my linux partition there, but being forced to do that seems so microsoft. It would also require the moving of a lot of data and maybe a defrag." 

If you cant find help on the driver that might save lots of time.

---

### Post by MakubeX on 2005-11-14
What confuses me is that I had encountered that error too, but in a system with no Wind0ze partition.. how come?

---

### Post by mcrane on 2005-11-14
[QUOTE=yesplease]A quick search on google shows that promise provides a linux driver for the fasttrack controller since 2000. I expect is it out of the beta phase by now.

I have no experience with this controller, but I would be surprised if it is not included in Ubuntu.
[/QUOTE]

Thanks for the reply. The controller works fine under Ubuntu. If I boot my utility CD and then boot the hard drive from that then I can boot into my Ubuntu installation and everything is fine. I just can boot directly from the HD. Haven't tried making a boot floppy because I don't have a working floppy drive.

---

### Post by mcrane on 2005-11-14
[QUOTE=MakubeX]What confuses me is that I had encountered that error too, but in a system with no Wind0ze partition.. how come?[/QUOTE]

Yeah, and I did unplug both hard drives from the promise controller and then got an error 21 (which I would expect). I think it's a problem between Grub this Promise controller. I don't think my windows partition or the other drives have anything to do with it.

---

