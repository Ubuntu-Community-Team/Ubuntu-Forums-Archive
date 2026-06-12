---
title: "install on HP Z600"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by pvanb on 2010-12-13
I just got a HP workstation Z600 and want to install Ubuntu, preferably using dual boot with the pre-installed Windows 7.

The Z600 has the following (relevant for my question) specifications:
HP 1000GB SATA 7200 (1st)
HP 1000GB SATA 7200 (2nd)
HP RAID 1 (mirrored  Array) Configuration
Windows 7 Professional 64 – bit OS

I can boot in Ubuntu 10.10 using the live CD without problem. Next step I tried is shrinking and re-partitioning to allow dual-booting. However, in Gparted I can see two drive marked with error message (exclamation mark), telling me that the sda1 and sda2 do not exist (see screenshot). 

The Device utility recognizes the SATA Host Adapter and two SATA Hard disks, but also lists under Peripheral Devices a 1.0 TB Hard disk, a 2.1 GB Hard disk and a 998 GB Hard disk, see screenshot (the 688 MB file is the CD, the 320 GB hard disk is an external harddisk)

Because I am not sure how to progress from here I tried to install Ubuntu first using Wubi, but that failed with the error message that 'no root system is defined, please correct from partitioning menu'.

Moreover, this hardware Support Matrix for Current HP Linux Workstations     ([http://h20000.www2.hp.com/bc/docs/support/SupportManual/c00060684/c00060684.pdf](http://h20000.www2.hp.com/bc/docs/support/SupportManual/c00060684/c00060684.pdf)) says that hardware RAID is supported using the LSI 8888 ELP (RAID 0,1, 5 SAS Only), LSI 8888 ELP (RAID 0, 1, 5 SAS Only), LSI 9260-8i (RAID 0, 1, 5 SAS Only), and the Onboard SAS 
Raid (RAID 0,1,). However, SATA Raid is not supported

Given the above I am not sure how I can safely install Linux (preferably with dual boot, although I could live with loosing Windows). Also, removing the RAID (if possible, unclear to me) and just using the two HD would be fine for me too.

Any tips for the best way forwards or info whether people have installed Linux successfully on the described system?

Regards,

Paulo

---

### Post by ronparent on 2010-12-13
The 10.10 distro gparted has a bug that prevent it from seeing the raid drives as a raid. It is easily worked around. Just boot to the live cd and in a terminal window do 'sudo apt-get install kpartx'. This is only temporary and will last only until the live cd seesion is closed but will allow you to do a normal install to the raid. 

If you decide not to use a raid, post and I will give further instruction. Once the raid has been configured and used even in Win7, the raid must be turned off in the raid bios and meta data which was written to both disk must be erased to insure the drives can be used as two separate normal drives. Post if you need more help.

---

### Post by ghostborg on 2010-12-13
[http://www.technobuzz.net/how-to-install-ubuntu-in-windows-with-wubi/]("http://www.technobuzz.net/how-to-install-ubuntu-in-windows-with-wubi/")

Here is a WUBI guide, just make sure your pointing to the correct Windows drive and partition, typically your C drive. Make sure your not pointing to an image partition if your system came with a pre-loaded Windows OS. It should attempt to create an environment within Windows without molesting your Windows system. It's been a few years since I used it but it ran pretty well and would recommend you try Ubuntu this way until you get a feel for it. I don't remember WUBI but as with Ubuntu you need to choose the correct 32 or 64 bit Desktop install for your processor.
If you are using the manual partitioning you typically have an 8MB swap partition, a bootable root partition "/" and /Home .
[https://help.ubuntu.com/8.04/switching/installing-partitioning.html]("https://help.ubuntu.com/8.04/switching/installing-partitioning.html")

If you have an old desktop laying around thats even better and it should run pretty snappy on an old system. Remember to be patient as you are going through a learning curve. I would say it was a good two years for me before I started using it everyday, but should be shorter for you since Ubuntu has come a long way.

P.S. I you have no luck with 10.10 try 10.04 LTS since it is the Long Term Support release.

---

### Post by pvanb on 2010-12-14
@ [ghostborg]("http://ubuntuforums.org/member.php?u=298901"): Thanks for your reply. I have been using Ubuntu for a year or two. My main problem right now is how to install it on my new computer. I never had major problems installing Ubuntu, but with RAID configuration installation seems to be less out of the box and more likely to go wrong. 

@ [ronparent]("http://ubuntuforums.org/member.php?u=634522"): Thank you for your information. I tried your suggestion and Gparted could see the RAID. I didn't take the next step, mostly because I am not sure right now what would be the better (and easier) solution, using the RAID or using the two HD separately. Running Windows on one, Linux on the other HD seems like a good solution, but how difficult is it (or more important, how likely that things go wrong)? I also wonder what they mean with SATA Raid not being supported on Linux (as opposed to RAID configuration listed in my previous post).

The RAID has been used in Windows 7. Complicating factor is that I can't create a recovery CD for Windows, the utility isn't there and the only information I get from the IT support at my university is links to HP website where they explain how to use that (absent) utility. So if possible, Windows should be maintained on one of the HD. Is that possible?

If going for the RAID, should I go for the FakeRaid or SoftRAID? I am not sure even after checking this page ([https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)). SoftRAID would work from the normal LiveCD install?

---

### Post by pvanb on 2010-12-15
Hi ronparent, 

I prefer to use the two HD separately, i.e., not in a RAID configuration and I would like to take on your offer to help out.

I have found the option to change the SATA emulation from RAID+AHCI to IDE in the BIOS (under storage-storage option).

There is also the option under Advanced - device option to enable/disable 'SATA RAID option ROM download', which is if I understand well, an utility to change RAID settings, including removing HD from the RAID setup?

I would appreciate it if you could provide the steps to do this, including your earlier remark about erasing meta data written to both disks (this means the OS will be erased too I assume?). After disabling the RAID, I can reformat the disks and install Ubuntu the normal way (on one of the disks)?

I don't know if it is relevant, but the DVD/CD is also under the SATA host adapter (see screenshot I posted previously).

Cheers,

Paulo

---

### Post by ronparent on 2010-12-15
> I prefer to use the two HD separately, i.e., not in a RAID configuration and I would like to take on your offer to help out .
This is perhaps your best option. I would suggest you first go into the raid bios and remove the two drives from raid configuration (probably best to leave them as AHCI).

Before you install, boot to the live cd and in a terminal first write 'sudo dmraid -rE sda' and then the same for sdb to erase the raid meta data.

Then you will have the choice to install in either sda or sdb. I would open gparted to check the status of the partitioning. There will probably be the mirrored windows partitions showing on both drives. You can delete the partitions on sdb and repartition them however you like. If you plan on installing to sda, however, you should try to boot to windows and use windows to create unallocated space on sda for your Ubuntu install. I'm not sure that windows 7 will be bootable at this point. If not you can fix it or reinstall it later. In any event you can install Ubuntu now wherever you please. If on sda, however, you should plan installing it to an extended partition - win 7 already occupies two primary partitions and Ubuntu will need two more partitions (not necessarily primary). Since you are limited to four primary partitions on a drive you would have more flexibility to create additional partitions if you do it this way.

Installing should now be straight forward, But post if you have any problems. Good luck.

Regards, Ron

---

### Post by pvanb on 2010-12-16
Hi Ron,

Your suggestions worked like a charm. Just in case anybody wanting to do the same. The option to reset the disks to non-RAID came with a big warning that all data would be lost. However, nothing was lost or changed on my disks. 

Following your suggestion I left the SATA emulation (under storage - storage option in the BIOS menu) as RAID+AHCI (the other option was to change it to IDE). 

After leaving the BIOS menu and booting into Windows I deleted the partitioning on my second HD with the Disk Management utility. 

After that I closed Windows and booted my computer with the Ubuntu live CD. Your suggestion to remove the RAID meta data did not work (I forgot the precise message, but it was something about the RAID disc not existing), neither was it needed. I guess the BIOS matrix storage manager, which I used to reset the discs to non-RAID, took care of that already. 

Just as an additional note for others wanting to do something similar: I choose to install Ubuntu on the second HD. I manually partitioned the drive. In the first place because I wanted a /home partitioning, but also to get the GRUB2 boot loader on the second HD (thus leaving the Windows boot loader intact). This means that when defining the partitioning table you have to define a /boot partitioning on your 2nd HD and tell the installer to install grub to that partitioning (default is to install grub on the 1st HD, which will overwrite the Windows boot loader). 

After that, you close Ubuntu, restart the computer, open the BIOS and change the booting order, placing the 2nd HD above the 1st HD.  

Again, thanks for the help!

Paulo

---

### Post by ronparent on 2010-12-16
Glad to hear of your success. It does seem that turning off the raid in bios does remove the meta data in your case. That is not typical but it does make life easier.

Have fun. Ron

---

### Post by pvanb on 2010-12-17
Mm, not sure, but I might have cheered too soon. Trying to boot into Linux this morning gave me a kernel panic message. However, I don't think this has to do with the dual boot setup. I am still posting what happened because it is related to another step I described in my previous post.    The problem started after an update, which included a kernel update.  Trying to boot up gave a kernel panic with the message: “not syncing; VFS: unable to mount root fs on unknown=block”.  As it turns out, the root was set to read only. There are many posts about similar issues, but it was this post [http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7) which showed me how restoring grub 2 solved the issue.    It looks like, after the kernel update, the boot script is looking in the wrong location for /root. The solution above basically (as far as I can see) copies the boot files from /boot to /boot, where it is found after booting again.   As this didn't feel like a real permanent solution, I decided to reinstall Ubuntu, but this time without a separate /boot partitioning, instead installing grub 2 directly on the /dev/sdb.   I rebooted twice now and it seems to work (keeping fingers crossed).  There is only this root folder (/root) which is unreadable, wonder what that folder is. I never noticed it on my other computer.

---

