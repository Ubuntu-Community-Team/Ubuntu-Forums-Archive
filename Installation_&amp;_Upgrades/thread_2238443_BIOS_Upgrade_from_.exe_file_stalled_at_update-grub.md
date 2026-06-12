---
title: "BIOS Upgrade from .exe file stalled at update-grub"
date: 2014-08-07
forum: Installation &amp; Upgrades
---

### Post by nathan46 on 2014-08-07
Hello!

I have an old Compaq that I am trying to get Ubuntu Server 14.04 set up on.  It needs to have a bios upgrade in order to start without a keyboard attached.  There is no floppy disk drive, so I thought I would educate myself on alternatives.  I followed the directions here: [HTML]http://ubuntuforums.org/showthread.php?t=318789[/HTML] up to the point where I need to generate a new grub.cfg file.  I used these instructions: [HTML]http://ubuntuforums.org/showthread.php?t=1545929[/HTML] to generate the file 50_memdisk in the /etc/grub.d directory.  These instructions work until I hit the qemu-system-i386 command which aborts due to an SDL error.  I have renamed the image from the first post to match the new name in the second post.

After I have everything set, I run ```
sudo update-grub
``` and it generates the following error after showing the current installation and memtest lines: 

```
/boot/grub.d/50_ memdisk: 5: /boot/grub.d/50_memdisk: usr/lib/grub/grub-mkconfig_lib: Permission denied
```

I have looked (someone may say not hard enough) for a solution trying to get this to work.  Might have been easier to plug an old floppy drive in for a few minutes, but then I wouldn't know how to do this...

Any help would be appreciated!

Thank you for looking!
Nathan

---

### Post by mörgæs on 2014-08-08
Hi, welcome to the fora.

If you are able to boot from USB the easiest is to create a USB stick with Freedos and run the .exe file from here.

---

### Post by ubfan1 on 2014-08-08
Double-check with the vendor about what type of exe file they are supplying.  Compaq/HP may be supplying only a Windows version, not the necessary DOS version your instructions assume.

---

### Post by grahammechanical on 2014-08-08
Did you make 50_memdisk executable? Just a thought.

---

### Post by MartyBuntu on 2014-08-08
> **nathan46 said:**
> Hello!

It needs to have a bios upgrade in order to start without a keyboard attached.

Are you sure there's no **HALT ON NO ERRORS** setting in the BIOS?

---

### Post by nathan46 on 2014-08-10
For some reason, the computer needed to write to the A:\ drive during the BIOS flash.  I never did get that figured out.  However, after looking at some more forums, I found this one [http://www.vintage-computer.com/vcforum/archive/index.php/t-1492.html](http://www.vintage-computer.com/vcforum/archive/index.php/t-1492.html).  I was able to get the computer to boot without the keyboard after following setting it up in server mode.  Thank you for the advice.

---

