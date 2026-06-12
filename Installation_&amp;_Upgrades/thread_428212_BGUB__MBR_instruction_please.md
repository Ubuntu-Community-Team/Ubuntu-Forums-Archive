---
title: "BGUB / MBR instruction please"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by dodjie60 on 2007-04-30
Hello,

This is my first post in this forum. I've been using Linux since 2001 meaning I have and above knowledge regarding installation.

I only need a simple instruction regarding the installation of Ubuntu. Unlike other linux installer like Anaconda and Novell/SuSE/OpenSuSE installer, you have an option on selecting where to put Grub whereas Ubuntu installer (or the one I downloaded) did not have this option. It just suddenly installed grub to the MBR without any choice,  which is not the way I liked. I've been using this 
[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/How_to_Dual_boot_with_XP_2000_NT_and_install_linux_windows_whenever_You_want]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/How_to_Dual_boot_with_XP_2000_NT_and_install_linux_windows_whenever_You_want")

instruction and had been very helpful ever since. 

The problem is this:

NOTE THAT I DON'T HAVE WIN XP INSTALLATION CP. WINDOWS XP WAS REINSTALLED IN MY PC.

- How do I revert back to changing my boot loader to boot.ini of win xp. Note that GRUB messed up my MBR and am now using GRUB from my OpenSuse 10.2 which is also included in my Laptop. I am doing a triple boot with this machine (WinXP, Fedora Core 7 and OpenSuse 10.2)

What I did temporarily while waiting for a solution to this problem was to install GRUB to boot my machine first and revert back to whatever instruction could be found here.

I know that this problem had been asked a hundred times before but my case is different. Triple booting using _dd if=/dev/hdaN of=/mnt/windowsdrive/bootsect.lnx bs=512 count=1_ to capture bootloader in / or /boot using win xp boot.ini.

Please help.

Only noticed now, the title of this thread should be GRUB / MBR instruction pleas. 

-

---

### Post by dodjie60 on 2007-04-30
And one more thing, Ubuntu installation messed up my partition. :) 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2098    16851208+   7  HPFS/NTFS
**Partition 1 does not end on cylinder boundary.**
/dev/sda2            2098        4345    18049028    f  W95 Ext'd (LBA)
/dev/sda3            4346        4864     4165560   12  Compaq diagnostics
**Partition 3 does not end on cylinder boundary.**
/dev/sda5            2099        2863     6144862+   7  HPFS/NTFS
/dev/sda6            2877        2942      530113+  82  Linux swap / Solaris
/dev/sda7            2943        3729     6321546   83  Linux
/dev/sda8            3730        4345     4947988+  83  Linux

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3264    26218048+   7  HPFS/NTFS
/dev/sdb2            3296        4864    12602992+   f  W95 Ext'd (LBA)
/dev/sdb3            3265        3295      249007+  82  Linux swap / Solaris
/dev/sdb5            3590        4864    10241406    b  W95 FAT32
/dev/sdb6            3296        3589     2361492   83  Linux

---

### Post by undecidable on 2007-04-30
1.  The graphical installer is non-obvious.  During install of grub there was an 'advanced' box, which if you clicked got you to a screen that said: install grub to (hd0) which you needed to change to (hd0,x) where x is the linux partition you wanted to install grub to.  I think it is easier to use the alternate installer when you have multiple partitions, the graphical installer is a bit restrictive and non-obvious in this area.

2.  boot.ini is the Windows equivalent of grubs /boot/grub/menu.lst.  Whatever you have as the bootloader in the mbr will pass control to ntldr in the W partiton which uses boot.ini to decide where to go next.  

3.  That being said, I am not sure I understand what the problem is.  If grub is in the mbr, it  can pass control to the W partition which will then run ntldr which will then use boot.ini.

4.  However if really want to use the Windows MBR loader, it can be restored with (from Windows)
fdisk /mbr
This will then pass control to ntldr in the W partition which will read boot.ini which you must modfiy to get it to boot your lx partition.

Hope this helps.
MC

---

### Post by dodjie60 on 2007-04-30
Sorry about this win xp. I already forgot that I can restore MBR through this. I've stopped using win xp since time forgotten and I have to retain it in my laptop for FIS (accounting software which I use for auditing clients) purposes.

Second, I need to use MBR boot.ini for the reason that I am using an IBM Thinkpad T43 with an option in booting to Access IBM troubleshooting. I can't access it using GRUB.

Anyways, thanks for this advice.

Never mind about my second (actually my bump post) regarding the fdisk -l. I can repair this, I was just informing the readers that Ubuntu installer screwed my partition big time. 

And third, thanks again for reminding me that I have a WinXP in my laptop, haven't used it for a long time that I forgot it is installed (seriously).

---

### Post by undecidable on 2007-04-30
1.  "re: I was just informing the readers that Ubuntu installer screwed my partition big time."
Someone else can confirm this, 
but I believe that:
Partition 1 does not end on cylinder boundary
is not critical, not even important.
(for reference see [http://tldp.org/HOWTO/Large-Disk-HOWTO-6.html](http://tldp.org/HOWTO/Large-Disk-HOWTO-6.html))

I used to frequently received this msg in PMagic with no ill effects on my health.  

2.  fdisk /mbr can also be done from a DOS boot disk if you don't have W installed.

3.  if you can access the Access IBM troubleshooting partition from ntldr/boot.ini
you can do so from grub.  
Dells also have a maintenance partiton - the Dell's is a fat partition with a 12 code instead of 16
though all you actually need to do is put an entry in /boot/grub/menu.lst for it,
similar to the one for W  (ie noverify, chainloader+1 etc).

---

### Post by dodjie60 on 2007-04-30
Yes, actually, in that particular setup I showed with fdisk -l, I haven't yet connected my USB HDD containing my Fedora core. Such setup shows only WinXP, OpenSuSE 10.2 and Ubuntu (which I am using now in writing this message). :) 

I already solved these problems including the partition. dd really helped a lot.

My main problem now (actually not a problem) is inserting these lines in my new GRUB Bootloader.

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e0568e7b-4817-4926-a851-d81bed301385 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

I'm still searching around on how to reinstall grub in my /boot and probably point it in my boot.ini.

---

