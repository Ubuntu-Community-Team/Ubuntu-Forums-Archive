---
title: "slight grub problem with boot on windows 8 machine/Ubuntu on external usb drive"
date: 2013-11-27
forum: Installation &amp; Upgrades
---

### Post by annieg on 2013-11-27
Sorry if this has already been asked here, my searches so far haven't led to an answer specific to my problem. I'm a technically competent but cautious newbie: just successfully used a liveUsb to install ubuntu desktop to a 500 GB usb3 drive connected to my windows 8 samsung. Everything is great (I love ubunutu!), windows still works and I can select the ubuntu drive by hitting F10 on startup, but I was hoping I could set the boot sequence to try the ext. drive first and then when it's not connected windows 8 would just come up. However, if I switch the boot sequence, when I unplug the ext. drive I get a grub rescue prompt, leading me to suspect that grub got installed to the samsung internal drive MBR instead of the ext usb drive. Does this sound like what happened? If this is the case, how do I fix it? I'm very leery about poking around in my windows boot sector... Also, having read about uefi problems, I disabled it in the samsung before the install, but am wondering if I needed to, and/or if I can safely re-enable it.

Thanks!

---

### Post by oldfred on 2013-11-27
If Windows is UEFI which all pre-installed systems are, you needed to install Ubuntu in UEFI mode. And then external drive needed to be gpt partitioned and have its own efi partition at beginning of drive.
Did you just do a default install. That normally installs grub to sda. And how you boot installer, UEFI mode or BIOS mode is how it installs.
You can move a BIOS boot of Ubuntu, so it only boots from external drive, and UEFI from Internal, but you will have to manually turn on/off UEFI mode. A few newer ones may auto switch but you still have to boot from UEFI or maybe one time boot key. 
Once you start to boot in one mode you cannot change, so grub menu only works when both are installed in same boot mode.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by annieg on 2013-11-27
Thanks, I think I understand...
re:
> If Windows is UEFI which all pre-installed systems are, you needed to  install Ubuntu in UEFI mode. And then external drive needed to be gpt  partitioned and have its own efi partition at beginning of drive.

As I said, I had disabled UEFI and it remains disabled - Ubuntu boots fine, windows boots fine and I'm not sure I care about UEFI enough to do complete reinstall, tho maybe that's the way to go. But if UEFI was, and remains, off, I don't see that it should have any impact on the grub rescue issue. That issue *only* exists if I want to start windows by simply setting the boot sequence to hit the external drive first, but unplug the ext. drive before booting. It seems my grub problem should have nothing to do with UEFI and probably arose from doing a 'default' install such that grub installed to sda instead of sdb. My question is, can/should I move it, and if so, how.

The thing about UEFI was/is a secondary question - is it important enough to redo the whole thing, or can I just leave it off and simply try to fix the grub location? I keep pretty good computer hygiene.

I appreciate your help.

---

### Post by oldfred on 2013-11-27
Can say without more info on your configuration. Post link to BootInfo report.
Some systems auto switch, so even with UEFI off, you may be booting Windows in UEFI mode as that is the only way it boots from a gpt partitioned drive. If you installed Windows 8 yourself, it could be in BIOS with MBR partitions. BootInfo will show all that.

---

### Post by annieg on 2013-11-29
Finally done with Turkey cleanup, here's the link: [http://paste.ubuntu.com/6497099/](http://paste.ubuntu.com/6497099/)
I have not tried to inspect it too closely yet myself, have to wait till the excess food wears off and my brain starts to function again

---

### Post by oldfred on 2013-11-29
You have Windows in UEFI on sda with gpt partitioning.
You have Ubuntu in sdb booting with BIOS mode and MBR(msdos) partitioning. (But grub is missing in MBR)
With the installs in different modes you can only dual boot from UEFI/BIOS menu and may have to change settings in UEFI to turn on UEFI or turn off CSM/Legacy/BIOS boot modes. Some do auto switch.
But to boot Ubuntu in BIOS mode you need grub installed to the MBR of sdb. Do not do auto repair with Boot-Repair as it either wants to try to convert to UEFI which will not work with MBR partitioning or will install grub to the MBR of every drive.
You need to boot Boot-Repair in BIOS mode, not UEFI mode and uncheck auto repair and in advanced choose to install grub to MBR of sdb with install in sdb5 and check /boot is in sda1.

Windows only boots from gpt partitioned drives with UEFI.
Both Windows and Ubuntu only boot from MBR partitioned drives with BIOS boot mode.
But Ubuntu will boot in BIOS or UEFI from gpt partitioned drives.
So I normally suggest if a drive will not have Windows to always use gpt partitioning as you can have BIOS or UEFI or convert if you have correct partitions. You should always have an efi partition as the first partition on every gpt drive. Then you could later install a system without major reorganization even if initially not planning on making the drive a bootable drive.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by annieg on 2013-11-30
Thanks for the detailed analysis. Guess the first lesson is to start with a more up-to-date tutorial! Since I have not spent any time yet on config or set-up of the ubuntu install, perhaps the best option would just be to start over. 
[LIST=1]
[*]Assuming I should start by turning UEFI back on in Windows boot setup?
[*]I used gparted to set up the usb3 drive after booting off the liveUsb - is that the recommended way to go second time around, following the guidelines from [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) to reformat the drive?
[*]Given the above (changes from my first attempt), is it straightforward to proceed with the default install from liveUsb, or will I need to change advanced settings?
[/LIST]

Sorry for needing so much hand-holding, I really appreciate the continuing help - normally I'd be a bit more adventurous but my old laptop is dying and I can't afford to screw the new one up right now.

---

### Post by oldfred on 2013-11-30
If starting over I highly recommend gpt partitioning on your sdb and any future drives. Better compatiblity with UEFI. And Ubuntu then can be configured to boot either UEFI or BIOS boot modes.

If partitioning in advance.:
       I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

How you boot install media is how it installs. So if you want UEFI on sdb, you will need to boot installer in UEFI mode.
With two drives, I am not sure any of the auto install methods will work correctly. I prefer manual install and partitioning in advance. But with Something Else or manual install you still have to click on change to tell it which partition is / (root) and its format, which is /home if that is separate. If you have swap already create it will find it or you have to tell it which is swap. Swap has no format.

I like having an efi partition on every gpt drive, so you can install boot loader to that partition. Then each drive can boot without the other. You can also install grub/ubuntu boot loaders to the efi partition on the Windows drive as now with UEFI multiple boot loaders co-exist as separate folders in the efi partition. Installing a boot loader does not overwrite the previous boot loader as with BIOS/MBR as there is only one MBR per drive.

---

