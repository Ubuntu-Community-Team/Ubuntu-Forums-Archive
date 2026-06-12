---
title: "Windows XP in Grub but can't boot to it"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by SteadyEdward on 2009-12-28
I've searched as best I can for my specific situation but can't find a solution (and I don't know Ubuntu enough to make educated guesses) but I've installed 9.10 to dual boot with my XP Home system. Everything is fine with Ubuntu (and it's great..)..but, although XP is showing in my boot list, when I select it the screen blanks for a second then returns to the boot list. I can mount the Windows partition (/dev/sda2) and browse the files etc (and the 3 files, boot.ini,NTLDR,NDETECT.COM are present). Boot.ini seems to show the windows partition correctly (see below)
========================
  GNU nano 2.0.9                    File: /Win/boot.ini                                                

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fast$
========================

========================
edward@edward-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfbbc7c52

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1669    13406211   12  Compaq diagnostics
/dev/sda2   *        1670       13903    98269605    c  W95 FAT32 (LBA)
/dev/sda3           13904       19457    44612505    5  Extended
/dev/sda5           13904       19224    42740901   83  Linux
/dev/sda6           19225       19457     1871541   82  Linux swap / Solaris
edward@edward-laptop:~$
==========================
My grub.cfg (extract)
==========================
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 580ecce0-8424-4293-b82f-770afa5e1446
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=580ecce0-8424-4293-b82f-770afa5e1446 ro  vga=773  quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 580ecce0-8424-4293-b82f-770afa5e1446
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=580ecce0-8424-4293-b82f-770afa5e1446 ro single  vga=773
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
	insmod fat
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 320d-180e
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###
=========================
I'm sure there's a simple solution but Ubuntu is new to me (at this level)
Regards, Edward

---

### Post by blue99 on 2010-05-02
[SIZE=2]I have the exact same problem.  Did you find a solution?[/SIZE]

---

### Post by Jeff Anthony on 2010-05-02
[http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)

```
apt-get install ms-sys
sudo ms-sys -m /dev/sda2
```

warning to blue99 and others: don't follow these steps unless you're sure sda2 is the correct partition the same way SteadyEdward did

```
sudo fdisk -l
```

---

### Post by SFCampbell on 2010-05-03
Blue,

Mr. Anthony's post will fix the MBR (master boot record) of your windows partition which could resove your problem, however if your problem persists then it may be caused by a bad directer in your GRUB configuration.  Depending on the path that your '/boot/grub/grub.cfg' has to point to your windows partition you may have to toy around with it.  

When you boot up your machine and you reach the GRUB menu, try selecting your Windows boot option and press '**e**' for edit, then delete the line that specifies your **UUID** and hit CTRL+X to see if that works.  This change is not permanent so even if it doesn't work no harm will be done.

Please post your machine's **fdisk -l** and **/boot/grub/grub.cfg** if the problem persists.

---

### Post by Bucky Ball on 2010-05-03
If you have XP in there not sure why you have it on a FAT32 partition. NTFS better.

... and under the windows entry try:

hd(0,1)

---

### Post by efflandt on 2010-05-03
It looks like the UUID for the Windows entry in your grub.cfg might have either gotten mangled or is for your Compaq recovery partition:

search --no-floppy --fs-uuid --set 320d-180e

On my HP it looks like this, where the first entry is the HP recovery partition and 2nd with (loader) is the XP Home partition.  But I have grub2 on a partition, in which case it does not specifically identify which Windows version.  It could just be that your UUID is shorter because it is FAT32 (like my HP partition) instead of NTFS (like my XP partition):

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    saved_entry=${chosen}
    save_env saved_entry
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2e35-2ef9
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (loader) (on /dev/sda2)" {
    saved_entry=${chosen}
    save_env saved_entry
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set c644a78244a77439
    drivemap -s (hd0) ${root}
    chainloader +1
}

Does your boot.ini really have a $ at the end, or were you viewing it in a not wide enough terminal with nano?  Mine has other stuff in it I need to remove from when I had WinXP 64 beta, but my entry for XP Home on same partition as yours:

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

---

### Post by oldfred on 2010-05-03
I am posting this until I am blue in the face. About 75% find it works, a few need other fixes. See  the boot info script referred to in link.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If this does not fix it each poster should start their own thread and post the results.txt (see link above and link on that site).

---

