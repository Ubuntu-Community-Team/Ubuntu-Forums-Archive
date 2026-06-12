---
title: "Machine boots into GRUB / how to remove GRUB?"
date: 2015-05-25
forum: Installation &amp; Upgrades
---

### Post by xinelo on 2015-05-25
Hi there, 

Using a live session from a USB pendrive I've tried to perform a ful installation Ubuntu in another USB drive but in my first trials I think I was writing to the hard disk. It wouldn't install but it seems it has messed the boot sector of  the machine. 

Now when I start the machine, the first thing I see is grub: 

```
Minimal BASH-like line editing is supported. For the first word,  TAB lists possible command completions. Anywhere else TAB lists possible device or file completions. 

grub>
```

I have run boot-repair but the option to fix MBR was not available. The report says that no errors were found but nothing has changed in the way the machine starts.

Here boot-repair's report: [http://paste.ubuntu.com/11345059/](http://paste.ubuntu.com/11345059/)

I have also run the Windows recovery pendrive I have, and have tried bootrec, bcd options, etc. and nothing works. 

I can now run Ubuntu from the installation I did in the pendrive, but not Windows (the machine always boots into GRUB). I guess what I need to do is to remove GRUB and restore or fix Windows' MBR or UEFI or BIOS (not sure). It runs Windows 8.1

Any help would be greatly appreciated. Thanks in advance!

Cheers, Manuel

---

### Post by oldfred on 2015-05-25
Try typing exit at grub>, it should then boot.
You should also go into UEFI and reset Windows as firstin UEFI boot menu choice.
You can also do that with efibootmgr from Ubuntu live installer.

Did you have the drive you installed Ubuntu into, plugged in when you ran Summary Report? I only see two drives 128GB &  8GB?

Grub does just install to sda. I installed a second Ubuntu to my sdb internal drive and explicitly told it to install to sdb. Watching install carefully it even said installing to sdb, but it overwrote the grub in my main working install in sda.

But with UEFI, the folder in the efi partition is all you need for internal drives. You can just copy the /EFI/Ubuntu folder to the other drive.

If an external USB drive, those only boot from /EFI/Boot/bootx64.efi. So we still have to copy all of the /EFI/ubuntu folder but then copy grubx64.efi or shimx64.efi to the /EFI/Boot folder and rename one or the other to bootx64.efi. Shim version is grub for secure boot, and now it seems to work whether secure boot is on or off, so most copy shim.

See also info and links in link below for more UEFI info.

---

### Post by xinelo on 2015-05-25
Thank you so much, oldfred.

> **oldfred said:**
> Try typing exit at grub>, it should then boot.

Yes! This works. I can boot into Windows. 

> **oldfred said:**
> You should also go into UEFI and reset Windows as firstin UEFI boot menu choice.
You can also do that with efibootmgr from Ubuntu live installer.

Reset Windows as the first and ONLY boot menu choice is exactly what I want to do. 

I don't know what you mean by "go into UEFI". 

I have the command efibootmgr in a live Ubuntu session from a pendrive, but I don't know hwo to use it. I had a look at the man page but there are many things I can do with it. As I don't know waht the problem is exactly, I don't know how which option I must use. 

In any case, whichever path I take, could you please provide some steps as to how to proceed, or at least some tip about what exactly I must do? 

> **oldfred said:**
> Did you have the drive you installed Ubuntu into, plugged in when you ran Summary Report? I only see two drives 128GB &  8GB?

No, probably I didn't. Those two drives you see are the two partitions in the hard drive. The big one has Windows and the smaller one is a OEM partition put there by Toshiba. 

Thank you very much.
Cheers, Manuel

---

