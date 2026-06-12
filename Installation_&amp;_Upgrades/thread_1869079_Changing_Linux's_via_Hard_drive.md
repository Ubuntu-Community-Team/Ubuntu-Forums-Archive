---
title: "Changing Linux's via Hard drive"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by Mackay508 on 2011-10-25
So im looking to change from Ubuntu 11.10 to Lubuntu but I have some problems after burning the upgrade disc my CD drive doesnt seem to read CD's so I tried a few fixes but nothing worked so I think the lasers blown. 

So thats the CD drive out the way of upgrading and after I installed 11.10 I cant seem to get any of the programs to work like Update Manager, Startup Disk Creatior etc so again thats out the way.

Would it be possible to upgrade via a external Hard-drive if i got the ISO burnt onto it? But here comes the tricky part would I be able to set the Hard-drive up on another computer and then use my current one to receive the upgrade? And if it does should my computer run all the programs with no problem unlike currently.

Any help is much appreciated.

---

### Post by jnorthr on 2011-10-25
just wondering if the CD you created was faulty so as to cause all your bother.  I'm assuming you've made a live CD, that's one that a system could possibly startup from, if it's in your Cd drive when you re-boot.

You might try taking that CD to a different system and booting lubuntu from the CD there. If it does not boot, it may be that your CD was burned incorrectly. I've had this prob. b4 when the CD's were burned at too fast a speed. If you can find  a way to re-burn your CD at the lowest possible speed, it might be more successful. Just to confirm your Cd is downloaded properly, you can do what's know as an MD5 checksum. This is a little program that computes a digital summary value from a downloaded file. It is printed out and you can then compare your checksum with the advertised checksum on the download page. They should match else you've got a failed download. I alway MD5 checksum b4 burning my CD's. good luck.

---

### Post by oldfred on 2011-10-25
You can use grub2's boot loader to directly load an ISO without extracting it. I have multiple ISOs on flash drives & my other hard drive that I can boot from grub's menu. You can create your own grub.cfg or edit 40_custom if a full install.

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by jnorthr on 2011-10-25
have always wanted to boot from usb keys but my poor old system is so old it does not offer the choice in bios to boot from usb. Can grub2 do it even when the bios cannot ?

---

### Post by oldfred on 2011-10-25
No, BIOS has to allow it.

But plop is a work around.

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

---

