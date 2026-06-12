---
title: "Dual Booting (Win 7 &amp; 10.10)"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by Rainman5419 on 2012-05-01
Ok Ubuntu noob here. I was doing a fresh Win7 install so I thought I'd take the opportunity to borrow a roommate's Ubuntu 10.10 disk(upgrade to 11.4 after the install) and give it a try.

The setup I'm trying to achieve is here

SSD1(Win7 OS is currently installed)
SSD2(Used for Win7 apps)
HDD1_Partition1(Media, ideally mounted so Ubuntu can access it as well)
HDD1_Partition2(Ubuntu will live here)

All of the guides I've seen so far are for a single drive setup using MBR. Two questions pop up before I dive into this. Firstly, having the drives formatted for GPT over MBR won't complicate the process, will it? Secondly, how will I go about installing GRUB on SSD1 with Win7 to maintain the boot speed there while using the ext4 partition I've created on HDD1 for Ubuntu?

---

### Post by mörgæs on 2012-05-01
I recommend installing 11.10 or 12.04. There are only disadvantages when beginning with 10.10 and upgrading.

---

### Post by oldfred on 2012-05-01
Having the grub2 boot loader on the SSD will not speed booting as that is just a boot loader, all the grub, kernel & system files are in the main install on your rotating drive. Generally it is better to have boot loader & system on same drive, or each drive fully can boot without other drives, so when a drive fails you can full boot from the other.

Is drive gpt now? If so you need a bios_grub if booting in BIOS mode or an efi partition if booting in UEFI mode. Windows will not boot from gpt unless in UEFI mode, but Windows 7 (not XP) will read NTFS partitions in a gpt drive.

You have to use manual install or Something else to have the choice on which drive's MBR to install the grub2 boot loader.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by Rainman5419 on 2012-05-01
All the drives are currently GPT, and I'm using UEFI mode. I suppose with your suggestion that there is no difference I'll install GRUB on HDD1 then.

I will use Mörgæs' advice and download 12.4 for initial install as well.

---

### Post by oldfred on 2012-05-01
If it is UEFI, can you install the boot loader the the same efi partition as your Window, so you can dual boot from one. I might add it to both the SSD & to an efi partition on the rotating drive just so the rotating drive could boot on its own.

I have seen posts on how to add an old fashioned chainload entry with grub and UEFI.

---

### Post by Rainman5419 on 2012-05-02
Thanks for the direction and help guys.

---