### Post by xinelo on 2015-05-25
In case this helps:

ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0004,0008,0003,0005,0007,0006
Boot0000* HDD1	BIOS(2,0,10).......................................................................
Boot0001* USB MEM	BIOS(2,0,10)............................ ..........................................
Boot0002* LAN1	BIOS(80,0,10)........................G..............................................
Boot0003* Windows Boot Manager	HD(2,200800,32000,f1111636-d417-11e3-9583-b86b23e30978)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0004* USB Memory	ACPI(a0341d0,0)PCI(14,0)USB(0,0)
Boot0005* HDD/SSD	ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000
Boot0006* LAN2	ACPI(a0341d0,0)PCI(19,0)MAC(b86b23e30978,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0
Boot0007* LAN1	ACPI(a0341d0,0)PCI(19,0)MAC(b86b23e30978,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000
Boot0008* ubuntu	HD(2,200800,32000,f1111636-d417-11e3-9583-b86b23e30978)File(\EFI\ubuntu\shimx64.efi)
ubuntu@ubuntu:~$

---

### Post by oldfred on 2015-05-25
You should be able to get into UEFI settings directly as you start to boot with whatever key your system uses. Just about every vendor is different, but often del, escape, f2 and sometimes combinations as HP uses escape then f10.

 You would first type sudo efibootmgr -v to get a list of boot options. Note the number associated with the Ubuntu entry -- for instance, it might be Boot0005. You'd then type sudo efibootmgr -o 5 to make "Ubuntu" (actually GRUB) the default boot loader. (You can specify a set of boot loaders to be tried in order, as in sudo efibootmgr -o 5,1,2 to use 5, then 1 if that fails, then 2 if both 5 and 1 fail.)

        change the BootOrder variable with efibootmgr's -o option
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)

Looks like you want 
efibootmgr -o 3,5
And maybe some of the others?

---

### Post by xinelo on 2015-05-25
Thanks, oldfred.

The issue seems fixed with your tips to use efibootmgr. 

A few comments about the UEFI...

> **oldfred said:**
> You should be able to get into UEFI settings directly as you start to boot with whatever key your system uses. Just about every vendor is different, but often del, escape, f2 and sometimes combinations as HP uses escape then f10.

With F2 I can access so-called TOSHIBA Setup Utility, where I can tweak Secury, Power and Advanced options. In Advanced, System Configuration I have Boot Mode, where I can switch between UEFI boot and CSM boot (which seemed to prevent booting at all). 

Then with F12 I can boot from the Windows recovery USB stick, the contents of which were out-of-the-box in another 8GB partition, and I moved it out to release drive space. Witg F12 I can access this blue screen where I can access Troubleshooting, then Restore PC, Reset PC, Advanced options like use a restoration point, retrive system image, boot/start repair, command line and Firmware UEFI firmware setup. I tried all relevant options from there but none fixed my grub issue. 

> **oldfred said:**
> You can specify a set of boot loaders to be tried in order, as in sudo efibootmgr -o 5,1,2

I had seen this option, but a) I didn't want to go ahead without confiming with someone first, and b) I thought all relevant drives where already included in the BootOrder: 0004,0008,0003,0005,0007,0006.

I have done: 

```
efibootmgr -o 4,3,5
```

Now it seems to boot fine, it does not stop in that grub prompt, and it boots into windows 8 as normal. 

However, now I can't boot from the pendrive, which means I can't launch Ubuntu live... (despite the fact that number 4 --USB Memory-- is the first boot choice). Any tips about that? 

Thansk a lot!
Cheers, Manuel

---

### Post by oldfred on 2015-05-25
Either f12 or f2 and the boot tab should show two options for the USB. One is just the name and that is the old BIOS boot. The other should show UEFI and the name/label of flash drive if flash drive is configured as a bootable device.
If you turn secure boot on, only secure boot options are shown. And many systems seem to need UEFI setting changed to allow UEFI boot of an external drive. 
You should also have tabs, or entries for devices like hard drive or flash drive and then also have UEFI boot options, which may be in same place, or a submenu or even on a different page/tab of the UEFI.

---

### Post by xinelo on 2015-05-25
> **oldfred said:**
> Either f12 or f2 and the boot tab should show two options for the USB. One is just the name and that is the old BIOS boot. The other should show UEFI and the name/label of flash drive if flash drive is configured as a bootable device.

Yes, I noticed that. I have: 

Boot0001* USB MEM	BIOS(2,0,10)............................ ..........................................
Boot0004* USB Memory	ACPI(a0341d0,0)PCI(14,0)USB(0,0)

so I think I used the right one.

I'll explore the UEFI more tomorrow, and will check the secure boot thing. 

Thanks again for all your great help! 
Cheers, Manuel

---

### Post by xinelo on 2015-05-27
Hi there again, 

I tried with another pendrive and I can boot from it, there I conclude that the boot order in the UEFI works fine. There must be something wrong with the USB stick that I was trying to boot, where Ubuntu is fully installed. I'll look into that, but that's another topic. 

Thanks again for your help!
Cheers, Manuel

---

### Post by xinelo on 2015-05-29
Hi again, 

I could boot from my Kingston 8Gb pendrive (ubuntu live) but I could not boot from my Qilive 32Gb one (ubuntu full installation), therefore I concluded that the Qilive one was not bootable, for some reason. I didn't know how to make it bootable, so I installed the whole thing again on it. 

