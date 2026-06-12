---
title: "copying cd image to usb stick?"
date: 2009-12-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by reub2000 on 2009-12-18
I'm trying to copy the KNE image to a usb stick with the following command:
```
sudo dd if=lucid-netbook-i386.iso of=/dev/sdc bs=1M
```

This appears to copy all of the files to the USB stick, however it won't boot. The same thing works with the fedora cd image, so I don't see why it wouldn't work with KNE.

---

### Post by ranch hand on 2009-12-18
What in flinderation is KNE?

---

### Post by reub2000 on 2009-12-18
> **ranch hand said:**
> What in flinderation is KNE?Kubuntu Netbook Edition

---

### Post by ranch hand on 2009-12-18
AH, we live and learn.

Can't help you with that, I can say that I have never seen a netbook of any kind, not even in a store.

I think that probably disqualifies me as an expert.

Thanks for the new knowledge.

---

### Post by ronacc on 2009-12-18
you can use either startup disk creator from the system>admin menu ( in gnome) or unetbootin  , if unetbootin is not installed it is in the repos , I'm not in KDE right now so I can't tell you where startup disk creator or it's KDE equivalent is , probably Kmenu>system

---

### Post by bennachie on 2009-12-18
Your method would have worked just fine for Fedora, Mandriva or openSUSE. I'm not sure why Ubuntu hasn't gone down the Hybrid ISO route. I've found that USB disk creator on Ubuntu can become flaky if you try to use all the space remaining after the liveCD and boot files have been copied over as a persistent file to hold documents and settings. The process works OK if you leave a small amount of buffer space at the end. Unetbootin is fine, but doesn't offer the option of persistence.

---

### Post by reub2000 on 2009-12-18
Well I burned the image to a dvd and tried booting it up on my desktop and was greeted with a pitch black desktop. Guess it doesn't work anyways.

---

### Post by sgosnell on 2009-12-18
It's a CD image, not a DVD image.  You can burn it to a CD, but not a DVD.  If you have Ubuntu on a computer, System/Administration/Create USB Startup Disk will do it, if you don't, then unetbootin should.  It can be flaky, though, and may take several tries to get a good burn.

---

