---
title: "Clone Dual Boot Windows 7/Unbuntu HD on i7 14.04"
date: 2015-09-02
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2015-09-02
Hello,

I've been using Dual Boot Win7/Ubuntu systems for years and have always been able to use Clonezilla, Apricorn Easy GIG, or Acronis True Image to upgrade, or clone the HD to backup my laptop. This always worked fine as long as I was on AMD architecture. Then I bought my new laptop with an i7 processor, thinking I was getting the latest and greatest. Little did I know what trouble lay in store for me at upgrade or backup time. I have never been able to successfully clone this configuration; and now I think I know why. Intel/MS have again conspired to take control of our pc's!

It turns out that systems drives in an Itanium rig have to be partitioned to the GPT spec; MBR is not allowed! That means that Clonezilla cannot create the partition table proportionally, which is necessary when upgrading to a larger drive. I'm upgrading from a 320 GB to a 1 TB drive. Both Apricorn and Acronis complain that cloning to a drive with a different block size is not allowed. Clonezilla can't read sdb2. When I have gotten Clonezilla to work, it will only copy the source partition table; which means I can only use 320 GB of a 1TB drive. This is less than useless! I then scoured google for any hint at solving this mystery. The only other suggestion was to backup an image to a usb drive and restore it to the target drive. That didn't work either.

Now I'm stuck trying to figure out how I'm ever going to upgrade. This is why I hate new builds.

Any help appreciated.

Thanks, Hannibal

---

### Post by oldfred on 2015-09-02
Not really answering your question. But I thought some of the newer versions of clone tools would work with gpt partitioning. I do not use cloning.

But I believe in new clean installs, copy /home and/or data partitions data to new install and export list of installed apps and reinstall. Not a lot more work, but a few more steps involved. But I am regularly backing up all the data I need to do a new install as if drive every fails that is what I will do to reinstall to new drive.

---

### Post by coljohnhannibalsmith on 2015-09-02
> **oldfred said:**
> Not really answering your question. But I thought some of the newer versions of clone tools would work with gpt partitioning. I do not use cloning.

But I believe in new clean installs, copy /home and/or data partitions data to new install and export list of installed apps and reinstall. Not a lot more work, but a few more steps involved. But I am regularly backing up all the data I need to do a new install as if drive every fails that is what I will do to reinstall to new drive.

I looked up Clone Tools and what I found is just for eliminating duplicate files. Another cloning tool I tried complained about source and target drive sector sizes being inconsistent. Is there a tool that will discover what the sector sizes are; and is there anyway to control this during partitioning/formatting?

---

### Post by oldfred on 2015-09-02
New large drives use 4K sectors, but logical sectors still are 512.
Some external drives use proprietary layouts to make a very large drive work with XP. Large drives require gpt partitioning and gpt does not work with XP.

You can see sizes with 
sudo parted -l

One line will be this:
Model: ATA WDC WD10EZEX-00B (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B

---

### Post by coljohnhannibalsmith on 2015-09-07
Believe it or not, I actually accomplished the feat; it was indeed a crucible. Please allow me to elaborate.

My current build actually took place on an older machine, a Dell Inspiron 1545; since I didn't want to compromise my existing build. This was in MBR format. Clonezilla would only clone my multi-boot, multi-partition drive as 1 to 1 without expanding the file system to fit the 1TB target drive; so I went with it. I did this for two reasons. The first was to have at least one functioning BU of my current build. The second was a little more complex. When I tried to clone the source drive with the option to expand the file system selected, Clonezilla would continually complain about not being able to read the second partition on the target drive (device sda2 not found). This initially made me suspect that there was something wrong with the drive itself. After determining that the drive was good, the idea occurred to me that Clonzilla was expecting the second partition on the target drive to have already been created; so repeating the cloning process in the 1 to 1 mode would do that w/o my having to create the partitions manually. Fortunately my hunch paid off; and I was able to use another cloning product, EasyGIG IV, to clone and expand the file system from the first 320GB drive to a second 1TB drive, that I purchased for this purpose. Then cloning once more between the two 1TB drives, I finally managed to get the correct expanded image copied to both 1TB drives. Unfortuately, EasyGIG IV did not copy GRUB onto either of the target drives; so when I tried booting, I was left staring at the GRUB Rescue prompt. (grub rescue>). It was then necessary for me to search BING to look for the appropriate commands to boot the system; so that I could update GRUB.  The procedure was as follows:

```

grub rescue>
     set prefix=(hd0,msdos5)/boot/grub
     set root=(hd0,msdos5)
     insmod normal
     normal
     insmode linux
     linux /boot/vmlinuz-3.16.0-45-generic
     initrd /boot/initrd.img-3.16.0-45-generic
     boot

```

The system did indeed boot. I was then able to update GRUB with the following commands:
```

     sudo update-grub
     sudo grub-install /dev/sda

```

This not only allowed my system to boot normally; it also found and included the dual-boot menu and the splash screen I configured with GRUB Customizer. I then repeated the procedure with the second 1TB drive. It should now be possible to just use Clonezilla in 1 to 1 copy mode for future BUs. My conclusion is that none of these cloning tools are a complete solution. IMHO cloning multi-boot systems is a dodgy endeavor, that will only yield success after the application of careful observation and clever wits.

BTW, both 1TB drives are in MBR format and are running fine on my Itanium (I7) laptop.

---