I could boot from the Qilive pendrive yesterday and spent the whole day working on it. Today I tried to boot into Windows and I got the Grub screen again. The boot order given by efibootmgr seems fine but I fixed it again in the same way: efibootmgr -o 4,3,5. I can boot into Windows fine again now, but not from the Qilive pendrive.

In case it helps, at the moment the volumes I can see from Gparted run in the live session are:
/dev/mmcblk0 1.90 GiB (SD Card)
/dev/sda (119.24 GiB) Windows
/dev/sdb 28.88 GiB the Qilive pendrive that doesn't boot
/dev/sdc 7.46 GiB the Kingston pendrive (ubuntu live), the one that boots

I don't understand what's going on. I would appreciate some help. How can I make my Qilive pendrive bootable? Is it in the pendrive itself or in the machine's boot sector/UEFI/MBR/Bios/whatever?

Thanks in advance.

Cheers, Manuel

---

### Post by xinelo on 2015-05-29
I noticed that the pendrive I can boot from is formatted as FAT32, whereas the partition where Ubuntu is installed in the USB pendrive I can't boot is formatted as ext4. I believe this is the default format used by the installer, but could it be that this is the reason for not being bootable? 

If yes, however, I wonder how I could boot from it yesterday, at least once. 

Cheers, Manuel

---

### Post by oldfred on 2015-05-29
My full install in a sdb drive I formatted in advance. And I told grub to install to the internal sdb. And watching closely it flashed by a command that said it was installing to sdb.
But it installed to sda. :( 
I also installed to a flash drive.
And grub/Ubuntu in both cases overwrite my working install's efi in sda. So if you have Ubuntu in sda, be sure to back it up first.

Do you have an efi partition on your flash drive. If not you will need to partition in advance and create one. If on flash drive 100MB should be plenty. For hard drives I normally suggest 300MB just in case in future we start doing additional things in UEFI.

But the only difference is a tiny grub.cfg in /EFI/Ubuntu that is a configfile that passes control to the real grub.cfg in the install.

But with USB or external drives UEFI only boots from /EFI/Boot/bootx64.efi.
I cheated and just copied my full install of grub in /EFI/ubuntu to my efi partition on the flash drive and copied grub to /EFI/boot and renamed it bootx64.efi. If using secure boot use shimx64.efi. But you still must have the grub.cfg in the /EFI/ubuntu folder or it will not work.
My grub.cfg in /EFI/ubuntu UUID & root specification must be your device. I now notice my hd2,gpt2 is probably wrong, Boot drive is always hd0, but UUID is correct so it still works.
```
search.fs_uuid c9aa0b01-e786-4b17-930a-fa6bedc785d2 root hd2,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

My 64GB flash or why I labelled as efi64 & System64 from parted:
```
Disk /dev/sdb: 62.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name      Flags
 1      1049kB  525MB   524MB   fat32        efi64     boot, hidden
 2      525MB   22.5GB  22.0GB  ext4         System64
 3      22.5GB  62.0GB  39.4GB  ext4

```
From gdisk:
```
Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1025484   499.7 MiB   EF00  efi64
   2         1026048        44033860   20.5 GiB    8300  System64
   3        44034048       120997887   36.7 GiB    8300  


```

---

### Post by xinelo on 2015-05-29
Hi oldfred, 

While you were writing your last answer I tried the following, following instructions here: [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_UEFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_UEFI_mode)

In boot repair, GRUB location (second tab), I selected

OS to boot by default: sdb2 (Ubuntu 14.04.02 LTS) <-- the ext4 partition in the pendrive
Separate /boot/efi partition: sdb1 <-- the 200MB partition in the pendrive 

Now it boots fine and GRUB shows the following options: 

Ubuntu
Advanced options for Ubuntu
EFI/ubuntu/MokManager.efi
Windows UEFI bootmgfw.efi
Windows Boot UEFI loader		-> 5
EFI/ubuntu/MokManager.efi sda2
EFI/Toshiba/Boot/bootmgfw.efi
System setup

Only the first two options work, leading to Ubuntu startup. System setup gives `unable to find command "fwsetup"` and all the other options give something like  

/EndEntire
file path: /ACPI .... 
erro: cannot load image
Press any key to continue

Not very neat. That's not a problem, because I can boot into Windows by just ejecting the USB pendrive. 

I also tried select sda2 for Separate /boot/efi partition, but then the GRUB dead screen appears again. I also noticed that before there was an option "Restore MBR" that is now gone. I don't know how bad that is or what it means, but I just noticed.

Thanks a lot. I'll look into your answer any way.

Cheers, Manuel

---

