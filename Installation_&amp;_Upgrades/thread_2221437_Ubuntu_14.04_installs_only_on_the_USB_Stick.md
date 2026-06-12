---
title: "Ubuntu 14.04 installs only on the USB Stick"
date: 2014-05-02
forum: Installation &amp; Upgrades
---

### Post by markcgriffiths2 on 2014-05-02
I tried to install Ubuntu from the USB and it went with no problems.  Then I had to reboot and I took the USB stick out, after that I have a message no OS available, it seems to install on the USB stick, how can I tell it to install on my C drive?

---

### Post by markcgriffiths2 on 2014-05-02
Seems, I have this error:

[http://askubuntu.com/questions/141879/error-1962-no-operating-system-found-after-installing-12-04-lenovo-thinkcentre](http://askubuntu.com/questions/141879/error-1962-no-operating-system-found-after-installing-12-04-lenovo-thinkcentre)

I have a Lenovo A720, so far no luck.

---

### Post by fantab on 2014-05-02
Boot with the Ubuntu USB and "Try Ubuntu without installing".
Open Terminal [ctrl+alt+T], run the following and post its output here:

```
sudo parted -l
sudo fdisk -l
```

---

### Post by markcgriffiths2 on 2014-05-02
I tried boot repair as said here:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I got the following error:

[http://paste2.org/eegjWXgf](http://paste2.org/eegjWXgf)

Not even the USB works now.  Will I need to reinstall again?

Only started using Ubuntu today, no idea what I'm doing :)

---

### Post by markcgriffiths2 on 2014-05-02
Booting from a DVD gives:
[FONT=arial]ubuntu@ubuntu:~$ sudo parted -l[/FONT]
[FONT=arial]Model: ATA HGST HTS541010A9 (scsi)[/FONT]
[FONT=arial]Disk /dev/sda: 1000GB[/FONT]
[FONT=arial]Sector size (logical/physical): 512B/4096B[/FONT]
[FONT=arial]Partition Table: gpt[/FONT]

[FONT=arial]Number  Start   End     Size    File system     Name  Flags[/FONT]
[FONT=arial] 1      1049kB  538MB   537MB   fat32                 boot[/FONT]
[FONT=arial] 2      538MB   992GB   991GB   ext4[/FONT]
[FONT=arial] 3      992GB   1000GB  8543MB  linux-swap(v1)[/FONT]


[FONT=arial]Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0[/FONT]
[FONT=arial]has been opened read-only.[/FONT]
[FONT=arial]Error: Can't have a partition outside the disk!                         [/FONT][FONT=arial]  [/FONT]

[FONT=arial]ubuntu@ubuntu:~$ sudo fdisk -l[/FONT]

[FONT=arial]WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.[/FONT]


[FONT=arial]Disk /dev/sda: 1000.2 GB, 1000204886016 bytes[/FONT]
[FONT=arial]255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT]
[FONT=arial]Disk identifier: 0x9d9cab17[/FONT]

[FONT=arial]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=arial]/dev/sda1               1  1953525167   976762583+  ee  GPT[/FONT]
[FONT=arial]Partition 1 does not start on physical sector boundary.[/FONT]
[FONT=arial]ubuntu@ubuntu:~$ [/FONT]

---

### Post by fantab on 2014-05-02
```
Installation finished. No error reported.
BootCurrent: 0002
Timeout: 2 seconds
BootOrder: 0002
Boot0002* UEFI: KingstonDataTraveler 2.0PMAP
BootCurrent: 0002
Timeout: 2 seconds
BootOrder: 0000,0002
Boot0002* UEFI: KingstonDataTraveler 2.0PMAP
Boot0000* ubuntu,BootCurrent: 0002
Timeout: 2 seconds
BootOrder: 0002
Boot0002* UEFI: KingstonDataTraveler 2.


```

Hard Disk is not in the boot picture. UEFI is booting only your USB drive...
Check your UEFI settings and look for Boot Order, there you have to set your HDD or Ubuntu as your first boot option.

However I am not sure why the above code in bootinfo summary does not show HDD... 

I suggest you reinstall ubuntu after you disable 'Secure Boot'.
Since you are not dual-booting and that there is no windows disabling 'secure boot' is a very good idea.

---

### Post by markcgriffiths2 on 2014-05-03
I disabled UEFI and selected legacy, not sure if this is slower but it works OK.

---

### Post by fantab on 2014-05-05
> **markcgriffiths2 said:**
> I disabled UEFI and selected legacy, not sure if this is slower but it works OK.

You shouldn't have done that. **Enable** it.
how does it work Ok?

```
parted -l: 
Model: ATA HGST HTS541010A9 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
[COLOR=#ff0000]**Partition Table: gpt**[/COLOR]

 
Number  Start   End     Size    File system     Name  Flags
1      1049kB  538MB   537MB   fat32                 boot
2      538MB   992GB   991GB   ext4
3      992GB   1000GB  8543MB  linux-swap(v1)


```

Since you have a GPT partition table you have boot with UEFI enabled... and Ubuntu should boot. In case it doesn't the reinstall.
[Advantages of GPT]("https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT").

You can use 'legacy' mode on GPT disks but then you'll have make a 10Mb un-formatted partition with 'bios_grub' flag on it.

Disable 'secure boot'.
And Re-install Ubuntu.

Its a good idea to keep your system files and your personal data separate.
25Gb Ext4 '/' for system files
???Gb Ext4 '/home' for personal data
swap...

---

