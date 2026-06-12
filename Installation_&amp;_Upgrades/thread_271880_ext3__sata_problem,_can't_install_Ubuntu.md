---
title: "ext3 / sata problem, can't install Ubuntu"
date: 2006-10-05
forum: Installation &amp; Upgrades
---

### Post by LazyTux on 2006-10-05
Hi guys, I just bought a new Sony VAIO S660/B that comes with 100GB SATA hard drive.  So far I have tried

1) Breezy
2) Dapper Alternate & Regular 
3) Edgy Beta Alternate & Regular

and none of them will install in this laptop.  I should also note I tried a Debian Sarge install and a Fedora Core 2 install.  

Dapper usualy always gets to 15% on the install process and completely locks.  Edgy just gets to 15% and just doesn't go any farther.  Breezy gets the farthest by installing the system and boot loader, but on reboot when it finishes I get the bug:

ata1: BUG: timeout without command

I feel like this is some issue having to do with a driver or kernel and the SATA controller used by Sony.  I'm not the only one thats had similar issues, although some people have successfully installed Debian based products on this particular model.  What seems to be consistent is that when it writes a ext3 partition, and it locks, and I reboot, it shows up as ext2.  I've also tried reiserfs, and it locks on it as well. 

I'm not an expert, so I'm reaching out for any help I can get. 

[http://www.eyesopen.org/projects/laptops/sony_s660b](http://www.eyesopen.org/projects/laptops/sony_s660b)

I've found this resource on a successful install, but I don't know how to apply it to a Ubuntu install, saying I need to install with the mod "ata_piix" enabled, and I'm not sure how to do this.  Some other threads suggested passing "noapic nolapic" or "nodma" into the F6 options command on install, but this has gotten me no where.  The Live CD works just fine, so I know this is just some issue about writing to the SATA drive.  

Are there any more suggestions, I"ll do anything to get Linux running on this machine.  

Thanks for any advice in advance.

---

### Post by eyesopen.org on 2006-10-12
Hi,


I am a member of eyesopen.org, to load this module you will need to open up a terminal or konsole and become root. Then type in this command to load the module:

*modprobe ata_piix*

That should do it for you.

Now type in:

*dmesg* 

and the last couple of lines should indicate that the system recognized your hard disk.

If you have any questions you can contact us at [email]webmaster@eyesopen.org[/email].

BTW we have more updates that will soon come up on the website regarding further features that we were able to get working. Best of luck and good choice on the laptop :)



Regards,


Phil

---

### Post by eyesopen.org on 2006-10-12
It would also be a good try to get our kernel configuration available from our website after your install the system and to compile the kernel with that configuration. So after installation if you cannot boot from hard disk:

you boot again from livecd 

load the module ata_piix.

try mounting the partition on your harddisk which has your installation. It should be sda.

Something like

mount /dev/sda1 /mnt

cd /mnt

make sure you have a root file system in there, If so:

cd /

chroot /mnt

This should put you in your installed system

This process should not give you errors.

cd /usr/src/

and then follow the instructions on our page to compile the kernel. Once done make sure to setup grub accordingly.

This should give you the kernel that is able to boot properly.

---

### Post by LazyTux on 2006-10-13
Thanks for the advice.  I tried with Edgy and Dapper to load ata_piix, but alas, they still cannot install.  I will try your advice on compiling the kernel using Breezy and post the results.

---

### Post by ZephyrXero on 2006-11-29
As an update to this thread...my friend who originally started this thread has tried numerous Linux distros, and none of them will work with his hard drive. I don't know if this is a problem with the kernel in general, or theres just a patch missing, but it's a no go so far. Interestingly enough, FreeBSD installed and worked just fine...

---

