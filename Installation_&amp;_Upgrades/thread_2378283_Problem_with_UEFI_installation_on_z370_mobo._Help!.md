---
title: "Problem with UEFI installation on z370 mobo. Help!!"
date: 2017-11-21
forum: Installation &amp; Upgrades
---

### Post by mfleming on 2017-11-21
I've been doing Linux installs for about 25 years -- since the days of Slackware on floppy disks. Never had much of a problem -- UNTIL NOW!!!

I am trying to install Linux on a MSI mobo with z370 chipset. It has 3 drives, including 2 WD nvme pcie M.2 drives. I installed Windows 10 on one of the drives without difficulty, but I've been unable to install Ubuntu on the other. I've tried with both 16.04 LTS and 17.10.  I need full disk encryption, so chose manual partitioning, created an encrypted disk, and set the encrypted disk to mount /. I created a 200 MB EFI partition. That should have been enough, but the partitioner told me I also had to create a partition for /boot, because / was on an encrypted partition, which didn't make sense to me -- shouldn't the boot files go in the EFI partition? I tried putting the boot loader on the target disk or in the EFI partition of the target disk. The installs complete, without error messages in the case of 16.04 and with error messages for 17.10. But then I can't boot into the target disk (either by giving that disk priority in the boot order or by manually selecting that disk to boot from). Also, the BIOS marks with a "U" all the UEFI devices, and doesn't put that "U" on the disk containing Ubuntu.

I have tried setting the BIOS for "UEFI" only or "UEFI plus Legacy".  I have Secure Boot and Fast Boot turned off in the BIOS. I have the latest BIOS version. The target disk has GPT partitioning.

I've spent days on this. Would really appreciate any suggestions.

Matthew Fleming

---

### Post by oldfred on 2017-11-21
While I like to have an ESP on every drive, Ubuntu's version of grub only installs to ESP on sda, or first drive if NVMe.
Do not mix the UEFI required ESP - efi system partition which must be FAT32, with Ubuntu's /boot partition which must be a Linux format usually ext2, since relatively small and journal not required.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by mfleming on 2017-11-23
Thanks very much. This is what boot-info is saying:

