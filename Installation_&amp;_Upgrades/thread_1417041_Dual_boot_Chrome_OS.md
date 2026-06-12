---
title: "Dual boot Chrome OS"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by vishnumrao on 2010-02-26
I am trying to dual boot [hexxeh's Chrome OS build]("http://chromeos.hexxeh.net/"), with my existing HP MIE (HP's heavily customized version of 8.04), on my HP mini 1120NR. 


I used instructions on the [dual boot wiki]("http://chromeos.hexxeh.net/wiki/doku.php?id=multiboot") at hexxeh's website. 

In step 3 I copied the contents of the USB drive to previously created partitions. However step 4 does not update the grub menu. 

Am I doing something wrong or is there something missing in the wiki?

Has anyone tried this on another machine running Ubuntu? If yes, can they post their menu.lst file contents. I will manually edit the menu.lst on my HP Mini.

Thanks,
Vishnu Rao.

---

### Post by oldfred on 2010-02-27
I do not know chromeOS but this script will list everything about your boot process, so we can see if there is something obviously wrong.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by vishnumrao on 2010-02-27
Thanks for the link. I dnld he bash file and executed. Please see the attached file for the results. 

I am not sure what you meant by highlight and use code tags!!

I the the changes listed below to my menu.lst file. I choose chrome OS from the boot menu. It starts booting into the Chrome OS, but fails at some point and drops to a shell prompt. I will click a pic at the next start up and post it as an update. can you tell me where I am wrong? 

```
title		HP Mi (Mobile Internet)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-lpia ro boot=disk resume=/dev/sda2 ht=on clocksource=hpet reboot=a acpi_os_name=Symphony  quiet splash delayloop
initrd		/boot/initrd.img-2.6.24-22-lpia
quiet

title 		Chrome OS
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.31.4-intel-menlow
initrd		/boot/initrd.img

title System Restore
root (hd0,2)
chainloader +1
boot
```

Thanks again.

---

### Post by vishnumrao on 2010-02-27
Update:

After adding the above changes to the menu.lst and choosing Chrome OS from the boot menu, I start boot where it fails and falls back to a shell

Please see attached pic for a screenshot.

---

### Post by oldfred on 2010-02-27
Did you have some other partitions before? Your hp boot says to go to sda2 on error and system recovery was probalbly there before your install. It seems the HP update of grub does not work the same as ubuntu's update.

We can add a manual entry by copying the grub2 version and edit it back to grub legacy (i think). Grub does not use {}, it has root or rootnoverify instead of  set root = and no mods like the ext2 line.

So something like this should work, hd0,1 looks like a boot parition, so I am using that.

title   ChromiumOS 
root    (hd0,1)
linux   /boot/vmlinuz root=LABEL=C-ROOT rw noresume noswap i915.modeset=1 loglevel=1 quiet
initrd  /boot/initrd.img

---

### Post by vishnumrao on 2010-02-27
oldfred,

I think my original problem of grub entries is solved(I could be wrong.). The reason I think so is that, after adding the changes I did to the menu.lst, I am able to choose Chrome OS and boot up. But the boot up halts mid way and falls back to a shell as shown in the screenshot. 

The bootup complains about not being able to find /proc/modules. Do you have any inputs? Or maybe now I should try to contact Hexxeh?

---

### Post by oldfred on 2010-02-27
It is beyond me. I just know booting in general and more specifics for Ubuntu or dual booting with windows. Good Luck.

---

