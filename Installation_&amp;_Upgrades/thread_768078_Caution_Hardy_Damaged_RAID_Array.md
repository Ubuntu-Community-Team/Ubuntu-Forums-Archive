---
title: "Caution: Hardy Damaged RAID Array?"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by DougS on 2008-04-26
Early warning:

Tried to boot from Hardy 8.04 Live CD with "Make no changes to your computer" option.

I  had W___________ software RAID 0 (Mediashield array)

Some action then just stopped.

On attempting rebooting the array is obviously damaged and looks as though everything is lost.

I realise this is my own fault but please be aware if you have a similar setup!

I know little about these arrays (has been working fine) but if anyone knows a quick fix before I start to re-install everything then I'd be grateful to know.

I really want to know and love Ubuntu but it's things like this which say it's not quite there yet (although this could be viewed as a particularly arcane set up, I'll bet there's lots of them out there?)

Regards
Doug

---

### Post by Blackkatt on 2008-04-27
> **DougS said:**
> Early warning:

Tried to boot from Hardy 8.04 Live CD with "Make no changes to your computer" option.

I  had W___________ software RAID 0 (Mediashield array)

Some action then just stopped.

On attempting rebooting the array is obviously damaged and looks as though everything is lost.

I realise this is my own fault but please be aware if you have a similar setup!

I know little about these arrays (has been working fine) but if anyone knows a quick fix before I start to re-install everything then I'd be grateful to know.

I really want to know and love Ubuntu but it's things like this which say it's not quite there yet (although this could be viewed as a particularly arcane set up, I'll bet there's lots of them out there?)

Regards
Doug

No and no :) your RAID was not broken. You only need to power of your PC by unplugging the power cord or just the press the power switch on the back of your PC, because your RAM still have information from the Live session. How do i know this? it happed to me as well. And i think before i react ](*,) and there is no way a Live session can alter your RAID aka hardware. It's to late for your now. But for the rest of ya :guitar: 'on

---

### Post by dryer on 2008-04-28
Yes, I had the same issue as well, it appears it does not recognize RAID 0, and installs on one of the drives only. So I guess that's a limitation for the desktop version, does anyone know if the server version is ok with SATA drives running RAID 0?  I'm going to try that tonight and add the GUI if all installs ok.

---

### Post by bigal99 on 2008-04-28
I'd like to know what you find out. 

With 7.10, there was an 'alternate' distro CD which had raid support during installation.

---

### Post by DougS on 2008-04-28
I believe I did switch off and reboot as this happened Friday night so I switched off and tried again Saturday until I was certain that it was impossible (for me) to find a way to fix it.

I will check this out before doing a full re-install.
Thanks for the ideas.
Doug

---

### Post by nickprandomnumber on 2008-04-29
The same thing happened to me, sort of. Stupidly, I assumed that something like Ubuntu 8.04 LTS would automatically support hardware (edit: pseudo-hardware) RAID.

Upon trying to install 8.04, the partition screen went right off the edge of my screen and just kept on going, leaving it a bit unusable. Discovered that it hadn't detected my raid array, so decided to reboot to see if i could find out how to install on a partition in a raid array.

At that point, mediashield did that horrible thing that we never hope to see - the red flashing error of death.

I turned my machine off, powered down and started up. Mediashield then said the array was fine, but still wouldn't boot.

As there was no 'os not found' message, just a blinking cursor, i rebooted and specifically selected my RAID array from my many hard disks in the BIOS boot menu. At which point, all was well again.

Would still love to know how to install 8.04 on a partition inside a RAID array, though. I think I'm going to back up everything important before trying again. :D

Almost gave me a heart attack, but it's my fault for storing anything important on a striped array, anyway.

---

### Post by st0nedpenguin on 2008-04-29
All you need to do to install on fakeraid is boot from the live CD, add the universe repo to your sources, install dmraid, carry out a regular install, then chroot into your new install and make sure you install dmraid there too. Everything should be working fine after a reboot.

[http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation](http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation)

Covers the whole process, just reboot after installing dmraid on the new install and ignore the parts related to manually installing Grub.

---

### Post by nickprandomnumber on 2008-04-29
St0nedpenguin:

Thanks for the link, found that same one earlier today.

Sadly, it still doesn't work - there is a problem between dmraid, the version of the kernel 8.04 uses and (it seems) nforce 680 motherboards or WD Raptors as i have discovered many others having this problem dotted about the net.

dmraid detects and displays the striped array ok, but creates a dev/mapper device that is the size of only one of the drives, causing partition managers to have a fit as the partition exceeds the size of the drive. Therefore, it seems, that although dmraid displays the array information, it actually believes that the array is made up of one disk.

See here:
[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/136804](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/136804)

Might have to go with Fedora 8 or Mandriva as (in the link) it appears they work.

Over the years, I have had nothing but trouble installing Ubuntu - I would really like the chance to use it properly, but there are always silly issues like this one that simply don't occur (for me, at least) with certain other distros that I have been forced to try.

The only time I successfully managed to install Ubuntu and get everything working (on a friend's computer) was shortlived as an update, mere hours later, completely hosed X. :(

I guess, if I have the time, I could install 8.04 on a single HD, update the kernel to see if there's any improvement and then manually move everything over to the array if it's found successfully. 

If you can think of a better idea, please let me know.

---

### Post by useless-b on 2008-05-30
> **Blackkatt said:**
> No and no :) your RAID was not broken. You only need to power of your PC by unplugging the power cord or just the press the power switch on the back of your PC, because your RAM still have information from the Live session. How do i know this? it happed to me as well. And i think before i react ](*,) and there is no way a Live session can alter your RAID aka hardware. It's to late for your now. But for the rest of ya :guitar: 'on

I tried this, but it broke my raid. I'm using gigabyte's raid, so I guess it's not supported. :( I tried dmraid too, with no luck. I'm sure there's a solution, but I'm kinda noobish still, so I've got lots of reading ahead.

---

