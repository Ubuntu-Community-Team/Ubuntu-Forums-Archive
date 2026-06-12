---
title: "Can't Live Boot from SanDisk USB"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by vancinas on 2012-12-22
Okay, I've got a problem with a couple of SanDisk Cruzer flash drives. I'm trying to live boot Ubuntu Studio. On one of the drives, neither Ubuntu's startup disk creator nor Unetbootin was able to load the ISO. Startup disk creator would just fail towards the end of the procedure (command line said something about a segmentation fault). Thinking that one was simply a bad disk, I tried the other. This time startup disk creator managed to finish it's work without any problem, but I have been unable to boot from the flash drive. I set the USB as the primary boot device, but the computer still keeps starting my native version of Ubuntu instead of the one that's on the flash disk.

I heard that some people had problems with SanDisk's u3-launchpad software that's installed on the drives. I quick-formatted both of the drives, and even formatted the first drive with a complete overwrite, but they still don't work. SanDisk's u3 removal tool does not recognize the drives anymore, I think due to the formatting, so can't use that. u3-tool doesn't work either. Does anybody have any idea what the problem with these flash drives might be, and how I might be able to fix them? Thanks in advance.

---

### Post by bogan on 2012-12-22
Hi!, **vancinas**,

Your description is not clear as to whether you installed Ubuntu directly to the Sandisks, or burnt the Iso to it.

I did a direct install. I do not know if this will apply to your Sandisk Cruzer flash drives, after what you have done to them.

I have 12.10 booting, & running, OK on an 8Gb Sandisk  with a 1GB ntfs first partition - so Windows will recognize it, and for mutual access Switch files - 6Gb for Ubuntu and 1Gb as a swap file.  I created the Switch partition in Windows, and then created and formatted the rest in Gparted, without difficulty..

I originally installed 12.04 on it, directly from a LiveCd, later upgrading to 12.10.
 It has its own Grub so I can boot to it, either from its own Grub Menu, after selecting it in the Bios boot menu, or  from the HDD Grub menu. Thus it is independent and mobile.

My Bios does not permit making an USB the default primary boot device, as it sees an USB as a hard drive, and I have to run down the drop down menu to select it.

The only problem I have had was from shortage of space after multiple kernel updates; I had to delete some old kernels to make room to install Ubuntu Tweak to clear out the crud.
Chao!, **bogan.**

---

