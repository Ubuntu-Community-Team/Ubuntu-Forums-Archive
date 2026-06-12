---
title: "Dual boot Xubuntu 15.04 Windows 8 on a laptop Yoga 2 (Lenovo)"
date: 2015-07-11
forum: Installation &amp; Upgrades
---

### Post by jawaka. on 2015-07-11
Hello,

I've recently bought a new laptop : Yoga 2 (mark Lenovo) with Windows 8 pre-installed. I want to install a dual boot with Xubuntu 15.04 on it. I have created a live USB Xubuntu amd64 with Lili USB creator then booted on USB and installed Xubuntu without any problems. I chose "automatic partition" during the partition process. Reboot. Everything was normal with GRUB. I launched Xubuntu. It was ok. Reboot. I launched Windows. Still OK. But then I reboot and there was no GRUB :( Windows was automatically launched.

I tried "boot-repair" which told me to disable "boot secure". OK. But then I tried "boot-repair" and I got this message :

```
An error occurred during the repair.

Please write on a paper the following URL:
http://paste.ubuntu.com/11849163/


In case you still experience boot problem, indicate this URL to:
boot.repair@gmail.com 

Locked-ESP  detected. You may want to retry after creating a /boot/efi partition  (FAT32, 100MB~250MB, start of the disk, boot flag). This can be  performed via tools such as gParted. Then select this partition via the  [Separate /boot/efi partition:] option of [Boot Repair].
```

And here I'm stuck. What should I do ?

Thank you for any answers ! :)
 
==========================================

EDIT 16h46 same day :

I have seen this thread :

[http://ubuntuforums.org/showthread.php?t=2112273](http://ubuntuforums.org/showthread.php?t=2112273)

So I tried it. The problem is that there is nothing in /EFI/ubuntu.  /EFI is composed of 3 folders : boot, windows and ubuntu. In boot there is a bootx64.efi file. May be this is the one I should erase ?

---

### Post by oldfred on 2015-07-11
Did you try backing up ESP - efi system partition or sda2. I think sda3 is just for Lenovo's boot files for recovery. 
And then totally delete sda2. Then recreate sda2 as FAT32 with the boot flag so it is the ESP again. And restore the Windows files. 
Then Boot-Repair when running grub updates should be able to write into it. 

You may not be able to manually write into it either if locked. Not sure how the lock occurs as it should not be possible on FAT32. Some have managed to just run chkdsk from Windows or fsck -t vfat from Linux.
 sudo fsck -t vfat /dev/sda2

Some systems will not boot ubuntu entry in UEFI, and for many of those a work around is to copy grub or shim into /EFI/Boot and rename grub to bootx64.efi. That is a hard drive or fallback boot entry that usually then works for those systems that do not let anything but Windows boot.

      
 Yoga2
[http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/](http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/)
Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)

 Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

---

### Post by jawaka. on 2015-07-12
1st I forgot to mention the last log of boot-repair :

[http://paste.ubuntu.com/11861282/](http://paste.ubuntu.com/11861282/)

There is something different :

```

Jul 11 14:42:06 xubuntu kernel: [ 3108.656325] FAT-fs (sda2): Corrupted directory (i_pos 131207)

```

I don't exactly understand that ...

2nd : Thank you oldfred for your help ! But I'm note sure of what I understand. You tell me to do :

. backup sda2 (with partclone ?)
. delete sda2 (with gparted)
. recreate sda2, FAT32 boot flag (with gparted)
. restore windows files (are they the backup ?)
. sudo fsck -t vfat /dev/sda2
. boot-repair

---

### Post by oldfred on 2015-07-12
I would not use partclone as that may clone the issue.
One advantage of UEFI is that boot files need no special program to reinstal. You can just copy with Nautilus, command line, or however you copy a few files & folders. Then use same tools to copy back.

You can try the fsck first just to see if that fixes it without the deletion. But having a copy of the ESP is highly recommended even if you were not installing Ubuntu.

Boot-Repair then is just to reinstall grub so you get new folder for ubuntu in ESP so from UEFI boot menu you can choose the ubuntu entry. That can also be done from command line, but Boot-Repair is a bit easier.

Just noticed you created a sda10 that also now is an efi partition. You can only have one ESP - efi system partition per hard drive or device. Was that your backup? At least remove boot flag so it then is just a FAT32 data partition and not an efi.

---

### Post by jawaka. on 2015-07-13
I solved it !! :)

So, here's what I did :

[LIST]
[*] back up sda2 and sda3 after mounting both partitions (with thunar) 
[*] delete sda2 (gparted) 
[*] create sda2 fat32 boot, hidden (and not sda3) 
[*] backup the preceding files (thunar) 
[*]now I don't remember exactly f I unmounted sda2 ... 
[*] fsck -t vfat /dev/sda2 
[/LIST]

It said that there was a problem but it does not seem that it has solved it ...

```

xubuntu@xubuntu:~$ sudo fsck -t vfat /dev/sda2
fsck from util-linux 2.25.2
fsck.fat 3.0.27 (2014-11-12)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
1) Remove dirty bit
2) No action
? 1
Orphaned long file name part "ubuntu"
1: Delete.
2: Leave it.
? 1
Leaving filesystem unchanged.
/dev/sda2: 180 files, 8104/65536 clusters
xubuntu@xubuntu:~$ sudo fsck -t vfat /dev/sda2
fsck from util-linux 2.25.2
fsck.fat 3.0.27 (2014-11-12)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
1) Remove dirty bit
2) No action
? 1
Orphaned long file name part "ubuntu"
1: Delete.
2: Leave it.
? 1
Leaving filesystem unchanged.
/dev/sda2: 180 files, 8104/65536 clusters
xubuntu@xubuntu:~$ sudo fsck -t vfat /dev/sda3
fsck from util-linux 2.25.2
fsck.fat 3.0.27 (2014-11-12)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
1) Remove dirty bit
2) No action
? 1
Leaving filesystem unchanged.
/dev/sda3: 479 files, 133463/254976 clusters

```

  
[LIST]
[*]Reboot but it launched automatically Windows.
[*]  I tried a boot-repair. But it told me that there was no boot partition and that I had to create a grub-boot partition.
[/LIST]
 
[LIST]
[*]I tried to give a label to sda2 because there was no label attached to this partition as I re-created it. So I tried to use e2label but it returned an error like : "bad superbloc".
[*]  umount /mnt/sda2
[*]  boot-repair and then it works, what !!!!?????
[/LIST]
 
```

Boot successfully repaired.

Please write on a paper the following URL:
http://paste.ubuntu.com/11871729/


In case you still experience boot problem, indicate this URL to:
boot.repair@gmail.com or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda (500GB) disk!

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi

```


Then reboot and there was the menu. I launched WIndows and reboot : OK !

Even if I have not understood why it has worked, I think it's ok !
Thank you a lot oldfred :)

---

### Post by oldfred on 2015-07-13
Not sure what fixed it but glad it worked. :)

---

