---
title: "Dual Boot Win2k, Kubuntu 6.06"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by NevrGivUp on 2007-02-18
Hi,  I would like to thank you in advance for reading this and for any assistance you may provide me.

I just got a 160gb Seagate Barracuda Ultra ATA/100 and I am failing at setting up a Win2K, Kubuntu 6.06 dual-boot.  I've never done this before...I had set up a straight Kubuntu install but didn't have drivers that NDIS wrapper could use for my WLAN device, so I went back to Win2K.  Well, while I was blowing money on a new HD (my old one was 12.7gb) I  ordered a WLAN device natively supported by Kubuntu, so I decided to give this a try.

I installed Win2K, upgraded it to SP4, and applied the fix that came with the drive to let SP4 access larger drives.

Then I install Kubuntu, during this install it tells me that the FAT32 partition I made is somehow messed up (but it was working fine when I was installing Win2K).  So the Kubuntu install finishes and I reboot.

The first two times I tried this when grub comes up, I picked Win2K but Win2K failed  Something about not being able to access the boot device.  The third time I got grub error 18 (Selected cylinder exceeds maximum supported by BIOS).

I partitioned my HD as follows:
32gb FAT32 (for Win2K)
80gb Ext3 (Media Storage, game patches, music, etc.)
36gb Ext3 (this is where I put Kubuntu)
01gb Ext3 (swap)

So, can anyone more experienced than me give me advice?

Thanks

Bryce

---

### Post by logos34 on 2007-02-18
> I installed Win2K, upgraded it to SP4, and applied the fix that came with the drive to let SP4 access larger drives.

Then I install Kubuntu, during this install it tells me that the FAT32 partition I made is somehow messed up (but it was working fine when I was installing Win2K). So the Kubuntu install finishes and I reboot.

The first two times I tried this when grub comes up, I picked Win2K but Win2K failed Something about not being able to access the boot device. The third time I got grub error 18 (Selected cylinder exceeds maximum supported by BIOS).

So are you able to able to boot into Kubuntu?

Some things to try:
-update the BIOS (you've probably already done this)
-Go into the BIOS and make sure hard disk detection is set for 'Auto', or set for 'User' and enable LBA/Logical Block addressing (not CHS)
-Get [SuperGrub CD]("http://supergrub.forjamari.linex.org/") and try to boot with that
-Download [SystemRescueCD]("http://www.sysresccd.org/Main_Page") and run **TestDisk** to fix any errors in the partition table 
-reinstall Grub to MBR using this procedure:
* Boot from the ubuntu livecd and load the desktop.  Open a terminal and type:
> * **sudo grub**
* at the grub prompt, type **find /boot/grub/stage2**
* based on your post, it should return '(hd0,2)'  -->assuming that / is hda3
* type **root (hd0,2)**. 
* type **setup (hd0)**
* now exit with **quit **

---

