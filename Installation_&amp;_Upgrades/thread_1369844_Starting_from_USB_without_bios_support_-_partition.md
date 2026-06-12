---
title: "Starting from USB without bios support - partitioned USB drive and boot CD."
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by squashpup on 2010-01-01
OK.

I've done a few USB startup disks before.  

When I do, I usually like to partition the drive so I have a place to put documents so I don't take up my casper-rw space.  Plus, it would make it possible to share documents between Windows and Ubuntu. 

Problem is, when I've put Ubuntu on the first partition, Windows sees it, but does NOT see the second data partition.  

So, when I got a 32gb Sandisk Cruzer for Christmas, I decided to put Ubuntu on the SECOND partition (6GB) and left the first one as storage.

Works perfectly...boots when the BIOS is set correctly, but in Windows you can still access the data drive. 

But, in solving one problem, I've caused another.  

I made a boot CD using these instructions: [http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-9-10/](http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-9-10/)

Which work fine if you have Ubuntu installed on the first partition, but when you try to boot from the second, displays "File not found".

Does anyone have a way to make a boot CD that will find Ubuntu on the SECOND partition of the USB drive?  Maybe a quick modification to the above directions?  Any help at all?

Thanks!

---

### Post by phillw on 2010-01-01
Hi,

yeah... from memory, pendivelinux have a little howto, for booting from a cd, then handing control over to a usb device .. it's over here --> [http://www.pendrivelinux.com/category/usb-boot-cds/](http://www.pendrivelinux.com/category/usb-boot-cds/)   

That should get you up & running, although I've never used it myself - I've found their stuff to be very good & have never had any come back and say their instructions are not clear or don't work. They also have a multi operating system version, as well, on that site.

There is, of course, another way --> [http://shop.canonical.com/product_info.php?products_id=577](http://shop.canonical.com/product_info.php?products_id=577)    I love mine :P

Regards,

Phill.

---

### Post by squashpup on 2010-01-01
I think I was unclear as to what I wanted. 

I made the boot CD so that I could boot on a computer that would not boot from USB.  In other words, on a computer where the BIOS doesn't support USB boot.

The boot CD works great, but only if Ubuntu is on the first partition.  It doesn't seem to work if it is on the second, for whatever reason.

Any ideas?

---

### Post by squashpup on 2010-01-01
Grub is seeing my pen drive as 

(hd0,0) (blank storage partition)
(hd0,1) (Ubuntu partition)

So, in light of this, how do I point GRUB to the second partition?

---

### Post by squashpup on 2010-01-01
I even thought of making symbolic links of everything required for booting and putting them in partition 1, but I don't think that would work, would it?

---

### Post by garvinrick4 on 2010-01-01
If it is a Live CD it should show the other OS's under places?  Does not matter what partition.   You can partition the flash just like a drive in gparted sb1a as /boot, sba2 as /root and so on.
In page 8 of gparted make sure you click advanced and choose boot as the same sb1a for instance. Change sba to whatever your media device is in gparted. If you have a large amount
of RAM do not worry about a swap. I have done this with 16 gig with full persistence.
  If you have linux already running grub2 it will put itself in mbr when sudo update-grub.
If you have just Windows it will give you a grub2.
 So if you want to carry it and use someone else's machine if it updates grub will install grub2 and use it instead of Windows bcd but not over write it. That is the good thing, you get rid of grub2 and machine will still see bcd. Will most likely freak owner of machine out.

Everyone keeps CD as first boot and USB as second boot and Hard Drive as third. Must keep CD as #1 of obvious reason, if machine becomes unbootable need to load CD to boot and repair. If you leave USB as second at times if you have Flash in USB port at boot it will try to read USB for boot and when it does not boot hangs. So if you do not have anything that boots off of USB keep it as third in order.

Your fdisk -l will show Flash drive as sba (32 gig)
                                                        sba1 (whatever you give it for boot) 500 meg most.
                                                         sba2 (your file system 31 gig)
                                                         sba3 ( not there or if you use swap it will be swap 2 
                                                                    gig or so)

---

### Post by phillw on 2010-01-01
Hi,

from reading that howto on pendrivelinux, it looks like it is grub legacy and not Grub2 ?

Sadly, my Grub skills are at the level of being able to read what drs305 posts in his Wiki's and HowTo's. 

I haven't seen drs305 on for a couple of days (must be taking a break) - He'd certainly be the one to help you on this one.

Changing stuff with grub legacy (which I am assuming it is using, as it is using menu.lst) is covered here --> [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

I * think* you want **4** ?

In any case, that HowTo covers the various options that Grub Legacy has.

Sorry I can't be of more help - I'm getting my head around Grub2 !!!
(Grub2 is over here, btw --> [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)   It is Grub2 central !!)

Regards,

Phill.

---

