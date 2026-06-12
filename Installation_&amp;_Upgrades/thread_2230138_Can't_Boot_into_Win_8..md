---
title: "Can't Boot into Win 8."
date: 2014-06-17
forum: Installation &amp; Upgrades
---

### Post by wolfxshadows on 2014-06-17
So my friend told me to try out Ubuntu so I looked at it and installed it... problem being now I can't boot into my Win 8 any longer. I've been searching and searching and can't seem to find anything that works. I've tried boot-repair and got this: [http://paste.ubuntu.com/7656773/](http://paste.ubuntu.com/7656773/) not sure what I can do. Please help, I really need my Windows to load - I'm a streamer and can't play 80% of my games now because they're not supported on Linux. I just want to dual - boot. please tell me there's a way to fix this.

---

### Post by yancek on 2014-06-17
Do you remember which installation option you selected during the Ubuntu install?  It looks to me like you used Erase and use entire disk as there is no sign of any windows partition on the 1TB drive except for the FAT32 boot partition, sda1.  You also used LVM with Ubuntu.  Did you intend to do that?  The only other dirve I see in your output is the 4GB flash drive which is what you used to install Ubuntu, correct?  Are you able to actually boot Ubuntu without the flash drive?  Since you have windows code in the mbr of the first drive, I would not think you would.  It looks like you have overwritten your windows 8.

---

### Post by oldfred on 2014-06-17
Did you make a recovery set of DVDs from the vendor recovery partition?
Did you backup Windows?

If not your only recourse is to see if your system vendor offers replacement recovery set of DVDs. Some offer them for just a nominal charge, others do not offer anything.
One user had just purchased from a local store and they still sold same model, so tech in store made a full DVD recovery set.
A recovery set is not a full Windows installer, but just an image of your hard drive as purchased. All your data is gone.
The Windows product key is in the UEFI. And that key only works with the vendor version.
 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

Otherwise you have to purchase another full copy of Windows.

LVM install or LVM install with encryption has always been a full drive install which erases everything. The install instructions should make that clear, but since that is how it has always worked and how it is supposed to work, they do not consider it a bug.

---

### Post by wolfxshadows on 2014-06-17
It doesn't even HAVE a 1TB hard drive. So I have no idea what that is even about... and I didn't choose to install it over windows, pretty sure I chose to put it along side it. And I have the USB with the windows I purchased on it, but it came with Windows 8 pre-installed. Thanks anyways.

---

### Post by yancek on 2014-06-17
[QUOTE and I didn't choose to install it over windows, pretty sure I chose to put it along side it][/QUOTE]

Did you read the post by oldfred above?  

> LVM install or LVM install with encryption has always been a full drive  install which erases everything. The install instructions should make  that clear, but since that is how it has always worked and how it is  supposed to work, they do not consider it a bug. 		

Your bootinfoscript clearly shows LVM.  If you don't have a 1TB drive, what do you have?

---

### Post by fantab on 2014-06-17
> **wolfxshadows said:**
> It doesn't even HAVE a 1TB hard drive. So I have no idea what that is even about... and I didn't choose to install it over windows, pretty sure I chose to put it along side it. And I have the USB with the windows I purchased on it, but it came with Windows 8 pre-installed. Thanks anyways.

The following 'parted -l' shows that you have a 1000Gb HDD:
[QUOTE=paste.ubuntu.com/7656773/]parted -l:

Model: ATA WDC WD10JPVT-55A (scsi)
**Disk /dev/sda: 1000GB**
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size   File system  Name                  Flags
1      1049kB  538MB   537MB  fat32        EFI System Partition  boot
2      538MB   794MB   256MB  ext2
3      794MB   1000GB  999GB  [/QUOTE]

Even though you correctly chose to "install Alongside Windows' option, YOU also chose [LVM]("https://wiki.ubuntu.com/Lvm") as your filesystem, which like oldfred points out:
[QUOTE=oldfred]LVM install or LVM install with encryption has always been a full drive  install which erases everything. 
The install instructions should make  that clear, but since that is how it has always worked and how it is  supposed to work, they do not consider it a bug.[/QUOTE]
You should have used EXT4 filesystem instead, which is the default in most of the linux distros (Fedora uses LVM as default).

Right now, there is NO windows there... it has been erased.

[QUOTE=wolfxshadows]I have the USB with the windows I purchased on it, but it came with Windows 8 pre-installed.[/QUOTE]

You can re-install Windows and Ubuntu after reformatting your HDD...
Use any good Windows Disk management tool or use [gparted]("http://www.dedoimedo.com/computers/gparted.html"). You must make a new GUID Partition Table [GPT]
Install Windows first (in UEFI mode): [http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Then install Ubuntu.

---

