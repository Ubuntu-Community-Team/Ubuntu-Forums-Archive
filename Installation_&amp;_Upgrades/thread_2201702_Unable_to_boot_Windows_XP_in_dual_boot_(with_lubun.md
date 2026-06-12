---
title: "Unable to boot Windows XP in dual boot (with lubuntu)"
date: 2014-01-25
forum: Installation &amp; Upgrades
---

### Post by jasper3 on 2014-01-25
I have attempted to configure a dual boot setup (Windows XP Media Center Edition + Lubuntu) but ever since i am not able to boot Windows. The option does appear in the Grub2 interface but using it results in a black screen with just a blinking cursor. Lubuntu does infact load via Grub2, so booting Windows is the only problem.

I have tried Boot-repair but this did not take away the problem. The following boot info script was provided:
[http://paste.ubuntu.com/6815839/](http://paste.ubuntu.com/6815839/) 
The script does say something about the ubuntu boot files being located far away from the "beginning" of the harddisk, potentially resulting in the bios not being able to find them. But this is unlikely since Lubuntu does actually load and windows doesnt? 

Anyone have any tips on fixing this issue? 

Thanks alot in advance!

---

### Post by Keith_Benjamin on 2014-01-25
What are the command line codes being passed by Grub2?

---

### Post by jasper3 on 2014-01-25
What do you mean exactly? Where would I find those?

---

### Post by slooksterpsv on 2014-01-25
I don't know if the boot-repair did repair the Windows partition. If you have a bootable cd of Windows XP (or even if you burn a hiren's boot cd), you may need to run a checkdisk on your C drive. This was a common problem with XP if I remember correctly. You can try to run the boot-repair again and see if it fixes anything or there is another option, it's called ntfsfix.
If you open a terminal window and type in:

```

sudo ntfsfix /dev/sde1

```

We can see if that'll fix the windows volume.

If that doesn't work, run boot-repair again and post the results again.

---

### Post by jasper3 on 2014-01-25
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo ntfsfix /dev/sde1[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
resulted in:
Mounting volume... OK
Processing of $MFT and $MFTMirr completed sucessfully.
NTFS volume version is 3.1.
NTFS partition /dev/sdel was processed successfully.

===============================
I will now retry Boot-repair[/FONT][/COLOR]

---

### Post by slooksterpsv on 2014-01-25
@Keith
```

menuentry "Windows XP Media Center Edition (on /dev/sde1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root AC883E62883E2AEA
	drivemap -s (hd0) ${root}
	chainloader +1
}

```

That's the grub command for his Windows XP.

By the way Welcome to the forums jasper =D

---

### Post by jasper3 on 2014-01-25
Thanks alot! =D

Boot-repair results in: 
[http://paste.ubuntu.com/6816045/](http://paste.ubuntu.com/6816045/)

---

### Post by slooksterpsv on 2014-01-25
It still just blinks when trying to load Windows?  When you select XP can you press F8 and see if you can get to the boot menu options like Safe Mode, etc.

You may need to download Hiren's BootCD via [http://www.hirensbootcd.org/download/](http://www.hirensbootcd.org/download/) and burn that to a CD to run checkdisk on the drive. What data/content do you need off the drive or do you still need XP?

---

### Post by jasper3 on 2014-01-25
Yes it still blinks when trying to load Windows. Pressing F8 does nothing in Grub nor in the black screen.

I can actually access all data/content through lubuntu, I would like to keep Windows XP operational and use Linux as main OS.

I will try the checkdisk option tomorrow.

The GRUB menu is as follows:
[IMG]http://i41.tinypic.com/9lbtw1.jpg[/IMG]

Thanks alot for the help so far, will check this thread again tomorrow!

---

