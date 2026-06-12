---
title: "Is Ubuntu on an SD Card any good?"
date: 2012-07-16
forum: Installation &amp; Upgrades
---

### Post by LMDevlin on 2012-07-16
So I've been toying with the idea of running Ubuntu 12.04 from a 32GB SD card. Why, you ask? Well I own a Macbook Air, and don't really want to mess with the current drive and it's partitions (128GB SSD with Mac OS X Lion on it) because I'm not all that confident, but it has an SD card slot I'm not using right now.

I'm fully prepared to be told that I'm either an idiot and should just use the SD slot for additional file storage, or to suck it up and just dual boot Ubuntu off the SSD alongside Lion because it will be rapid, but is it worth installing on an SD card? Will it perform well, or am I just wasting my time?

Has anyone got experience for using it on an SD card?

Currently using 12.04 from Parallels, but it'd be nice to just boot straight into it.

---

### Post by robtygart on 2012-07-16
I have been wanting to do that too, it should work fine, the funnest part it trying and seeing how it turns out.

---

### Post by sudodus on 2012-07-16
You can put a live system (Ubuntu install CD/USB drive) on a USB pendrive or an SD card. Both will work :-)

But it will be slow partly because USB is slower than SATA (for internal drives) and partly because the flash hardware is slow, often slower than the USB connection. So it is a good idea to install a system with a small foot-print, for example Lubuntu with an ultra-light-weight desktop environment or Xubuntu with a light-weight desktop environment.

So in order to get a good system, get a fast card, as fast as possible (while still compatible with your card reader). But it is certainly also an alternative to get a fast USB pendrive, for example one capable of USB 3. I don't think you can boot from a USB 3 port, but a USB 3 pendrive has faster flash hardware, so it can read and write faster than a standard one also from a USB 2.0 port.

But you will not be satisfied with a standard live session, which cannot save private files or updates.

- If you are happy saving only files, you can create one data partition along with the system partition.

