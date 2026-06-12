---
title: "Three downloads - three installation failuers - why?!"
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by zozza on 2011-06-13
Hello, 

I am having real trouble installing Ubuntu.  I downloaded 10.04 LTS from ubuntu.com and checked the MD5 before burning to a CD.  I rebooted and the computer loaded from the CD but after a few minutes I got the following error:

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs dailed: Input/output error
Can not mount /dev/loop0/ (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

This appears to be a common error so I looked at some of the threads.  I then tried burning the same file on to a CD-RW whereas the first CD was a CD-R.  Same error message.

I then downloaded 11.04 and checked the MD5 and burned it to a CD-R.  Same error message.

In each case I tried on two computers.  

Why is this happening?  How can I actually install Ubuntu?  Is there some well-known issue with downloads from ubuntu.com?  What should I do?  Three downloads (all with correct MD5 hashes) but none will load.  

Thanks!

---

### Post by coffeecat on 2011-06-13
If the md5sums check out then the ISOs are OK. Are you burning at a low speed? It's recommended to burn at low speed to lessen the risk of write errors. I usually choose x4.

The other thing you need to do is a disc integrity check. As soon as the CD starts booting, you'll see a purple screen with two small icons at the bottom. Tap the spacebar, select your language and you'll see the old-style text menu. A disc integrity check is about 3rd on the list. Try that.

---

