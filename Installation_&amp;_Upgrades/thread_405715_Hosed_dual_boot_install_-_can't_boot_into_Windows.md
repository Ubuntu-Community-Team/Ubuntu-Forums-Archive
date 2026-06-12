---
title: "Hosed dual boot install - can't boot into Windows"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by Kawinma on 2007-04-10
I've installed Ubuntu onto my laptop (an Acer Aspire, no floppy drive) and managed to hose my Windows install **somehow.** I'm no newbie to Linux -- more of an intermediate user, really -- and I had Acronis Boot Selector as my previous bootloader, with Slax as the last distro on here.

Long story short, replaced Slax with Ubuntu, didn't remember to find the option to stop GRUB from forcing itself on my partition, and ended up with GRUB as my new bootloader. When I try to boot XP, I see the boot options at the top of the screen and the rest is pure black.

I tried to use another bootloader (GAG) and it wouldn't boot Ubuntu or WIndows, but Linux can read from the partition fine.

I don't know what happened, but I hope I can get help from you guys!

Windows is on /dev/hda2, Linux on /dev/hda1, and swap on /dev/hda3

Thanks in advance! :)

---

### Post by koshari on 2007-04-10
you may have a problem with ntfs bootloader, if this is the case you will need to run" fdisk mbr" or whatever the windows command is, then you will need to boot with a live disk and re run the grub conf.

---

### Post by dbrjay on 2007-04-10
I reccomend first fixing your windows boot loader using fdisk/mbr and then booting into ubuntu using the installation disk. Configuring grub to dual boot and make a boot floppy, modding grub.list to solve any booting problems. 
Once boot disk works transfer to the MBR and you should be able to dual boot from the HDD.

---

### Post by Kawinma on 2007-04-10
After digging around, and finally finding, a Windows XP CD (the laptop didn't come with one, but I had one from my old PC) and booting into recovery mode, I did fixmbr by itself. Warned me about my partition table, said screw it, and went through with it.

That put my lappy in a reboot loop.

Then I went back in, and did fixboot too. Rebooted, and INTO WINDOWS! Then Outpost whined, rebooted to fix it, and Acronis graciously reinstalled the boot loader I know and love.

Long story short, **Acronis Boot Loader rocks, fixboot + fixmbr are the two proverbial duct tapes of dual-boot problems, and Ubuntu works perfectly!**

---

### Post by JayDeePlus on 2007-04-10
i have this same problem trying to boot into vista after installing edgy. i am still not able to boot into vista. i see the windows vista option in the boot screen, it gets to the loading screen of windows, then it goes to another black screen with a live mouse and not able to go any further.

is there a possible solution other then getting the intall CD? my comp came with vista, so there was no CD. and i fear that if my files is still on me vista OS , then running a install CD may erase that info.

what is another solution?

---

### Post by dbrjay on 2007-04-11
Hi Jay  xD

what i suggest you do is boot into GRUB (should boot into GRUB after the linux installation) and select 'Windows' from the list. Otherwise get yourself a SuperGRUB disk (CD) and use this to fix the MBR so that it can boot into Windows.  This is an option on the SuperGRUB disk...once this is done you can boot into Windows and then you can configure GRUB so that dual booting is possible. .

Any questions, 
email or PM me or something.

---

