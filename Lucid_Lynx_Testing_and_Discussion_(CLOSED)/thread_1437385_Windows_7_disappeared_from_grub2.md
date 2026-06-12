---
title: "Windows 7 disappeared from grub2"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ernstblaauw on 2010-03-23
Hi,

Today I noticed Windows 7 is missing from my grub2 menu. I don't know for how long, but for sure, it was available in the boot menu not longer than a month ago (and I was running Lucid already).
I created a LaunchPad entry: [https://bugs.launchpad.net/bugs/545033](https://bugs.launchpad.net/bugs/545033)

I tried a couple of things:
- I downgraded os-prober, grub-pc and grub-common
- I repaired the boot process of Windows 7. Windows 7 booted correctly (but of course, no grub and thus no Linux). After that, I reinstalled grub2, but again: Windows 7 is not detected.

I have this issue too on my laptop. I don't have a clue what to do. Does someone here has an idea?

I attached the results from the bootinfoscript (v055). (I zipped it, otherwise I was running over my quotum)

---

### Post by kansasnoob on 2010-03-23
How, exactly, did you downgrade those grub2 packages?

Edit: To help me help you please boot into Lucid and post the output of:

```
df -H
```

And:

```
ls /boot/grub
```

And:

```
grub-install -v && aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4 && aptitude show os-prober|head -4
```

---

### Post by VMC on 2010-03-23
I quick looks shows you have both XP and 7 partitions on sda3, sda4.

My question is why did you try downgrade grub2? 

One thing I always try and do is keep Windows installed on the first partition. It doesn't like it when its anywhere else. It use to be in grub-legacy that you needed to map windows in if it was on a partition other than 1.

First i would say to re-install grub2, then update-grub and see if it catches your ntfs volumes.

Not sure what to make of the bottom message:
```
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg 

```
Also, you have errors on those coming from blkid. Is there something external plugged in?

---

### Post by djchandler on 2010-03-24
When I updated to the latest kernel (2.6.32-17 generic AMD64) yesterday, my default boot moved from Windows 7 at the bottom of my GRUB2 menu to 2 spots up and made the default memtest86+. Of course two items, the new kernel in both single user and normal mode were placed at the top of the menu. I had to use startup-manager to restore my default.

This appears to be buggy behavior to me, and appears to validate the OP's experience.

I manually partitioned on the clean install of Beta 1 and specified ext3 for / instead of ext4. Space for Ubuntu was created in Windows 7. Yes, I'm trying to break this--many people upgrading may still be using ext3 with live data.

---

### Post by ernstblaauw on 2010-03-24
> **kansasnoob said:**
> How, exactly, did you downgrade those grub2 packages?
I tried the two packages before the last one from here:
grub-pc, grub-common: [http://nl.archive.ubuntu.com/ubuntu/pool/main/g/grub2/](http://nl.archive.ubuntu.com/ubuntu/pool/main/g/grub2/) 

os-prober: [http://nl.archive.ubuntu.com/ubuntu/pool/main/o/os-prober/](http://nl.archive.ubuntu.com/ubuntu/pool/main/o/os-prober/)

> **kansasnoob said:**
> Edit: To help me help you please boot into Lucid and post the output of:

```
df -H
```

And:

```
ls /boot/grub
```

And:

```
grub-install -v && aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4 && aptitude show os-prober|head -4
```
```

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              58G  9.6G   46G  18% /
none                  2.0G  512K  2.0G   1% /dev
none                  2.0G  7.7M  2.0G   1% /dev/shm
none                  2.0G  508K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda5             164G  123G   33G  80% /home
/dev/sda4             320G  318G  1.4G 100% /mnt/media
/dev/sdb9             201G  180G   21G  90% /mnt/programma
/dev/sdb10             40G   39G  739M  99% /mnt/documents
/dev/sdc1              16G   13G  2.4G  85% /media/7CC3-8AD3_

```
/sdc1 is a usb stick.
```

$ ls /boot/grub
915resolution.mod  bsd.mod         device.map    gfxterm.mod  jfs.mod        memrw.mod       part_msdos.mod  reboot.mod          tga.mod           video_fb.mod
acpi.mod           bufio.mod       diskboot.img  gptsync.mod  jpeg.mod       minicmd.mod     part_sun.mod    reiserfs.mod        true.mod          video.lst
affs.mod           cat.mod         dm_nv.mod     grldr.img    kernel.img     minix.mod       parttool.lst    relocator.mod       udf.mod           video.mod
afs_be.mod         cdboot.img      drivemap.mod  grub.cfg     keystatus.mod  mmap.mod        parttool.mod    scsi.mod            ufs1.mod          videotest.mod
afs.mod            chain.mod       echo.mod      grubenv      linux16.mod    moddep.lst      password.mod    search_fs_file.mod  ufs2.mod          xfs.mod
aout.mod           charset.mod     efiemu32.o    gzio.mod     linux.mod      msdospart.mod   pci.mod         search_fs_uuid.mod  uhci.mod          xnu.mod
ata.mod            cmp.mod         efiemu64.o    halt.mod     lnxboot.img    multiboot.mod   play.mod        search_label.mod    unicode.pf2       xnu_uuid.mod
ata_pthru.mod      command.lst     efiemu.mod    handler.lst  loadenv.mod    normal.mod      png.mod         search.mod          usb_keyboard.mod  zfsinfo.mod
at_keyboard.mod    configfile.mod  elf.mod       handler.mod  locale         ntfscomp.mod    probe.mod       serial.mod          usb.mod           zfs.mod
befs_be.mod        core.img        ext2.mod      hdparm.mod   loopback.mod   ntfs.mod        pxeboot.img     setjmp.mod          usbms.mod
befs.mod           cpio.mod        extcmd.mod    hello.mod    lsmmap.mod     ohci.mod        pxecmd.mod      sfs.mod             usbtest.mod
biosdisk.mod       cpuid.mod       fat.mod       help.mod     ls.mod         part_acorn.mod  pxe.mod         sh.mod              vbeinfo.mod
bitmap.mod         crc.mod         font.mod      hexdump.mod  lspci.mod      part_amiga.mod  raid5rec.mod    sleep.mod           vbe.mod
blocklist.mod      datehook.mod    fshelp.mod    hfs.mod      lvm.mod        part_apple.mod  raid6rec.mod    tar.mod             vbetest.mod
boot.img           date.mod        fs.lst        hfsplus.mod  mdraid.mod     part_gpt.mod    raid.mod        terminfo.mod        vga.mod
boot.mod           datetime.mod    gettext.mod   iso9660.mod  memdisk.mod    partmap.lst     read.mod        test.mod            vga_text.mod

```

and the last one:
```

$ grub-install -v && aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4 && aptitude show os-prober|head -4
grub-install (GNU GRUB 1.98-1ubuntu2)
Package: grub
State: not installed
Version: 0.97-29ubuntu60
Priority: optional
Package: grub-pc
State: installed
Automatically installed: yes
Version: 1.98-1ubuntu2
Package: grub-common
State: installed
Automatically installed: yes
Version: 1.98-1ubuntu2
Package: os-prober
State: installed
Automatically installed: yes
Version: 1.36

```


> **VMC said:**
> I quick looks shows you have both XP and 7 partitions on sda3, sda4.

I actually only use Windows 7 (which is on sda3), the other ones (XP's) are old or used for some other purpose. I don't even know if they could still boot; I only know for sure Windows 7 is bootable. Btw, does it matter which version of W7 is installed?

> **VMC said:**
> 
My question is why did you try downgrade grub2? 

To see if an upgrade of grub or os-prober introduced a new bug, namely that it skips some valid installations. But the bug is not (at least not not only) caused by those packages, as I downgraded to packages which did provide W7 at that point.

> **VMC said:**
> 
One thing I always try and do is keep Windows installed on the first partition. It doesn't like it when its anywhere else. It use to be in grub-legacy that you needed to map windows in if it was on a partition other than 1.
It used to work, and now W7 has disappeared on my two machines. So I guess my two setups have something in comming, making grub2 skipping W7. Of course, this could be triggered by not installing W7 on /sda1.

> **VMC said:**
> First i would say to re-install grub2, then update-grub and see if it catches your ntfs volumes.
I already did this by downgrading my packages and after that I did update-grub. But never, W7 came back.

> **VMC said:**
> 
Not sure what to make of the bottom message:
```
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg 

```
Also, you have errors on those coming from blkid. Is there something external plugged in?
I have almost always a usb stick plugged in.

@djchandler:
I guess you spotted a different bug: you still have W7 in your list.

---

### Post by ernstblaauw on 2010-03-24
I found the cause! I always install the latest ntfs-3g driver. It seems, that ntfs-3g 2010.3.6AR2 (thus the advanced release) triggers a fail in os-prober: it does not find my W7 partition correctly.
However, downgrading to 2010.3.6 (from source) or 2009.4.4 (package in Lucid) solves my problem!
I will report this problem to the developers of ntfs-3g.

---

### Post by VMC on 2010-03-24
> **ernstblaauw said:**
> I found the cause! I always install the latest ntfs-3g driver. It seems, that ntfs-3g 2010.3.6AR2 (thus the advanced release) triggers a fail in os-prober: it does not find my W7 partition correctly.
However, downgrading to 2010.3.6 (from source) or 2009.4.4 (package in Lucid) solves my problem!
I will report this problem to the developers of ntfs-3g.

Interesting and good to know. I never thought of upgrading ntfs since it works fine for me, and may not be a good idea in the midst of testing a new os.

---

### Post by ernstblaauw on 2010-03-24
> **VMC said:**
> Interesting and good to know. I never thought of upgrading ntfs since it works fine for me, and may not be a good idea in the midst of testing a new os.
Well, it is true I maybe should not upgrade such drivers. However, the version provided by Ubuntu (2009.4.4) is rather old and Tuxera has released several new versions which provide not only speed enhancements (which is nice, but not necessary), but also bug fixes. Tuxera has already issued a recommendation to upgrade to version 2010.1.16, as it contains a quite important bug fix. As ntfs-3g is improving quite fast, I usually update to the latest stable version available, because I think my data is the most safe with that driver.

---

### Post by VMC on 2010-03-24
> **ernstblaauw said:**
> Well, it is true I maybe should not upgrade such drivers. However, the version provided by Ubuntu (2009.4.4) is rather old and Tuxera has released several new versions which provide not only speed enhancements (which is nice, but not necessary), but also bug fixes. Tuxera has already issued a recommendation to upgrade to version 2010.1.16, as it contains a quite important bug fix. As ntfs-3g is improving quite fast, I usually update to the latest stable version available, because I think my data is the most safe with that driver.

I'm not sure where you would file a bug report. It probably would also have problems using a previous ubuntu release.

 Now that I that I think about it, sounds like os-prober is at fault.

---

