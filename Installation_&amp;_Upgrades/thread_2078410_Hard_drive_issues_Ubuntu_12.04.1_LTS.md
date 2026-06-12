---
title: "Hard drive issues Ubuntu 12.04.1 LTS"
date: 2012-10-30
forum: Installation &amp; Upgrades
---

### Post by Mr SMS on 2012-10-30
Hi,

I'm completely new to Ubuntu, and I have a question concerning hard drives.

My internal hard drive is badly damaged and will not operate correctly. Will I require an internal hard drive, or will the external hard drive plugged into my computer suffice for installing Ubuntu?

---

### Post by zeroseven0183 on 2012-10-30
Yes, it's possible to install Ubuntu on an external hard drive (see documentation for Installation  [https://help.ubuntu.com/community/Installation#Installing_on_external_or_RAID_hard_disks](https://help.ubuntu.com/community/Installation#Installing_on_external_or_RAID_hard_disks)), although I would prefer getting an internal hard drive instead especially if you're using a laptop.

---

### Post by Mr SMS on 2012-10-30
Thank you for the link, but unfortunately, I do not understand what I'm supposed to do here. I followed the instructs for properly downloading Ubuntu to my external hard drive, but the computer wont load from it, instead it tries to load from the internal hard drive, which is damaged, prompting the computer to say

"Insert proper boot media".

Plus the instructions appear to be for Macs. The only other OS I've used up until now is Windows

I put in my Ubuntu disk and it loads the trial version of Ubuntu fine (all preferences are deleted when the computer is shut down).

So I'm not sure what I should do from here.

I think the external hard drive is missing the "grub" or something that tells my laptop to look in the external as opposed to the broken internal.

---

### Post by oldfred on 2012-10-30
If you have installed to your external download Boot-Repair and run the BootInfo report.

If still installing these have instructions. Differences in versions are minor. But for an external or second drive you need to use manual install to bet the choice on where to install the grub2 boot loader. You want the boot loader in the MBR of the external drive. (unless you have a new UEFI system.)

Install to external drive 11.04. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by darkod on 2012-10-31
First, you need to make sure in bios you are booting from the usb-hdd first otherwise it will try to boot from your internal.

Second, ext hdd will never be even near as fast as internal, so I sugegst you look into the option to by a replacement internal hdd.

On top of all that, grub2 might have been installed on the internal disk thinking you will want to boot from that since it's the natural first boot option.

If you still want to continue with your ext hdd install, boot the live cd again in live mode, open terminal and post the output of:
sudo parted -l (small L)

---

### Post by shreepads on 2012-10-31
Silly question, is the external drive connected via USB 3.0? Some systems are a bit cranky about booting from USB 3.0 and connecting to USB 2.0 should improve things.

So
- Connect external drive to USB 2.0
- Read your manual, find out how to trigger the boot menu and set the boot order to use the external drive first
- Cross your fingers... If it still doesn't work then it's time to start running Boot Repair

---

### Post by Mr SMS on 2012-10-31
Quoting you below. I looked on my external and the grub is on there, now I just need to get to the bios and tell it to boot from an external.

---

### Post by Mr SMS on 2012-10-31
> **darkod said:**
> First, you need to make sure in bios you are booting from the usb-hdd first otherwise it will try to boot from your internal.

Second, ext hdd will never be even near as fast as internal, so I sugegst you look into the option to by a replacement internal hdd.

On top of all that, grub2 might have been installed on the internal disk thinking you will want to boot from that since it's the natural first boot option.

If you still want to continue with your ext hdd install, boot the live cd again in live mode, open terminal and post the output of:
sudo parted -l (small L)


**Re: Hard drive issues Ubuntu 12.04.1 LTS**
 		Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system     Flags
 1      1049kB  750MB  749MB   primary  ext4            boot
 2      750MB   151GB  150GB   primary  ext4
 3      151GB   157GB  6000MB  primary  linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk

---

### Post by Mr SMS on 2012-10-31
The problem I am having now: 
The option to open the BIOS never appears. The computer, after I turn it on, just prompts me to insert proper boot media, no screen giving me the option to go to the BIOS or anything.

I pushed every possible button for the BIOS that I know (del, f2, f11) but I could not navigate there.

As for the external hard drive, this computer is all I have until my new computer arrives, and I can't do my work very well without mobile computer access. Can someone help me get to the BIOS so I can *encourage* the computer to boot from the external?

---

### Post by oldfred on 2012-11-01
Usually BIOS screen tells you what keys to hit, or you need to look in manual. 

I also have one time boot key f12 which lets me choose a boot device just this one time. My USB flash drives are always listed under hard drives not USB devices.

---

### Post by Mr SMS on 2012-11-02
I went to another thread in the forums and found that holding F2 and then pressing the power button (keeping f2 held the whole way through until boot menu setup opens) can get me to the bios. So I did that and am booting from my external now. Yay (solved). Now if only realtek-hd audio manager would install properly.

---

