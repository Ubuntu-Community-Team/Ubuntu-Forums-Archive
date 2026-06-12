---
title: "Live CD to usb?"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by Strategist01 on 2010-12-04
Hi guys

So I have a 10.04.1 Live CD iso sitting on my HDD. I want to install it to my 4GB flash, and have at least 1GB of persistence, as I want it to be a sorta quick and handy tool to get the job done, or I specifically need something from there.

Now, I have created similar before, with 1 GB of persistence, but the persistence just didn't really work for some odd reason.

SO the outline is that I want to install the Live CD to my USB, have at least 1GB of persistence and I'm also thinking of transferring some essential packages to the persistence/flash, like samba etc.

How would I go about doing this?

---

### Post by dandnsmith on 2010-12-04
The way I've used for similar jobs is to consult [pendrivelinux](http://www.pendrivelinux.com/) where you can find descriptions of how to do it, and any necessary links to software. Last time I looked the default persistance area was only 512MB, and I read up the scripts and constructed my own for 1G 2G and so on. There seem to be some snags with using this persistence - but, again, my knowledge may be out-of-date

---

### Post by sikander3786 on 2010-12-04
This one helps in most cases.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

And remember, you can always do a full install to your USB just as you'd have done to an internal HDD. And that would be persistent by nature :-)

It is recommended that you disconnect all internal drives, boot from an Installation media i.e, another USB or an Ubuntu disc and do an install to your desired USB.

If you are unable to disconnect the internal drives for any reason, select manual partitioning during installer and install Grub to the MBR of your USB drive. Those look like sda, sdb, sdc etc without an integer.

To find out your desired disc,

```
sudo fdisk -l
```

Be cautious. If Grub gets installed to any of your internal HDDs, it would need some hard work to recover the boot for those OS :-)

---

### Post by Strategist01 on 2010-12-04
Thanks guys

> **sikander3786 said:**
> This one helps in most cases.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

And remember, you can always do a full install to your USB just as you'd have done to an internal HDD. And that would be persistent by nature :-)

It is recommended that you disconnect all internal drives, boot from an Installation media i.e, another USB or an Ubuntu disc and do an install to your desired USB.

If you are unable to disconnect the internal drives for any reason, select manual partitioning during installer and install Grub to the MBR of your USB drive. Those look like sda, sdb, sdc etc without an integer.

To find out your desired disc,

```
sudo fdisk -l
```Be cautious. If Grub gets installed to any of your internal HDDs, it would need some hard work to recover the boot for those OS :-)

Ok, I have a Kubuntu 9.10 CD lying around...somewhere... If I boot from there, will I be able to install the 10.04.1 Live CD onto it? Or should I just boot from my current 10.04.1 installation on the disk drive?

I can't disconnect the drives, I'm on a laptop :/

Out of interest, can I keep my USB drive to be FAT32? I still have data that needs to be used in windows, and I don't want a flash that can only be used by Linux systems. And during manual install, it will give me the option of installing GRUB?

Thanks.

---

### Post by oldfred on 2010-12-04
A full install to 4GB would be very tight. Not much room for downloads, constant housecleaning and no room for an extra FAT partition. If your USB was larger then a full install would work.

My 4GB drive is FAT, uses grub2 to boot, and has multiple ISOs for installing or repairs.
With grub2 persistant C.S.Cameron post#15:
[http://ubuntuforums.org/showthread.php?t=1593656](http://ubuntuforums.org/showthread.php?t=1593656)

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by C.S.Cameron on 2010-12-04
A Full install to pendrive, as Fred says is tight, but works if you don't load up too many programs and use Computer Janitor frequently.

Usb-creator from the Live CD and Universal from pendrivelinux.com both work well for making a compact persistent drive.

---

### Post by efflandt on 2010-12-04
If you want to put live/install iso on USB w/1 GB persistent data, just make sure that you have less than 2 GB of files on it first.  The iso on USB uses FAT32 file system for the iso files anyway (initial boot is from a squashfs file and persistent data is a loop mounted file system called casper-rw).  No reason not to simply run Startup Disk Creator from your current 10.04 installation.

---

### Post by Strategist01 on 2010-12-04
Wow thanks for the info!

Basically, I have the 4GB flash with 600 to 700MB used in personal docs.

I wouldn't want a full install, I need to use it for other things, only have the one flash atm. So more like a Live CD, but with some of the packages that I can import from my current install? Re-downloading them is not really an option as I have an Internet connection which is capped to 18GB a month and I have to ration that...

I have a lot of reading to do, thanks.

---

### Post by C.S.Cameron on 2010-12-04
If you go the persistent disk image method, (usb-creator, Universal), you can mount the casper-rw persistence file and access it's folders as shown here:

[http://ubuntuforums.org/showpost.php?p=7055983&postcount=2](http://ubuntuforums.org/showpost.php?p=7055983&postcount=2)

---

