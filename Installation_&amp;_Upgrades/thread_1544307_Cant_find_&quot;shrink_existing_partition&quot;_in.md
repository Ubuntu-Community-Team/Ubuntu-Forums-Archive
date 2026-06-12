---
title: "Cant find &quot;shrink existing partition&quot; in gui installer....only delete/manual advanced"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by UbuNoob001 on 2010-08-02
Hey all very newbie question here.

Situation: I have done two installs of Ubuntu before, one was 10.04 on my own system, and 9.10 on a friends. I am now trying to do a 10.04 dual boot for my friend on his dell 1521 insprion laptop. 

Question: When I load the live cd >install after the opening options for timzone/keyboard etc, then only options for partitioning are to 1. completely reformat his entire other OS partition (on which he has Vista), and 2. Advanced partitioning. What do you think is the problem? 

below is the partition table

```
/sda1   fa16 Dell Utility     109 mib
/sda2   ntfs recovery      10gb
/sda3   ntfs OS             220.28 gb
/sda 4  Extended            2GB
         unallocated 1.0 mib
         fat32    MEDIADIRECT    2.5gb
```

---

### Post by viralmeme on 2010-08-02
> **UbuNoob001 said:**
> ```
/sda1   fa16 Dell Utility     109 mib
/sda2   ntfs recovery      10gb
/sda3   ntfs OS             220.28 gb
/sda 4  Extended            2GB
         unallocated 1.0 mib
         fat32    MEDIADIRECT    2.5gb
```

Dunno, I guess Dell don't want you messing with the partition layout and you may bork the "instant on" or the recovery partition.  You do have a full Dell recovery CD, not the basic one that relies on the presence of the recovery partition?

[MediaDirect provides "instant on" access to multimedia and other items]("http://support.dell.com/support/topics/global.aspx/support/dsn/document?c=us&l=en&s=gen&docid=278270")

---

### Post by UbuNoob001 on 2010-08-02
> **viralmeme said:**
> Dunno, I guess Dell don't want you messing with the partition layout and you may bork the "instant on" or the recovery partition.  You do have a full Dell recovery CD, not the basic one that relies on the presence of the recovery partition?

[MediaDirect provides "instant on" access to multimedia and other items]("http://support.dell.com/support/topics/global.aspx/support/dsn/document?c=us&l=en&s=gen&docid=278270")

Okay, well there must still be a way to get around this, are you suggesting trying to disable media direct in some way and this might help? I have defragged.

---

### Post by oldfred on 2010-08-02
I think the auto partitioner saw all four partitions in use (even though one is already the extended), so it cannot auto adjust.

With manual partitioning you can shrink the NTFS partition. If XP you can use gparted, but if Vista or 7, you should use the windows tools to shrink the windows install. Then you will have to expand the extended partition into the new free space and create partitions for root, swap & optionally /home . From the installer you can assign / (root), &  /home. If in partitioning you make the swap as swap it will find it, if not tell it which partition is swap.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by efflandt on 2010-08-02
What Windows version is on it?  Something also looks odd about what you posted, because that does not show the sda# for the MEDIADIRECT logical partition.  I have a work Dell laptop like that and I just decided not to tamper with it and boot 64-bit Ubuntu from a USB hd (WD Passport).

Although, that can be somewhat problematic for a Dell laptop that goes through its splash screen so fast that the USB hard drive has not spun up yet and is not recognized on cold boot.  So I usually either have to change something in CMOS setup that is insignificant (like boot order or floppy and CD/DVD) or boot to WinXP first and then reboot.  At a motel I often boot Windows first anyway to establish a wireless connection, and after that it will allow Linux to connect based on MAC address.

As mentioned, if running Vista or Win7, use its computer management to shrink Windows first.  Or for XP first boot to Windows, make a note of virtual memory settings, and disable virtual memory and reboot for that to take effect.  Otherwise the unmovable virtual memory may limit how much you can shrink it.  Then boot to a live Ubuntu system on CD or bootable iso on USB flash and use gparted to shrink the XP partition.  That resizing the Windows partition with gparted marks it as dirty so Windows will check it during boot, so you may then want to boot Windows to make sure everything is OK.

I don't know if MEDIADIRECT is booted to a specific location on the disk or a specific partition.   So I don't know if that will work leaving it where it is, ending up with a higher sda#, or moving the beginning of the extended partition down and then moving that down to the beginning of that so it remains sda5.  If that is not important to you, you may want to first uninstall that from Windows before you even start doing anything else.  Then you could shrink the Windows partition delete sda5(?) and sda4, then recreate a larger extended hda4 and whatever logical partition(s) you want in it for Ubuntu.

---

