---
title: "GRUB Errors 17 and 13 immediately after dual boot installation"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by Cicero480 on 2007-04-10
Hi. I just installed Ubuntu 6.10 and I'm having trouble booting from GRUB.

My system has Windows XP Media Center Edition on /dev/hda. Intending to create a dual-boot setup, I installed Ubuntu to /dev/hdb and, on the last page of setting up the installation, chose to install GRUB to "/dev/hdb" where the default was "(hd0)". (I also tried again, choosing "(hd1)" instead, with the same results.) The idea is to place hdb first in the system's boot order and boot to GRUB, while the system will still boot straight to Windows in the factory-installed fashion if hda is placed first in the boot order. I discussed the creation of this setup at [another thread]("http://ubuntuforums.org/showthread.php?t=380803").

The Ubuntu installation (from the Desktop live CD) was completed without any apparent problems and I am able to boot to hdb and get GRUB. However, GRUB appears as a text-only menu, which seems suspicious since I thought it was supposed to have a graphical menu by default. The menu consists of the following choices:
```

Ubuntu, kernel 2.6.17-10-generic
Ubuntu, kernel 2.6.17-10-generic (recovery mode)
Ubuntu, memtest86+
Other operating systems:
Windows NT/2000/XP
Windows XP Media Center Edition

```

When I choose any of the three Ubuntu options, I get "Error 17: Cannot mount selected partition". When I choose the first Windows option, I get "Error 13: Invalid or unsupported executable format". When I choose the second Windows option, the screen shows "Starting up..." but then hangs there forever.

