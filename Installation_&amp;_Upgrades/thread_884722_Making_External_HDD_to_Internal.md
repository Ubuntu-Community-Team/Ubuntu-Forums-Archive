---
title: "Making External HDD to Internal"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by n1nj4r on 2008-08-09
Hey guys, 
I'm new to Linux and I've been having problems.

I recently built my new desktop(mind you its been awhile since i built a desktop).  I was trying to install Windows and Linux, and I kept getting a "disk boot failure" error.  So I decied that I was having problems with the CDROM.  

I then looked into using the Install from USB to install linux.  I was having alot of problems with that too.  I would finally get to install Ubuntu, but no luck with it saying it needs to get files from a CDROM.  And No luck changing the USB to act like a Cdrom.

I had an extra Ext. HDD casing around, I put the internal HDD from my desktop on the ext. hdd casing and plugged it into my Laptop with a working cdrom.  I installed Ubuntu on the ext hdd, with no problems.  

I tested and tested, finally got the ext hdd into the desktop to boot from ubuntu.  But I'm pretty sure I have to change the files to make it not act like a laptop.  I tried the command, sudo /boot/grub/menu.lst to change the boot, but It kept saying "Command Not Found"  

If i Just try and open the Menu.lst, I can't save it.. saying I don't have the permission.

Any Ideas on what I can do? and what else do I have to change?

Thank you so much,

---

### Post by SkonesMickLoud on 2008-08-09
> **n1nj4r said:**
> sudo /boot/grub/menu.lst to change the boot, but It kept saying "Command Not Found"

You're close, but your command lacks a command for what editor you want to use.

The default GNOME editor is "gedit", so you'd run:

```
sudo gedit /boot/grub/menu.lst
```

For KDE, I believe that it's "kate", which would be:

```
sudo kate /boot/grub/menu.lst
```

Out of curiosity, what are you trying to change?

---

### Post by n1nj4r on 2008-08-09
Ahh thank you.

And Well, I'm just trying to make it so it will only boot Ubuntu.

And I'm not sure if theres any other files I have to change, since I installed Ubuntu from my laptop.. wouldn't it have my laptop settings?

And how would I go about changing the MBR on my laptop? Without the ext. HDD attached, I get the Error 21.  Could I just use the Super Grub disk to fix that?

Thanks!

---

### Post by SkonesMickLoud on 2008-08-09
> **n1nj4r said:**
> Ahh thank you.

And Well, I'm just trying to make it so it will only boot Ubuntu.

And I'm not sure if theres any other files I have to change, since I installed Ubuntu from my laptop.. wouldn't it have my laptop settings?

And how would I go about changing the MBR on my laptop? Without the ext. HDD attached, I get the Error 21.  Could I just use the Super Grub disk to fix that?

Thanks!

Grub error 21 can be a toughy:

```
21 : "Unknown boot failure"

This error is returned if the boot attempt did not succeed for reasons which are unknown.
```

Can you post the output of:

```
sudo fdisk -l
```

---

### Post by n1nj4r on 2008-08-09
So I could do the Sudo fdisk -1 after I get into linux and do alt f2, currect?

and should I be worried about changing any other file?

---

### Post by Pumalite on 2008-08-09
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

---

### Post by Herman on 2008-08-09
The way I understand this story is, you built a new desktop computer and you wanted to install Ubuntu in it but it seemed to have problems in the CD/DVD drive (possibly).

You removed the hard disk and placed it in an USB external hard drive case, plugged it into your laptop, (with a known good CD/DVD drive, and installed Ubuntu in the external USB hard disk.

Now your laptop is giving you GRUB Error 21 when you try to boot it without the USB external hard drive. ( 21 : Selected disk does not exist).
Your USB external hard drive is now back in your dektop computer as an internal hard drive, with Ubuntu in it, but it doesn't boot.
====================
If I have interpreted your story accurately so far, I would say that you installed GRUB to MBR in your laptop's hard drive instead of in your external USB drive, which is a very common mistake when installing Ubuntu in a USB.

It's easy to fix.
Just use Super Grub Disk in your laptop to restore the MBR with whatever boot loader you had in there before. If your laptop had Ubuntu in it, then you need to re-install GRUB. If your laptop had Windows in it, then you need to re-install the Windows boot loader to MBR. If it's Windows XP you can run FIXMBR from your Windows CD if you prefer. 
Here is a whole web page full of ways to restore your Windows boot, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

In your Desktop, you just need to install GRUB to MBR. You should be able to do that with your Ubuntu 'Desktop' Live/Install CD ([Re-install GRUB]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")), or with Super Grub Disk, ([ Let's recover the Linux boot]("http://supergrub.forjamari.linex.org/?section=documentation#windows_reinstalled_a1")).

---

### Post by |Eric| on 2008-08-09
you can also trasfer MBR with the dd command :P 

~ dd if=(source) of=(dest [this CAN be a file!] ) bs=512 count =1 
what is neat with this tool is you can keep the windows XP loader & have linux boot from it :-) 

this would look like this 
dd if=/dev/sda1 of=/media/win_part/bootlinux.bin bs=512 count =1 


you can add to boot.ini in your windows part 
C:\bootlinux.bin="Linux Ubuntu Real Hardcore System 7.10"

than simply move your .bin file there :P

&-voila!

---

### Post by n1nj4r on 2008-08-09
The Dekstop boots fine, just has the Grub list from the laptop.  Has the two options, Ubuntu or XP.  I just change the boot to Hd0,0 for Unbuntu and it runs fine.

---