- Otherwise you can make a persistent live system with a casper-rw file or partition. Then you can save also updates (except kernel updates). But it is not as reliable as an installed system.
[[COLOR="Red"]_http://ubuntuforums.org/showpost.php?p=11546560&postcount=5_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11546560&postcount=5")

- So you can install [LX]Ubuntu to the SD card or USB pendrive. Disconnect your internal drive and install like you would have installed to an internal HDD (but in this case to the USB drive). This installation can be done in any PC, and as long as you don't install any proprietary driver (typically for graphics or wifi), it will be perfectly portable between computers (except those that really need proprietary drivers to run at all).
[[COLOR="red"]_http://ubuntuforums.org/showthread.php?t=1872303_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1872303")

---

### Post by LMDevlin on 2012-07-17
Thanks for the response guys.

I guess it would be best to install it on my SSD... I may try it at some point.

I guess in terms of installing it on an SD card, my plan was to get a Class 10 32GB SDHC Card- since I'm sure Class 10 is meant to be the fastest (if not the fastest), so maybe I'll just try it out.

I'd appreciate hearing any other stories if anyone has them.

---

### Post by robtygart on 2012-07-17
> **LMDevlin said:**
> Thanks for the response guys.

I guess it would be best to install it on my SSD... I may try it at some point.

I guess in terms of installing it on an SD card, my plan was to get a Class 10 32GB SDHC Card- since I'm sure Class 10 is meant to be the fastest (if not the fastest), so maybe I'll just try it out.

I'd appreciate hearing any other stories if anyone has them.

Well do it just to see if you can, buying an extra card is still worth it, 32GB card is always nice to have laying around for backing up your files.

---

### Post by Megaptera on 2012-07-17
I run Ubuntu 10.04 from an SD card occasionally (nostalgia?!) and don't notice a huge difference in speed. Faster than CDs/DVDs in my opinion - no stats to back that up.

---

### Post by TenPlus1 on 2012-07-17
I have a full install of Kubuntu 12.04 running from an SD card (class 10) and it seems to work pretty fast with a few minor tweaks (cache and apt in memory, no swap, noatime)...

---

### Post by sudodus on 2012-07-17
> **Megaptera said:**
> I run Ubuntu 10.04 from an SD card occasionally (nostalgia?!) and don't notice a huge difference in speed. Faster than CDs/DVDs in my opinion - no stats to back that up.

How are you running it - Live, Persistent Live, or 'Installed'?

I agree that USB flash is faster than CD, and SD is basically also USB flash.

---

### Post by spjackson on 2012-07-17
I think it would be definitely worth trying. My Raspberry Pi [http://www.raspberrypi.org/](http://www.raspberrypi.org/) boots from an SD card.

I have Xubuntu 12.04 on my Asus eeePC, and inspired by your suggestion I have installed Lubuntu on an SD card. It works fine. I didn't put a Live CD on it but rather installed to it. Definitely turn off swap.

---

### Post by Mr.Dee on 2012-07-17
VirtualBox? That's anothe way to try it without really messing anything up.  You'll need to install virtual box and that's it... Plus you'll be able to try out other distrobutions fairly easily.

---

### Post by sudodus on 2012-07-17
> **spjackson said:**
> I think it would be definitely worth trying. My Raspberry Pi [http://www.raspberrypi.org/](http://www.raspberrypi.org/) boots from an SD card.

I have Xubuntu 12.04 on my Asus eeePC, and inspired by your suggestion I have installed Lubuntu on an SD card. It works fine. I didn't put a Live CD on it but rather installed to it. Definitely turn off swap.
... or use swap on the internal drive, but then the SD card system will not be quite happy when ported to another computer unless you edit /etc/fstab. But a live or persistent live system will use whatever swap files that can be found.

---

### Post by efflandt on 2012-07-17
As long as you have enough RAM and will not do anything like ripping DVD's that might need a lot of /tmp, you can take a hint from fstab of a live/install iso on USB to use tmpfs (RAM) for /tmp and maybe go without swap or set swappiness very low to minimize writes.

Also using a non-journal file system like ext2 can minimize writes.

Something to note though is that a bootable SD slot is probably internally USB connected, so a really fast SD card may be wasted if the fastest it will work for that is USB 2.0 speed.  I tried 16 GB Class 10 SDHC in my tablet PC (Acer W500P), and it is no faster than any other SD would be in a USB card reader.  But its CPU is just a 1 GHz 2 core AMD C-50 w/2 GB RAM, so I don't ever expect it to be a speed demon.

---

### Post by Megaptera on 2012-07-18
> **sudodus said:**
> How are you running it - Live, Persistent Live, or 'Installed'? .. 

Just live with no persistence.

---

### Post by sudodus on 2012-07-18
> **Megaptera said:**
> Just live with no persistence.
Yes, this is the fastest way, because USB is fairly fast reading one big file compared to reading the same amount of data distributed to many small files (which will be the case in a regular install, and to some extent in a persistent live system) :-)

---

### Post by kurt18947 on 2012-07-18
> **sudodus said:**
> Yes, this is the fastest way, because USB is fairly fast reading one big file compared to reading the same amount of data distributed to many small files (which will be the case in a regular install, and to some extent in a persistent live system) :-)

Reading may be slow but writing seems to be REALLY slow.  I don't have a USB 3 flash drive yet but supposedly they are a good bit faster even when plugged into USB 2 ports.

---

### Post by sudodus on 2012-07-18
> **kurt18947 said:**
> Reading may be slow but writing seems to be REALLY slow.  I don't have a USB 3 flash drive yet but supposedly they are a good bit faster even when plugged into USB 2 ports.
Yes, it is, update & upgrade of a 'regular' install to USB is really slow. If a lot of updates, it is better to clone and update via an internal HDD ;-)

---

### Post by monkeychef on 2012-07-18
My computer configuration makes this type of install very helpful. How exactly would I go about installing Ubuntu like this, especially with specific things like installing using Ext2 instead of Ext4?

---

### Post by efflandt on 2012-07-18
> **monkeychef said:**
> My computer configuration makes this type of install very helpful. How exactly would I go about installing Ubuntu like this, especially with specific things like installing using Ext2 instead of Ext4?

Boot to a live system (Try Ubuntu) from the install CD or ISO on USB and then install.  During install chose "Other" for partitioning and set up types of partition(s) and format you want.  Make sure that you review the drop down list to put grub on mbr of the SD card or USB flash you are installing to.

After installing, instead of rebooting right away, chose Continue reviewing Ubuntu (something like that).  Then figure out where the new system is mounted in /media and edit its etc/fstab for tmpfs for /tmp or mount options (like noatime), before booting the new installation.

---

