---
title: "Dual-boot ONLY off of a floppy?"
date: 2005-12-01
forum: Installation &amp; Upgrades
---

### Post by HippoMan on 2005-12-01
I want to create a dual-boot instance of Ubuntu and Windows 2000. I have done dual-boot installations before, and I know how to do this in the normal way. However, in this case, I have a special requirement: I don't want to modify the normal boot record for the machine, and I ONLY want to be able to boot into Ubuntu by means of a boot floppy.

In other words, without a floppy, I'd like the machine to boot up into Windows in the normal, Windows-specific manner, without my seeing anything about Ubuntu at all on the Windows boot menu. But when I boot off of my desired boot floppy, I want to then be presented with a grub menu which will let me choose between booting up into Windows or into Ubuntu.

Is there a way to set up this scenario during the normal Ubuntu installation? I don't want the normal MBR to be modified at all on the machine, and instead, for grub to put the appropriate boot information on a floppy.

I couldn't find anything about this in the forum or on the net, but perhaps I wasn't looking in the right places.

Thanks in advance.

---

### Post by bwog on 2005-12-01
Look here [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253)
Use

 grub-install /dev/fd0

In case grub has overwritten your mbr already you can restore it with the fixmbr command in de rescue mode of the windows XP install disk (probably the same with win2000). Check a windows tutorial for that.

---

### Post by HippoMan on 2005-12-01
[quote=bwog]Look here [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253")
Use

 grub-install /dev/fd0[/quote] Thanks. I've seen this. But doesn't this imply that I have already done a full Ubuntu install, and that I'm sitting at the unix command line after having already booted up into Ubuntu?

If so, then the initial install will have already altered the original MBR, and I don't want this to happen.

How do I perform the dual-boot install of Ubuntu so as not to change the normal MBR, and so that it creates this /dev/fd0 boot diskette *at the time of this initial install*? ... so that the original MBR is still intact after the Ubuntu install.

Thanks again.

---

### Post by Hopsonn on 2005-12-01
Couldn't you do a standard dual boot installation and when asked where to install grub, specify the floppy drive?

It might require that you reset the windows partition as active, but I think this would let you do what you want to.

---

### Post by HippoMan on 2005-12-01
[quote=Hopsonn]Couldn't you do a standard dual boot installation and when asked where to install grub, specify the floppy drive?

It might require that you reset the windows partition as active, but I think this would let you do what you want to.[/quote]
Thank you.

I don't recall seeing an option to specify the floppy drive during the initial boot installation, which is why I posted here ... but perhaps I overlooked it.  I'll try the installation again and see if I can find this option.

---

### Post by vinnyjones on 2005-12-01
I actually have this setup

My computer has two harddrives, one with windows xp and the other with ubuntu linux, the boot priority is for the hard drive with windows xp.. If there is no floppy drive the computer boots in windows, otherwise it boots with linux...

When i installed linux i didn't want to touch the boot record of either harddrive, so when i was asked the question of installing the GRUB bootloader to the primary harddrive, i clicked no. By doing so another menu allowing me to choose where i want to install the bootloader appeared, allowing me to install to the second hard drive and also the floppy drive. I chose floppy drive (/dev/fd0) which installed the GRUB bootloader to floppy...

It was that simple. Obviously if the floppy drive is in the computer, it brings up GRUB which will start up ubuntu within ten seconds unless you click on it 1st, it also allows you to select windows...

---

### Post by HippoMan on 2005-12-01
[quote=vinnyjones]When i installed linux i didn't want to touch the boot record of either harddrive, so when i was asked the question of installing the GRUB bootloader to the primary harddrive, i clicked no. By doing so another menu allowing me to choose where i want to install the bootloader appeared, allowing me to install to the second hard drive and also the floppy drive. I chose floppy drive (/dev/fd0) which installed the GRUB bootloader to floppy...[/quote]
Aha!  That explains why I didn't see an option for this during the bootloader installation.  I didn't click **no** at that point like you did.

So, my problem is now solved, and I thank you very much ... all of you ... for your help.

---

