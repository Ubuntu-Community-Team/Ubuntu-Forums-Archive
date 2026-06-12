---
title: "Dual boot to winXP with grub and uefi board."
date: 2012-08-12
forum: Installation &amp; Upgrades
---

### Post by phalantice on 2012-08-12
I installed xp and ubuntu a while back had every thing running well.  I  could dual boot etc.  I upgraded my systemboard that came with uefi and  now it wont boot to winxp unless i select the drive that xp is installed  on from the bios boot menu. 

The windows partition was created by the winxp install and is the first  primary on that drive.  In another users question it had the same issues  and edited the partition to fix it.  which was subsiquently locked by a  mod claming it was to old to be relivent :roll:  

I suspect it is a bug in grub but have no way to verify that.  I tried  to boot the drive in legacy mode today,  the only option i could change  was from ahci to ata which didnt help.  

I have tried multiple versions of grub with and wo efi support,  I even tried grub 1 and same results.

---

### Post by oldfred on 2012-08-12
Most UEFI will also boot in BIOS mode. With XP you just about have to use BIOS mode as XP does not work with gpt partitioning and requires special drivers to work with AHCI which are easiest installed while installing XP.

If in BIOS mode it should not be different than your old install. Grub2 will work from MBR.

Post link to BootInfo report from this:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by phalantice on 2012-08-13
[http://paste.ubuntu.com/1145874/](http://paste.ubuntu.com/1145874/)

My systemboard is an asrock z68 extreme 3 gen 3 I checked the manual and didnt see any thing that listed a legacy/bios mode. the closest was a uefi shell option the bios updates adress ivey bridge cpu's which i may try in a bit

sda3 was ghosted from sdb1 and expanded by 30 gb or so. sdb2 fedora install was a test to verify another linux got the same results with grub 1 and grub 2.  I left ubuntu's grub at 2.  fedora got the same results as ubuntu did.

---

### Post by oldfred on 2012-08-13
Someone with Asrock posted this, not sure if your model has similar settings:

> So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!
AsRock calls BIOS mode AHCI.

But with XP you have to have AHCI drivers. I converted to AHCI with my new SSD as that was recommended/required and I finally shut down my XP which I said I was going to do for the last 5 years. I did boot it once but had to go into BIOS and turn off AHCI, so it is a real hassle. Not sure with your new motherboard you can do that or not.

I would not try to use grub legacy anymore, it is missing a lot of features for newer systems that grub2 now has. I did use grub2 to boot my XP since 9.10 until I converted to 12.04 and my new SSD.

Are you still running PAE 32 bit?
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

---

### Post by phalantice on 2012-08-14
yes for ahci drivers...  I intigrated them when I built the install image.  grub1 was just a test to see if it was a grub2 only thing...  

thats the kernel that came with ubuntu... was to lazy to do any thing about it since it was my desktop ad the nvidia drivers were being a pain.  i have a pair of 1440x900 pannels one running 90 rotated.  since it didnt want to play nice i never bothered with how well it ran.  I may make it work right when steam goes native. 

I had a couple issues with x64 that I got tird of fighting and when i installed 11.4 i went with 32bit.

---

### Post by oldfred on 2012-08-14
Only the 64 bit version has the option to install in UEFI mode. 

But if you want to run XP, you cannot use UEFI as that has to have gpt partitioning which does not work with XP.

---

### Post by NewAmercnClasic on 2012-11-12
I was having the same issues and I was only able to remedy by drawing a new partition table, I was also able to replicate the error with a Windows8 pre-release.  It turned out to be a grub related error.  Not sure if that helps.

---

