---
title: "Two distros, one linux box. Help!"
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by linuxmick on 2006-12-11
Hi folks,

Here's my problem. I have a linux box, with two hd's. Ubuntu on hd1 and Pclinuxos on hd2.

Both distros are already installed to each hd. I recently installed both hd's in the one box. I want to know how do I tell grub on hd1 (ubuntu) that there is another linux distro on hd2?

I have read some of the posts on the installation forum, and I feel I am very close. I was able to edit menu.lst to do simple changes like splash images etc...but trying to get grub to see my other hd2 is proving more comlex. I also did a *sudo fdisk -lu* to determine where everything is on both drives. If that output is needed I can include it later.
 
My main problem is trying to see the data on hd2. When in Ubuntu, (from desktop gui)I try to click the hd2 drive but get an error about not being able to mount the drive. 

I tried to add the distro to the menu.lst in grub, but I do not have the exact details right. Kernal number, exact location etc...so it wouldn't load. :confused: 

So how do I access the hd2 with Pclinuxos on it, and then what do I have to do in grub to make both available?
I'm pretty sure I am not the first user to be here, so if anyone could shed some light on what to do, I'd be very grateful.
Thank you in advance.:-D 
Mick

---

### Post by confused57 on 2006-12-11
Here's my PCLinuxOS menu.lst:

title linux
kernel (hd0,2)/boot/vmlinuz root=/dev/hda3 splash=silent vga=788
initrd (hd0,2)/boot/initrd.img

title linux-nonfb
kernel (hd0,2)/boot/vmlinuz root=/dev/hda3 
initrd (hd0,2)/boot/initrd.img

title failsafe
kernel (hd0,2)/boot/vmlinuz root=/dev/hda3 failsafe
initrd (hd0,2)/boot/initrd.img

title 261627tex1lve
kernel (hd0,2)/boot/vmlinuz-2.6.16.27.tex1.lve root=/dev/hda3 splash=silent vga=788
initrd (hd0,2)/boot/initrd-2.6.16.27.tex1.lve.img

title 261714tex1
kernel (hd0,2)/boot/vmlinuz-2.6.17.14.tex1 root=/dev/hda3 splash=silent vga=788
initrd (hd0,2)/boot/initrd-2.6.17.14.tex1.img

Maybe they can help you...I updated the kernel, which I had to manually add as the last entry...I think the live cd kernel is the 2.6.16.27.tex1.lve

You'll need to adjust it to your system, depending on where your PCLinux is located according to fdisk -lu, e.g. for an IDE disk...hdb1, root (hd1,0)

If you're interested in mounting your linux partition & getting your kernel boot entries:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

You can boot your PCLinux by chainloading(installing grub to the root partition), if the above doesn't work.

---

### Post by linuxmick on 2006-12-12
Thank you so much for responding, Confused57

I used your menu.lst entry for PCLOS, (with my system details of course) and I'll be damned it booted up!!!
But then I got an error about the file system, it had been unmounted uncleanly. 
I had it formatted as reiserfs and it said the superblock was corrupted. If I wanted to fix the errors I had to run the 'utility' with '--rebuild-sb'.

I now have two questions. If I want to keep this install and try fix it, what utility is it talking about? 

This is an older version of PCLOS (0.92) and I could install a newer version to this hd, but if I do, what do I do  when it asks where to load the boot loader? Will it see Ubuntu (w/Grub) on hd1? 

I know this would normally frustrate most new users, but I am just delighted that I got it to boot!!! Thanks again.
Mick

---

### Post by confused57 on 2006-12-12
Sounds like it'd be better just to reinstall a newer version of PCLinuxOS to your 2nd drive...by the way, Linux would designate your Ubuntu drive as hd0 and your PCLinux drive as hd1.  Are both the drives IDE?

You could install PCLinux to your 2nd drive and allow grub to be installed to your Ubuntu hd0 mbr...it may actually add the entry to boot Ubuntu...if it doesn't, it's easy to reinstall the Ubuntu grub to the mbr, using the desktop live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

If the PCLinux grub doesn't add an entry to boot Ubuntu, boot into PCLinux...write down the exact entries to boot PCLinux...reboot with the live cd, restore Ubuntu grub, then add the PCLinux to Ubuntu's /boot/grub/menu.lst.

What I find easier is to chainload different Linux OS...during the installation of PCLinux, opt to install grub to the root partition(probably /dev/hdb1, if you're using IDE drives)...then add an entry similar to this to your Ubuntu grub to boot PCLinuxOS:
```
title   PCLinux OS on hdb1
rootnoverify (hd1,0)
chainloader +1
```

There's some excellent information about grub on this site:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by linuxmick on 2006-12-12
Here's the final outcome!

First up, thank you once again confused57 for your right on target advice!
I downloaded and installed the latest pclos, and as you advised I place the boot loader on the root partition. I then inserted the chainloader code you quoted and edited it with my system details.
At first it didn't boot, the text from the stanza just sat there on the screen....nothing. So I had obviously pointed it to the wrong location. That grub numbering system can be a little confusing at first, to say the least. (hd1,4) Turned out to be the magic target. 

By the way, thanks also for the links to all the great Grub info. They were very helpful.

Both hd's are IDE, so you weren't far off on the numbering designation. Finally I placed the pclos where I wanted it in the Grub list and all is now working well! :D 

Once again, many thanks and I hope I can return the favor some day. Maybe to some other multi-distroed new user!
Merry Xmas.
Mick

---

### Post by rigdzinthar on 2006-12-12
have you thought about using VMware instead?:-k

---

### Post by linuxmick on 2006-12-13
Now that IS a good idea too! VMware.
I have not looked into virtual machines yet, but  most of what I read about it states that you must have plenty of memory available. This is an older AMD Athlon Thunderbird 1 ghz with just 512 mb max.

But thank you for the suggestion, I will keep it in mind for the next distro try-out.
Mick

---

