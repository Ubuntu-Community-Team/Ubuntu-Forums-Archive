---
title: "Persistent USB UFEI Installation Help"
date: 2016-05-03
forum: Installation &amp; Upgrades
---

### Post by charlesofstate on 2016-05-03
Greetings all! I come to you in my hour of need. 

I have a Lenovo Yoga 2 13inch laptop, and I'd like to install Ubuntu on my flash drive. 
Currently, I have another flash drive with Ubuntu live usb running. 
So, in essence I'm trying to install Ubuntu onto a flash drive from another flash drive. 

I know there are a lot of threads that cover this, but I can't figure out which method would be best.
The only problem as far as I can tell is that this machine is UEFI. 

Can anyone point me in the right direction here?

* Just to give a bit more detail, I'm a Ruby on Rails developer, and I'd really like to have a portable linux environment. 
The drive only needs to boot on this laptop, but I need to be able to save work and install packages. 

Thanks,
Charles.

---

### Post by oldfred on 2016-05-03
Depends on whether you want flash drive to boot in UEFI or CSM/BIOS mode. But either way it requires the Something Else install option and best to partition in advance with gpt partitioning.
I normally add both the ESP - efi system partition and a bios_grub partition, so it can be configured for either UEFI or CSM.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation) 
    
Some Yoga specific issues.
 With the Linux 4.4 kernel the Lenovo Yoga 3 laptop owners out there will finally have support for using their ESC key.
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.4-ESC-Key-Patch](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.4-ESC-Key-Patch)
Many Lenovo function key issues
[https://groups.google.com/forum/#!topic/fa.linux.kernel/f7lTE1YafwQ](https://groups.google.com/forum/#!topic/fa.linux.kernel/f7lTE1YafwQ)
Lenovo Yoga 11s (Intel i5/Intel HD 4000)
Needed this: acpi_backlight=vendor 
[http://ubuntuforums.org/showthread.php?t=2188199](http://ubuntuforums.org/showthread.php?t=2188199)
[http://ubuntuforums.org/showthread.php?t=1911972](http://ubuntuforums.org/showthread.php?t=1911972)
Yoga2
[http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/](http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/)
Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive 

My 32GB flash drive's partitions.
```
Disk /dev/sdc: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name        Flags
 1      20.5kB  500MB   500MB   fat32        EFI System  boot, esp
 2      500MB   501MB   1049kB                           bios_grub
 3      501MB   15.2GB  14.7GB  ext4         sys
 4      15.2GB  31.0GB  15.8GB  ext4         data32      msftdata

```

If you install in UEFI mode, you also have to copy files to flash drive from sda's ESP.
[http://ubuntuforums.org/showthread.php?t=2323172&p=13482619#post13482619](http://ubuntuforums.org/showthread.php?t=2323172&p=13482619#post13482619)

---

### Post by ubfan1 on 2016-05-03
One of the 16.04 Ubuntu's would be a good starting point, with the 4.4 kernel.  For a more portable USB stick, you could just make an install media with two 4G writeable files (the max size), casper-rw and home-rw, assuming you have at least a 16G stick.  For an 8G stick, make the files smaller.  The home-rw file would be for your personal files, and the casper-rw for the additional packages you want to install.  You won't get any security patches this way, since the kernel booted is fixed at creation time, but the stick would be both legacy/UEFI bootable, and run on most systems.
  Doing a full install to the stick is probably better, since you don't care about portability, and you can use all of the stick's memory.

---

### Post by charlesofstate on 2016-05-03
Thanks guys. I'm still researching, but I still haven't come across anyone saying "This is what you need to do." 
I'm wanting to do a uefi only boot. 
Since my 1st drive already runs usb live, isn't there something in there I can just replace with the full version of Ubuntu?

---

### Post by ubfan1 on 2016-05-03
The live media and a full install are pretty different, but if you just want to tweak a live system, and you installed it on a USB with a large FAT partition instead of a minimum 2G, you can just add the casper-rw and home-rw files, and put an ext2 filessytem (or ext4 non-journaling) on them.  Then add the word "persistent" to the grub kernel boot line, and you should be all set with a persistent USB, as if you had created it that way to begin with.  I have never used a home-rw, just the casper-rw file.  I have used an ext4 partition labeled "casper-rw" instead of the file, and that worked.  I have used the "toram" on the kernel boot line, and that copies the compressed filesystem into ram, and produces really quick responses for a USB based system.  I have had a full USB as my main system for years with no problems also, so what you do is dependent upon your needs.  The live-media with persistence is so easy to create, that might be a good starting point.  If you want a full install for the system updates you cannot get on a live media, you could always copy off any of your files from the live media (or just move the casper-rw/home-rw files to the new system and mount them with a loop option.

---