[http://paste.ubuntu.com/26029539](http://paste.ubuntu.com/26029539)

Just to reiterate, nvme0 has Windows 10 and boots just fine. nvme1 has Ubuntu 17.10 and won't boot. I created an EFI partition, but it is not recognized by the motherboard (because the BIOS shows a "U" on nvme0 but not on nvme1) and won't boot nvme1. The nvme1n1p1 partition is the EFI partition, the nvme1n1p3 partition is an encrypted partition, and nvme1n1p2 is a partition that mounts /boot. Even with the EFI partition, the partitioner insisted that I create a partition for /boot, which did not make sense to me. Boot-info seems to be complaining about the encrypted file system (which should mount /) on nvme1n1p3, and I don't know why. /dev/sda1 is a SATA SSD which I've not used for anything. The machine also includes an optical drive which can apparently boot via EFI.

Any further assistance would be much appreciated!

Matthew Fleming

---

### Post by mfleming on 2017-11-23
One more thought. According to the documentation to which you referred me, Grub requires an ESP on nvme0 or sda, but I have one on nvme1.  Maybe that is the problem?  Based on the documentation, it seems I could use the ESP that Windows created on nvme0 to boot Ubuntu, without clobbering Windows. Should I try that?

I still don't understand why the partitioner insisted on an unecrypted filesystem for /boot. I'm pretty sure the installer was booted in EFI mode, because that's the BIOS was configured only for UEFI.

Matthew

---

### Post by oldfred on 2017-11-23
With UEFI you have to have an ESP - efi system partition as FAT32 with boot flag.
And with LVM and full drive encryption you have to have the /boot partition as ext2 or at least Linux type.
For Boot-Repair to work you have to mount, if not mounted and unencrypt the LVM partition(s), so grub can reinstall.
If using encryption be sure to have really good backup procedures. Many do not know LVM and often any system issue can cause issues with encrypted partition that then are difficult or impossible to recovery from. Then good backups save the day.

You show Ubuntu installed. And it is in same ESP as Windows as GUID in UEFI entry is same. Can you not boot this entry?
```
Boot0000* Windows Boot Manager	HD(2,GPT,[COLOR=#ff0000]260570d1-5618-42a5-b54d-30a360b932d8[/COLOR],0xfa000,0x32000)/File(EFIMICROSOFTBOOTBOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0001* Hard Drive	BBS(HD,,0x0)/VenHw(5ce8128b-2cec-40f0-8372-80640e3dc858,0200)..GO..NO..........W.D.C. .W.D.S.5.1.2.G.1.X.0.C.-.0.0.E.N.X.0....................,.@.r.d.=.X..........A............................DJDI..........Gd-.;.A..MQ..L.1.7.2.5.5.8.4.2.1.8.4.6........BO..NO..........W.D.C. .W.D.S.5.1.2.G.1.X.0.C.-.0.0.E.N.X.0....................,.@.r.d.=.X..........A............................DJDF.P........Gd-.;.A..MQ..L.1.7.1.3.6.0.4.2.0.7.9.8........BO..NO..........C.r.u.c.i.a.l._.C.T.2.7.5.M.X.3.0.0.S.S.D.1....................,.@.r.d.=.X..........A...........................>..Gd-.;.A..MQ..L. . . . . . . . .7.1.2.4.9.1.9.3.5.4.2.C........BO
Boot0002* CD/DVD Drive	BBS(CDROM,,0x0)/VenHw(5ce8128b-2cec-40f0-8372-80640e3dc858,0300)..GO..NO..........H.L.-.D.T.-.S.T. .B.D.-.R.E. . .W.H.1.6.N.S.4.0....................,.@.r.d.=.X..........A...........................>..Gd-.;.A..MQ..L.I.S.9.K.H.7.I.8.3.A.3.4. . . . . . . . ........BO
Boot0003* ubuntu	HD(2,GPT,[COLOR=#ff0000]260570d1-5618-42a5-b54d-30a360b932d8[/COLOR],0xfa000,0x32000)/File(EFIUBUNTUSHIMX64.EFI)
```

---

### Post by mfleming on 2017-11-24
> **oldfred said:**
> With UEFI you have to have an ESP - efi system partition as FAT32 with boot flag.
And with LVM and full drive encryption you have to have the /boot partition as ext2 or at least Linux type.
For Boot-Repair to work you have to mount, if not mounted and unencrypt the LVM partition(s), so grub can reinstall.

That should be what I have -? When I created the partitions I asked for an efi system partition on nvme1. The partitioner said I also needed a partition for /boot, which I created with an ext4 filesystem. And then the encrypted partition, of course.

I'm thinking that my mistake was requesting the efi system partition on nvme1.  I should have asked the installer to place the EFI files in the existing ESP on nvme0 that was created by the Windows installer, I'm now thinking. Is that correct? In this case I would still have created the other two partitions.

I don't understand your comment about the encrypted partition. I used boot-repair by running Ubuntu from the installation DVD and installing boot-repair from the ppa. The encrypted partition was supposed to be mounted at / on the installed system. It can't be mounted at / in the OS running off the DVD. What mount point should I use? Or can I use anything and then just tell boot-repair where it is?

> **oldfred said:**
> 
If using encryption be sure to have really good backup procedures. Many do not know LVM and often any system issue can cause issues with encrypted partition that then are difficult or impossible to recovery from. Then good backups save the day.

I run a medical lab and will be using this system to maintain software for the lab. I will copy the production system and its data to this one. so it has to be encrypted. I've been doing this for years, just never had a problem installing Ubuntu.
> **oldfred said:**
> 

You show Ubuntu installed. And it is in same ESP as Windows as GUID in UEFI entry is same. Can you not boot this entry?

Strangely I don't get a boot menu when I press F11, which is supposed to produce one. But I can boot the entry. It gives me a grub command line prompt, nothing more.
> **oldfred said:**
> 

```
Boot0000* Windows Boot Manager	HD(2,GPT,[COLOR=#ff0000]260570d1-5618-42a5-b54d-30a360b932d8[/COLOR],0xfa000,0x32000)/File(EFIMICROSOFTBOOTBOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0001* Hard Drive	BBS(HD,,0x0)/VenHw(5ce8128b-2cec-40f0-8372-80640e3dc858,0200)..GO..NO..........W.D.C. .W.D.S.5.1.2.G.1.X.0.C.-.0.0.E.N.X.0....................,.@.r.d.=.X..........A............................DJDI..........Gd-.;.A..MQ..L.1.7.2.5.5.8.4.2.1.8.4.6........BO..NO..........W.D.C. .W.D.S.5.1.2.G.1.X.0.C.-.0.0.E.N.X.0....................,.@.r.d.=.X..........A............................DJDF.P........Gd-.;.A..MQ..L.1.7.1.3.6.0.4.2.0.7.9.8........BO..NO..........C.r.u.c.i.a.l._.C.T.2.7.5.M.X.3.0.0.S.S.D.1....................,.@.r.d.=.X..........A...........................>..Gd-.;.A..MQ..L. . . . . . . . .7.1.2.4.9.1.9.3.5.4.2.C........BO
Boot0002* CD/DVD Drive	BBS(CDROM,,0x0)/VenHw(5ce8128b-2cec-40f0-8372-80640e3dc858,0300)..GO..NO..........H.L.-.D.T.-.S.T. .B.D.-.R.E. . .W.H.1.6.N.S.4.0....................,.@.r.d.=.X..........A...........................>..Gd-.;.A..MQ..L.I.S.9.K.H.7.I.8.3.A.3.4. . . . . . . . ........BO
Boot0003* ubuntu	HD(2,GPT,[COLOR=#ff0000]260570d1-5618-42a5-b54d-30a360b932d8[/COLOR],0xfa000,0x32000)/File(EFIUBUNTUSHIMX64.EFI)
```

---

### Post by oldfred on 2017-11-24
If you get grub menu, then grub is installed & working.
Then is issue that you need boot parameter to boot.
If you have an add-in video card you may need nomodeset until you install a proprietary driver. Some systems also require other boot parameters.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

