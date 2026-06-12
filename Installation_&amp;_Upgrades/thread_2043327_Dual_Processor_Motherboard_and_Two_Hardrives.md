---
title: "Dual Processor Motherboard and Two Hardrives"
date: 2012-08-16
forum: Installation &amp; Upgrades
---

### Post by WindsOfChange on 2012-08-16
Hi Members

Couple of questions please.

I'm installing ubuntu today from the CD I created after downloading the ISO image from the Ubuntu download site. I built a very powerful computer (at the time) back in 2001 that utilizes an iWill DVD 266R motherboard running two pentium III coppermine cpu's. I'm still running windows 2000 on this particular machine. I know how to install additional drives and know how to configure the BIOS if need be.

System:

iWill DVD266R Motherboard
Two (2) Pentium III cpu's onboard (each cpu is 1 GHz total 2.0GHz system)

Currently running 1 gig of DDR memory (total allowed on motherboard: 4 gigs)

One (1) 40 gig IDE hard drive set to master on its own 40 pin cable 

One (1) CD Rom Drive set as "Master" and One (1) DVD Drive set as Slave all on the same 40 pin cable.

**Questions please:**

1) Will Ubuntu support a two processor motherboard? I understand (for example) that windows XP home edition will not run on a dual processor motherboard however windows XP Pro will work just fine. Are there any issues with Ubuntu being installed on a Dual processor motherboard running two Pentium III cpu's for a total of 2 GHz ? 

2) I'm installing Ubuntu on its own hard drive today. I currently have windows 2000 installed on a 40 gig drive set to "master" (aka IDE0 slot on the motherboard). I'd like to install another drive and I'd like to know the best way to help Ubuntu dual boot the two OS's without a glitch using two separate drives. The 40 gig drive is partitioned and is full and I really don't want to reformat any partitions as I'd rather just install Ubuntu on a second drive.

I understand and read a lot of tutorials but one item is not addressed. Should I install the second hard drive on its own 40 pin cable or hook it to the same cable as the 1st hard drive and install Ubuntu to this second "slave" drive?

I currently have the CD Rom drive and the DVD drive on a second 40 pin cable (aka IDE1 slot on the motherboard). The CD drive is set to Master and DVD drive is set to slave.

Thanks so much members.

---

### Post by darkod on 2012-08-16
I don't know about the CPU question, but as far as the HDD is concerned I think it doesn't matter. You can install it as slave on the same IDE cable, and it should work fine.

Just make sure first (you can boot into live mode first and check) whether the new hdd is /dev/sdb or /dev/sda.

Being a slave, the new hdd for ubuntu should be /dev/sdb but it's best to check first than to install on the wrong hdd.

---

### Post by WindsOfChange on 2012-08-16
Hi Darko,

[B][COLOR=Blue]>>>Just make sure first (you can boot into live mode first and check) whether the new hdd is /dev/sdb or /dev/sda.

>>>Being a slave, the new hdd for ubuntu should be /dev/sdb but it's best to check first than to install on the wrong hdd. 	[/COLOR] [/B]

Thanks for helping Darko. What do you mean by "Live Mode"? Are you referring to the Live CD that I will use to install Ubuntu? If so, are you suggesting that I boot from the lIve Cd and run Ubuntu without installing (like a test drive)? If so, how do I find out if the second hard drive is actually reading the "Live CD" and showing it as /dev/sdb? Where would I check to see this?

Thank you kindly

---

### Post by darkod on 2012-08-16
Yeah, with the cd use the Try Ubuntu option first that will load the live desktop.

Then open Terminal and see the output of:
```
sudo fdisk -l
sudo parted -l
```

Those commands will show all HDDs and according to the hdd size and existing partitions you can see which is sda and which sdb.

---

### Post by oldfred on 2012-08-16
From the terminal you can run this to see drives & partitions.

sudo fdisk -lu

If you have IDE/PATA with 40 wire connections, you have to set jumpers correctly on drive. Some have master & slave, others have master with slave and slave.

If you have the somewhat newer IDE 80 write connection, you could use cable select. Newer BIOS with cable select let you boot either drive, but with master slave you can only boot the master, so you will have to install the grub2 boot loader to the MBR of sda which should be the master.

---

### Post by WindsOfChange on 2012-08-16
Hi Oldfred and Darko,



The additional drive I am using is a Western Digital 80 gig drive model WD800-BB that has the following jumper settings:

1) Cable select ::::l

2) Master w/Slave ::l::

3) Slave  :::l:

4) Master (only-no jumper installed) :::::

[COLOR=Blue]>>>f you have the somewhat newer IDE 80 write connection, you could use  cable select. Newer BIOS with cable select let you boot either drive,  but with master slave you can only boot the master, so you will have to  install the grub2 boot loader to the MBR of sda which should be the  master. 	[/COLOR]

Oh boy.... I knew this was coming :-) Thanks guys, I had a hunch it wasn't going to be as easy as I thought.  Is Grub2 available inside the Ubuntu Live Cd when I install Ubuntu or do I have to find the file separately? Are you saying that the bootloader should be installed on "sda" (which contains my windows 2000 OS) and Ubuntu will be on "sdb"?

Please be patient with me. There's a lot of new words here sucha s "terminal", "Grub" etc. Just working my way through. Thank you.

---

### Post by oldfred on 2012-08-16
If you only have the 40 wire cables, then you will have to install the grub2 boot loader to the MBR of the sda or master drive. That is the boot loader only and from grub's menu will still be able to boot Windows. You should have a Windows install disk and know how to reinstall the Windows boot loader in an emergency, or from a LIveCD you can install generic Windows work alike boot loaders so you could go back to directly booting your Windows.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

If you prefer a gui to repair boot loaders you can use this. You can install it into the Ubuntu liveCD (Each time you boot with CD) or download a full liveCD with it built in.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

If you have the newer 80 conductor cables, they have three colors on connectors.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

The little jumpers were so tiny & I always dropped them and could not see to find them, I often tried to use an old 40 conductor cable or in mucking around would bump the wide parallel cable just enough to partially disconnect them and many other issues. Or I am ham handed with hardware :) . So when I built my new system in 2006 and SATA was only slightly more expensive I jumped at using SATA, and have had a lot fewer issues.

---

