---
title: "/Dev/sbdl Eh?"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by Squee351 on 2005-10-14
Okay, I toss the CD in, finish phase one of the installation, it's all dandy. Where it gets iffy is where it's suppost to finish the installation (reboot without CD). I get this error
> 
...
boot
uncompressing linux... ok, booting the Kernel

Alert! /dev/sdbl does not exist. Dropping it to a shell!


BusyBox V1.00-pre10 (Debian 20040623-1ubuntu22)Built-in shell(ash)
Enter 'help' for a list of commands.

/bin/sh: can't access tty; job control turned off
# [429468.923000] sdb: assuming drive cache: write through
[4294686.964000] sdb: assuming drive cache: write through
...


I've been searching the forums and google but with no luck. Maybe you guys could help me along. I've heard great things about Ubuntu :).

Thanks!

~Tom

edit: If you guys/girls need more information, just ask. No need to flame me or anything. Thanks again.

editx2: added more information on the error I get.

---

### Post by Squee351 on 2005-10-15
Okay, played around with it - reinstalled twice, and tried different configs. Still doesn't want to work. Grr.

I try booting Ubuntu using GRUB, I get the error above. If I put in the CD which has the install poo on it, I get this guy right here -

> 
Booting command-list
root (hd 1,0)

Filesystem type is ext2fs, partition type 0x82
Kernel /vmlinuz-2.6.12-9-386 root= /dev/mapper/Ubuntu-root ro quite splash
[Linux-vzImage.setup=ox1c00, size=0x123616]
intird /initrd.img-...
...
boot
uncompressing Linux... Ok, booting the kernel.
loading, please wait
/dev/cdrom1= open failed= no medium found
unable to find volume group "ubuntu"

Alert! /dev/mapper/Ubuntu-root does not exist. Dropping it to a shell!

<<then it freezes here and must reboot by holding the on button>>


I am tired as butt and will try to help myself in the morning. Sorry for double posting but I must get this working!

Thanks and whatnot

<3 Tom

---

### Post by dbott67 on 2005-10-15
What kind of hardware are you installing on?  PC or laptop, CPU, RAM, type of hard drive (SCSI or IDE), CD/DVD, any USB devices (flash USB or USB CDROM), etc.

It's also possible that your CD burn was bad.  The very first Ubuntu ISO I burned gave me all sorts of problems during installation.

I re-burned the ISO at a much lower rate (8x instead of 48x) and re-installed again.  After that, installation went without a hitch.

-Dave

---

### Post by Squee351 on 2005-10-15
My computer specs -
Desktop
Intel Pentium 4 (3.31 GHz)
2 gigs of ram

CD/DVD Burner (internal)
iPod
HP 1350 All-In-One printer


Installing it on a Maxtor 80 gig external hard drive via USB and I do believe it is IDE.
[http://www.maxtor.com/portal/site/Maxtor/menuitem.ba88f6d7cf664718376049b291346068/?channelpath=/en_us/Products/External%20Storage/Personal%20Storage%20Family/Personal%20Storage%203100&productview=Overview]("http://www.maxtor.com/portal/site/Maxtor/menuitem.ba88f6d7cf664718376049b291346068/?channelpath=/en_us/Products/External%20Storage/Personal%20Storage%20Family/Personal%20Storage%203100&productview=Overview")

I'm burning a new copy of the image as I type.
Thanks for your help!

~Tom

edit: I reburned the ISO but it still pooped out around the BusyBox part. I'll try it again. Hopefully it'll work.

---

### Post by dbott67 on 2005-10-16
I think it may be related to trying to install onto the external USB hard drive.

This territory is pretty foreign to me, so I don't really have any good info for you --- just a couple of places to start:

- check your BIOS settings for any USB-related settings, such as being able to boot from it, etc.
- installing to external USB drive would be a similar procedure to installing to USB thumb drive; you might want to search for "installing linux on USB drive", as the procedure is somewhat different --- not every computer supports booting from USB.

-Dave

---

### Post by Squee351 on 2005-10-16
Aha! Thank you! That's why it wasn't working. 

I googled it and found many long lists of commands and whatnot to get it to work, but instead of doing that - I'm going to have Ununtu share a harddrive with Windows and put all my songs (majority of my windows hard drive) on the external one. The old switch-a-roo. 

Thanks for all your help, Dave.

---

