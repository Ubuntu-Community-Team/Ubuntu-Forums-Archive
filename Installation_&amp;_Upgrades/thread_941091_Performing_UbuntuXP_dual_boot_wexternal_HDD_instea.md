---
title: "Performing Ubuntu/XP dual boot w/external HDD instead of partitioning internal"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by peetnote on 2008-10-07
Hi there,

I'm currently running Ubuntu, but I need XP for some recording/production needs. I am interested in performing a dual boot with a copy of XP I have. I have a spare external hard drive (160 gig) laying around, so instead of partitioning my internal I would like to designate my internal for Ubuntu and my external for XP. How would I go about doing this? Should I just boot it to my external, or will that wipe out my saved Ubuntu settings?

I apologize if this should be posted in the extreme noob section. :)

peet

---

### Post by peetnote on 2008-10-07
Sorry... accidentally tagged as kubuntu. Meant to do ubuntu. my bad.

---

### Post by arshomette on 2008-10-07
This is an excellent website I used to install Ubuntu on my external: [http://www.pendrivelinux.com/category/install-to-usb-hard-drive/]("http://www.pendrivelinux.com/category/install-to-usb-hard-drive/")

However, you should precheck if you can boot from USB (that is what I am assuming that you will use to interface with the HD).  If you insert the USB drive prior to startup and open the BIOS config, you should see a boot-up priority list.  USB should be above the internal HDD, unless you still want to use XP as the main system... Either way, you can still access either OS using a one-time boot menu that most motherboards now have.

That said, you should note that XP does not support Ext2 or Ext3 (the main Ubuntu file systems).  I can't help you (actually, I am looking for help here) with which file system to use for access to both XP and Ubuntu.  In my research, I found Fat32 (and worse) to work with both 100%, but over 30GB, it is incredibly inefficient.  NTFS is (somewhat, iirc) supported in Ubuntu 8.10 (its native to Microsoft), but I don't know the status of that (or whether someone can even install Ubuntu on NTFS).

Right now, I have partitioned on my external HD 20GB Ext3 for Ubuntu (which has failed for me...), 2GB for swap, and the rest (of an 80GB drive) in Fat32, but I might change to NTFS if Ubuntu support is better.  Can someone help me (us) here?

Hope this helps,
Andrew

---