### Post by reub2000 on 2009-12-19
> **sgosnell said:**
> It's a CD image, not a DVD image.  You can burn it to a CD, but not a DVD.  If you have Ubuntu on a computer, System/Administration/Create USB Startup Disk will do it, if you don't, then unetbootin should.  It can be flaky, though, and may take several tries to get a good burn.
[http://cdimage.ubuntu.com/kubuntu-netbook/daily-live/20091218/](http://cdimage.ubuntu.com/kubuntu-netbook/daily-live/20091218/)

It's a 829MB image, so it won't fit on a CD.

---

### Post by sgosnell on 2009-12-19
I knew there was another good reason to avoid Kubuntu.

---

### Post by jocko on 2009-12-19
> **sgosnell said:**
> It's a CD image, not a DVD image.  You can burn it to a CD, but not a DVD.  If you have Ubuntu on a computer, System/Administration/Create USB Startup Disk will do it, if you don't, then unetbootin should.  It can be flaky, though, and may take several tries to get a good burn.
It doesn't matter if it's a cd or dvd image, a cd image can be burnt to a dvd.
But, since the image in question is made for netbooks (which don't have cd or dvd drives), it is irrelevant if it is a cd or dvd image (or an oversized cd image as in this case). It needs to be put on a usb device, as that's the only option to boot a netbook.

---

### Post by bennachie on 2009-12-19
I'm not (yet - I hope for better days ahead) a great fan of Kubuntu, and think that openSUSE has done the KDE thing much better. However, my general impression is that "netbook editions" in general are less than convincing, and often tend to add to, rather than diminish, bloat. 

For the record, plain vanilla Ubuntu 9.10 runs very well indeed on my eeePC 701 4G, as does Mint 8, and later model netbooks (I also have an eeePC 1000H) will run any current Linux distro easily and efficiently.

---

### Post by reub2000 on 2009-12-19
> **bennachie said:**
> I'm not (yet - I hope for better days ahead) a great fan of Kubuntu, and think that openSUSE has done the KDE thing much better. However, my general impression is that "netbook editions" in general are less than convincing, and often tend to add to, rather than diminish, bloat. 

For the record, plain vanilla Ubuntu 9.10 runs very well indeed on my eeePC 701 4G, as does Mint 8, and later model netbooks (I also have an eeePC 1000H) will run any current Linux distro easily and efficiently.My laptop runs Kubuntu 9.10, which is runs like a charm.

Now my netbook currently has moblin, and I was curious to see where plasma netbook has gone since the karmic preview image.

---

### Post by VMC on 2009-12-19
> **bennachie said:**
> I'm not (yet - I hope for better days ahead) a great fan of Kubuntu, and think that openSUSE has done the KDE thing much better...

I think the same way except openSUSE has a couple of problems that there bug people don't address. OpenOffice fails on trying to create new labels. Also I can't print to my HP printer. At lease Kubuntu works.

---

### Post by sgosnell on 2009-12-19
No, it's not the only option to boot a netbook.  Lots of people have external USB CD/DVD drives, and it's easy enough to boot from one.  Using an external CD/DVD drive is actually easier than a USB flash drive, at least for getting the .iso burned.

---

### Post by garvinrick4 on 2009-12-21
On the bottom of page in fdisk -l you will see the flash drive with full persistence.


This is a working USB Flash drive with that operates with full Ubuntu O.S.
Has persistence for all 13 gig partition with boot in seperate partition done
with gparted manually. It works I am using it now on Laptop. 

I have finally got a 16 gig Flash drive to work as independent system. A lot of trial and error.
Used Live CD. 9.10 64 bit and the 16 gig flash drive.
Booted Live CD and selected install.
When it got to partitioning selected USB device of course.
1st partition was 500 meg ext3  /boot as mounting point
2nd partition was 13.5 gig ext3 / as mounting point
3rd partition was 2 gig Swap

IN THE 8TH PAGE YOU HAVE TO CLICK ADVANCED TAB AND SELECT BOOT AS THE SAME
AS YOUR 1ST PARTITION  THAT YOU SELECTED AS /BOOT AS MOUNTING POINT.

 Then add your repositories such as partners, medibuntu, backports, all the same ones as your normal install. You have over 12 gig left to work with so use what you want. Compiz works fine, the only thing in Karmic I have not gotten to work is sound and every install of 9.10 on my HP G71-34OUS has
had sound issues, I will get it. WIFI came right in. Has been a normal install.

Grub menu.  When you upgrade it installs itself onto your systems grub with no partition
number such as sba1 or any device. This works well it just installs a grub selection while
plugged in to USB port with recovery selection.

                                                        here is fdisk.   I am running flash drive now.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       26132   209696248    7  HPFS/NTFS
/dev/sda3           26133       37330    89947935    5  Extended
/dev/sda4           37331       38914    12709888    7  HPFS/NTFS
/dev/sda5           32107       37111    40202631   83  Linux
/dev/sda6           37112       37330     1759086   82  Linux swap / Solaris
/dev/sda7           26133       31856    45977967   83  Linux
/dev/sda8           31857       32106     2008093+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 16.7 GB, 16687038464 bytes
64 heads, 32 sectors/track, 15914 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x0008849e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         954      976880   83  Linux
/dev/sdb2            3831       15914    12374016   83  Linux
/dev/sdb3             956        3830     2944000   82  Linux swap / Solaris
                                                                                               __________________
                Remember hence where you come and pass it down.

---

### Post by phillw on 2009-12-21
> **VMC said:**
> I think the same way except openSUSE has a couple of problems that there bug people don't address. OpenOffice fails on trying to create new labels. Also I can't print to my HP printer. At lease Kubuntu works.

Would not that be a bug to OO ?

My usb boot with 9.10 on is happy little bunny when it boots, even got persitance on the 4GB dongle. For the price of a 4GB memory stick & 9.10 pre-installed - I reckon it's a real good price  -->>  [http://shop.canonical.com/product_info.php?products_id=577](http://shop.canonical.com/product_info.php?products_id=577)

It's cute, as for HP printers - if you go digging, they do have linux drivers available

[http://www.hp.com/wwsolutions/linux/products/printing_imaging/index.html](http://www.hp.com/wwsolutions/linux/products/printing_imaging/index.html)

Is a good place to start, HP are amongst the better manufacturers for such support.

Regards,

Phill.

---

### Post by VMC on 2009-12-21
> **phillw said:**
> Would not that be a bug to OO ?

Phil, 
 That's what I orignally thought so I created a bug report at OO.org and was told after much ado that its openSUSE distro probelem. The exact same OO works in Kubuntu without a hitch.

---