I looked up the error messages on [the Hermanzone Super Grub Disk page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Grub_Errors"). It doesn't seem possible that Error 13 was caused by the Windows bootsector being corrupted, since I'm still able to boot to Windows (as planned) if hda is placed first in the boot order. As for Error 17, it seems odd that GRUB would be pointed at the wrong partition fresh off of Ubuntu setting itself up.

What can I do to troubleshoot this? Ideally, I'd like to make GRUB able to boot to both Ubuntu and Windows, though Ubuntu is my priority. I'd be happy to provide more information about GRUB's configuration if you tell me what to look for, or to answer any other questions. Thanks for reading this and for any help you can give!

---

### Post by Cicero480 on 2007-04-11
Okay, I researched the issue a bit more and decided to go poking around /boot/grub/menu.lst (from the Ubuntu installation on /dev/hdb). From the GParted interface on the Ubuntu live CD, I found that the boot partition (or at least the partition with the flag "boot") was /dev/hdb1 for Ubuntu and /dev/hda2 for Windows. Experimenting, I edited menu.lst to add some options to try to boot Ubuntu from (hd1,1) and Windows from (hd0,2). (I'm still not sure whether I was on the right track here -- I know that hda = hd0 and so on, but does (hd1,1) correspond to /dev/hdb1 or to /dev/hdb2?)

The (hd1,1) option returned Error 17 like before, and the (hd0,2) partition was said not to exist. This Error 17 confuses me -- it would be one thing if GRUB couldn't boot successfully from whichever Ubuntu partition, but why can't it mount any of them in the first place?

So, any advice on what to try next? I have a copy of Super Grub Disk here and I'm willing to try messing around with it, but I'm not sure where to start. I could also post copies of my /boot/grub/menu.lst and /etc/fstab files if that would help. Thanks!

---

### Post by dcahill on 2007-04-11
Hi!

I have exactly the same problem here when installing Ubuntu 7.04b on an external usb drive. Same error messages, screens etc. 

Did you ever sort it out?

---

### Post by confused57 on 2007-04-11
> **Cicero480 said:**
> Okay, I researched the issue a bit more and decided to go poking around /boot/grub/menu.lst (from the Ubuntu installation on /dev/hdb). From the GParted interface on the Ubuntu live CD, I found that the boot partition (or at least the partition with the flag "boot") was /dev/hdb1 for Ubuntu and /dev/hda2 for Windows. Experimenting, I edited menu.lst to add some options to try to boot Ubuntu from (hd1,1) and Windows from (hd0,2). (I'm still not sure whether I was on the right track here -- I know that hda = hd0 and so on, but does (hd1,1) correspond to /dev/hdb1 or to /dev/hdb2?)

The (hd1,1) option returned Error 17 like before, and the (hd0,2) partition was said not to exist. This Error 17 confuses me -- it would be one thing if GRUB couldn't boot successfully from whichever Ubuntu partition, but why can't it mount any of them in the first place?

So, any advice on what to try next? I have a copy of Super Grub Disk here and I'm willing to try messing around with it, but I'm not sure where to start. I could also post copies of my /boot/grub/menu.lst and /etc/fstab files if that would help. Thanks!

If you get a grub boot menu at startup, try highlighting your Ubuntu entry, press "e", then replace root (hd1,0) to root (hd0,0), then press "b" to boot...if this works, then post your /boot/grub/menu.lst & /etc/fstab files.

When you first installed Ubuntu, your bios boot order was hda then hdb, which grub recognized as (hd0) & (hd1), respectively.  You changed the boot order to boot hdb first, then it is recognized as (hd0) by grub, hda would then be (hd1) in grub.

---

### Post by Cicero480 on 2007-04-12
> **confused57 said:**
> When you first installed Ubuntu, your bios boot order was hda then hdb, which grub recognized as (hd0) & (hd1), respectively.  You changed the boot order to boot hdb first, then it is recognized as (hd0) by grub, hda would then be (hd1) in grub.

Aha! That *was* my boot order during installation -- I didn't change it until afterward. Thank you, I'll go try this ASAP.

---

### Post by Cicero480 on 2007-04-12
It worked. All of the error messages have stopped now and GRUB boots successfully into Ubuntu. The only problem is that I can't boot into Windows from GRUB -- when I choose "Windows XP Media Center Edition" from the menu, it gives the same behavior as before (probably for an independent reason, since that menu entry has been edited): it displays "Starting up..." and a blinking cursor, and then nothing happens.

Here are the contents of my edited /boot/grub/menu.lst file, starting with the "End Default Options" line (above which everything is commented out):
```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd1,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Windows XP Media Center Edition
root		(hd1,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda5
title		MS-DOS 5.x/6.x/Win3.1
root		(hd1,4)
savedefault
chainloader	+1

```

And here's /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=9bbc8f0e-3fc7-41cc-bb94-1fc39435786c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=4800b02a-fff1-493a-9268-e0c860a0aef3 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

So, to summarize my understanding of the solution, GRUB was set up incorrectly during installation because the boot order had /dev/hda first at that time, and when I changed the boot order (so as to boot to GRUB), the meanings of "hd0" and "hd1" had changed. What I could have done to avoid this problem was to put the disk that was going to receive GRUB first in the boot order *before* installing Ubuntu, and then selecting "(hd0)" at the end of the installation process. (dcahill, does this help?)

So, any tips on what I can do to keep GRUB from hanging up while trying to boot Windows XP? As I said above, according to GParted, the Windows partition with the flag "boot" is /dev/hda2, so I think the GRUB entry with "root (hd1,1)" should be the correct one, but it hangs at "Starting up..." when I select it.

---

### Post by confused57 on 2007-04-12
I didn't respond directly to dcahill's post, because I thought what I had suggested to you would also work for him.

You probably need to add mapping commands to your Window's entry:

```
title		Windows NT/2000/XP
root		(hd1,0)
savedefault
makeactive
map   (hd0) (hd1)
map   (hd1) (hd0)
chainloader	+1
```

Yes, you're correct in your assumption that setting your hdb drive to boot first in bios before installing Ubuntu would have made the drive (hd0), grub would have been installed to the mbr & an entry added to boot Windows.

See the 3rd link in my signature for how I have my system set up.

You'll also need to change the groot line in your menu.lst from (hd1,0) to (hd0,0):
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)
if you don't, a kernel update will change your root back to (hd1,0).

---

### Post by Cicero480 on 2007-04-12
> **confused57 said:**
> I didn't respond directly to dcahill's post, because I thought what I had suggested to you would also work for him.

You probably need to add mapping commands to your Window's entry:

```
title		Windows NT/2000/XP
root		(hd1,0)
savedefault
makeactive
map   (hd0) (hd1)
map   (hd1) (hd0)
chainloader	+1
```

Yes, you're correct in your assumption that setting your hdb drive to boot first in bios before installing Ubuntu would have made the drive (hd0), grub would have been installed to the mbr & an entry added to boot Windows.

See the 3rd link in my signature for how I have my system set up.

You'll also need to change the groot line in your menu.lst from (hd1,0) to (hd0,0):
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)
if you don't, a kernel update will change your root back to (hd1,0).

The mapping commands did the trick; both systems are now booting from GRUB and working fine! :D Thank you very much for the help, and for the tip about the groot line.

---

### Post by confused57 on 2007-04-12
Glad to help and that everything worked.

---

