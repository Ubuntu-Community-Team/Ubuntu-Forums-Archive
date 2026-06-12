---
title: "No Grub after installing ubuntu studio; Windows 7 doomed"
date: 2015-01-27
forum: Installation &amp; Upgrades
---

### Post by prasad13 on 2015-01-27
Hello everyone!

I am new to ubuntu(or linux) & i need urgent help!!


I did a complete formatting & re-partitioning of my hard disk.

After  that I installed windows 7 (64 bit) first & then ubuntu studio (64  bit). But after installing ubuntu studio, it did'nt bother to install  grub or any software to allow me to enter windows 7.


I used the boot repair software for the problem. Boot repair installed a grub menu but there is no option for windows.


[B]Also, it gave me a URL to indicate my boot repair stats or something!
[/B][U][http://paste.ubuntu.com/9822690](http://paste.ubuntu.com/9822690)
[/U]
Please help me add the windows 7 option to the menu. My work is stuck since many days!!


Thanks & Regards,

prasad :)

---

### Post by Bashing-om on 2015-01-27
prasad13; Hi ! Welcome to the forum .

Try this:
boot to a terminal in 'buntu and execute terminal command:
```

sudo update-grub

```
I do expect the tool 30_os-prober to find Windows boot code and the system to then chainload it onto grub's boot menu .
Reboot to see the effect.

[INDENT][INDENT]ain't 'buntu wonderful
[/INDENT][/INDENT]

---

### Post by prasad13 on 2015-01-27
Tried it...didn't work!

---

### Post by Bashing-om on 2015-01-27
prasad13; Welp;

> **prasad13 said:**
> Tried it...didn't work!
Does not tell us anything and does not help in finding the cause.
What exactly was the result of "update-grub" ?
What is the exact error messages given ?

Maybe what is required is to install Windows Boot code from Windows (??) Then (RE-)install ubuntu's grub ??

Might be best to show us what we are working with :
```

sudo fdisk -lu
sudo parted -l
df -h

```
These will give a more directed response .

[INDENT][INDENT]bios hands off where ?
[/INDENT][/INDENT]

---

### Post by prasad13 on 2015-01-27
i didn't take note of errors during update-grub...but i think it was successful. I ran the command again & the output is like this:
-------------------------------------------------------------------------------------
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-44-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-44-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-44-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-44-lowlatency
Found linux image: /boot/vmlinuz-3.13.0-32-lowlatency
Found initrd image: /boot/initrd.img-3.13.0-32-lowlatency
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
-------------------------------------------------------------------------------------
Also, i have installed ubuntu on 200 gb partition, 8 gb partition was given for swap, & two 134 gb volumes were for windows

sudo fdisk -lu output:
-------------------------------------------------------------------------------------
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xf71899d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   540291072   976771071   218240000   83  Linux
/dev/sda2          206848   262146047   130969600    7  HPFS/NTFS/exFAT
/dev/sda3       262146048   524290047   131072000    7  HPFS/NTFS/exFAT
/dev/sda4       524290048   540291071     8000512   82  Linux swap / Solaris

Partition table entries are not in disk order
-------------------------------------------------------------------------------------

sudo parted -l output:
-------------------------------------------------------------------------------------
Model: ATA WDC WD5000BPVT-7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start  End    Size    Type     File system  Flags
 2      106MB  134GB  134GB   primary  ntfs
 3      134GB  268GB  134GB   primary  ntfs
 4      268GB  277GB  8193MB  primary
 1      277GB  500GB  223GB   primary  ext4         boot
-------------------------------------------------------------------------------------

df -h output:
-------------------------------------------------------------------------------------
Filesystem             Size  Used Avail Use% Mounted on
/dev/sda1              205G   28G  167G  15% /
none                   4.0K     0  4.0K   0% /sys/fs/cgroup
udev                   1.9G  4.0K  1.9G   1% /dev
tmpfs                  387M  1.2M  385M   1% /run
none                   5.0M     0  5.0M   0% /run/lock
none                   1.9G   84K  1.9G   1% /run/shm
none                   100M   32K  100M   1% /run/user
/home/prasad/.Private  205G   28G  167G  15% /home/prasad
-------------------------------------------------------------------------------------

---

### Post by Bashing-om on 2015-01-27
prasad13; Humm ..

Will take someone with greater Window's fu than I posses; but, I think Windows wants to be in that 1st partition where you presently have 'buntu installed.
per:
> 
/dev/sda1 * 540291072 976771071 218240000 83 Linux
/dev/sda1 205G 28G 167G 15% /


Else Window's boot code will not install correctly.

I could be in error
[INDENT][INDENT]Windows is not in my interest
[/INDENT][/INDENT]

---

### Post by prasad13 on 2015-01-27
Oh God :(
Let's see if someone can come up with a solution!
Anyways, Thanks a lot for trying!! :)

---

### Post by Bashing-om on 2015-01-27
prasad13; Hey !

The knowledge base here is astounding. There are a number of peeps here with that knowledge.
Hang loose and let's see who responds .

[INDENT][INDENT]If I knew everything
[INDENT][INDENT][INDENT][INDENT]I would not be me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by LostFarmer on 2015-01-27
Your win7 partition does not show the needed boot file "bootmgr".  I do not know how to fix but a web search for 'missing win7 bootmgr' likely will have some info.

---

### Post by oldfred on 2015-01-27
Windows 7 installs most often have a separate boot partition that has bootmgr & BCD. That is not required, but it looks like you erased the Windows boot partition. You can move boot flag to sda2. Windows has to have boot flag to know which partition to boot, repair or install into. Grub/Ubuntu does not use boot flag. You can use gparted to move boot flag or your Windows repairCD/flash to make active sda2.

Then you need  a Windows repairCD or flash drive and run the standard set of Windows repairs. You cannot add bootmgr nor BCD from any Linux repair tools.

After Windows repairs it will probable also add the Windows boot loader to the MBR. You then can use Boot-Repair to add grub & update grub menu to show Windows.

 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)

---

### Post by Bashing-om on 2015-01-27
@ prasad13; 

See oldfred's directive .

@oldfred, so I stand corrected that it is not imperative that Windows occupy that 1st partition ?
(just so I do not pass invalid advise in the future ) .

[INDENT][INDENT]one of those times I just do not know
[/INDENT][/INDENT]

---

### Post by yancek on 2015-01-27
Generally, windows 'boot' files need to be on a primary partition in order to install properly.  Having a missing bootmgr file and having the Ubuntu partition marked as active rather than the windows partition are likely the major problems here.

---

### Post by prasad13 on 2015-01-28
solved!!
Had to reinstall win7 and run boot repair tool.
the grub has bot ubuntu and windows now!
I had deleted the boot partition windows created before....because i can have max 4 partitions & the extra windows partition was unwanted(for me :p)
so i had deleted that partition...anyways, everythings working now.
Thanks a lot guys! :)

---

### Post by oldfred on 2015-01-28
Windows in BIOS/MBR boot mode only boots from a primary partition formatted NTFS with the boot flag or active partition. It normally is first as most systems are pre-installed. But can be any sda1 thru sda4. But often does not correctly see Linux in the extended partition if installed after the extended and causes issues. So if using an extended partition best to have it after Windows.

---

