---
title: "Scary messages in a successful Grub2 restore"
date: 2010-12-12
forum: Installation &amp; Upgrades
---

### Post by rpaskudniak on 2010-12-12
Greetings.

Last week, something I did blew away my Windows boot partition and, until Dell shipped me the installation disk (why didn't they send it with the machine?  That's another issue.) I was forced to work from the Ubuntu live disk.  After using
```
bootrec.exe /fixboot
bootrec.exe /fixmbr
```
to get it back, of course, I had to restore the grub loader, using talsemgeest's instruction in [article 1014708]("http://ubuntuforums.org/showthread.php?t=1014708").

It worked, as it has in the past, but it always issues a scary message:
> ubuntu@ubuntu:~$ sudo mkdir /media/sda5
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /media/sda5
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda5 /dev/sda
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.Can anyone tell me what this means?  What is Flexnet antyway?  What disaster is it worried about and should I worry as well? (My lifelong companion, Alfred E. Neuman, is concerned as well. :-o  )

Thanks for some enlightenment here.

---

### Post by ryadav on 2010-12-12
try to reinstall grub without specifying --root-directory
boot into rescue more using LiveCD

mount /dev/sda5 to its intended location. 
if /dev/sda5 is your root /
then do "sudo mount /dev/sda5 /"

to install grub, follow the instructions here
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

if you have /boot on a separate partition make sure it's mounted to /boot before you reinstall grub

---

### Post by Quackers on 2010-12-12
I thought Flexnet writing to the boot sector had been fixed now! Maybe not.

---

### Post by oldfred on 2010-12-12
It is one of those problems that  grub2 had to work around. The boot area is for booting not DRM.

Adobe Photoshop, CAD/CAM, Rosetta Stone, Matlab others 
Sector 32 or similar is already in use by FlexNet
[http://www.amazon.com/Adobe-Photoshop-Extended-CS4-VERSION/product-reviews/B001EUDGO2](http://www.amazon.com/Adobe-Photoshop-Extended-CS4-VERSION/product-reviews/B001EUDGO2)
The problem turned out to be Adobe's digital rights management software [DRM]. Do your own search for "FlexNet," formerly known as "SafeCast." What I have read is that FlexNet is a viral rootkit that replicates in multiple locations whenever a CS3 or CS4 product is installed, including trial versions.

 see google search on others with same issue: flexnet site:ubuntuforums.org
One from above search:
[http://ubuntuforums.org/showthread.php?t=1605076&page=3](http://ubuntuforums.org/showthread.php?t=1605076&page=3)

---

### Post by Quackers on 2010-12-12
Very illuminating oldfred, thanks.

---

