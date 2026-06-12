---
title: "Minimal CLI uefi install on Asus AM1I-A/AM1M-A"
date: 2015-06-13
forum: Installation &amp; Upgrades
---

### Post by Matt_H on 2015-06-13
I just bought an inexpensive, low-power system for use with Linux. I want to dual-boot Xubuntu and a command-line interface minimal install (exact distro tbd).

My system is based on a AMD Kabini Athlon 5150 APU with an Asus AM1M-A mb. I have enabled CSM, and disabled secure boot. Xubuntu installs fine in UEFI mode.

My problem is that I cannot find a minimal, CLI distro that will successfully install on this motherboard in UEFI mode. Specifically, I want to install a bare-minimum OS so that I can build it up to what I want. I would much prefer it be Debian/Ubuntu based.

I have tried mini.iso, but it does not have UEFI support, and my Linux knowledge does not go far enough to modify it. Ubuntu server is the same. Also, as I understand, trying to mix BIOS and UEFI booting is a no-no.

Does anyone know of a solution? Or am I stuck booting both disrtos in legacy BIOS mode?

PS. I assume that once I install mt minimal distro first, the Xubuntu install will be smart enough to install itself in a dual-boot configuration.

Thanks,

Matt

---

### Post by ajgreeny on 2015-06-13
> I have enabled CSM, and disabled secure boot. Xubuntu installs fine in UEFI mode.
So is Xubuntu installed in UEFI or CSM, as it must be one or the other?

Are you saying the minimal install version will not even work in CSM?

---

### Post by Matt_H on 2015-06-13
I do not fully understand how all of the boot (uefi, CSM, etc) options on the Asus mb work together - that my be part of my problem - however, when I installed Xubuntu, I selected "UEFI: Sandisk..." from the boot menu list, and Xubuntu created a CSP (sp?) partition as the first partition. From what I understand, that is a UEFI mode partition.

The CSM option was also enabled, and the Boot Device Control option was set to "UEFI and Legacy OpROM", and Boot from Storage Devices was set to "Both, UEFI first" - although I don't think that option matters as I selected EUFI from the boot device menu.

Minimal mini.iso does install in legacy boot mode, however it does not boot afterwards.

Matt

---

### Post by oldfred on 2015-06-13
If you have minimal installed in CSM mode on a gpt partitioned drive that also has an efi partition, you can use Boot-Repair to convert from BIOS to UEFI. All it really does is uninstall grub-pc(BIOS) and install grub-efi-amd64(UEFI).

The server installer seems to have UEFI boot files. And you can just not to choose to install any of the default applications that it offers.

If you have one Ubuntu in UEFI mode, another install in UEFI mode will overwrite the efi boot. There is only one /efi/ubuntu folder. If same version of grub the only real difference is the grub.cfg in the /efi/ubuntu folder as it uses a configfile to find the rest of grub in your install. Back up efi partition or at least /efi/ubuntu/grub.cfg before another Ubuntu install.

---

### Post by Matt_H on 2015-06-13
Thanks for the responses. I will try Boot-Repair (I saw this mentioned in a few other places on the forum, but I always assumed it was referring to the Windows boot repair, since they all dealt with dual boot involving Windows). I'll have to look into the Ubunut boot repair since I'm not familiar with it.

Just to be sure, I should
1. install Xubuntu using UEFI mode, creating a GPT partitioned disk with a UEFI partition
2. back up the UEFI partition
3. install minimal to a  (newely created) parition using CSM nad legacy BIOS mode
4. boot repair to convert minimal to uefi

is that right?

In the meantime, i'll try experimenting with it (that's how I learn best!)

Thanks, 

Matt

---

### Post by oldfred on 2015-06-13
Should work, but testing always best.
Boot-Repair has a variety of repair options. It primarily is just automating various commands to reinstall grub or other boot issues. It only does minor repairs to Windows as for Windows you usually need the Windows repairCD or flash drive to run chkdsk or do more than install a Windows type boot loader.

There is another current thread where they posted that f4 on server install has 4 choices and one of those is minimal. Not sure if as minimal as minimal ISO?

[http://ubuntuforums.org/showthread.php?t=2282300&p=13303163#post13303163](http://ubuntuforums.org/showthread.php?t=2282300&p=13303163#post13303163)

---

### Post by Matt_H on 2015-06-15
I tried and was successful using the boot-repair method. It was actually pretty straight forward:

1. Install Xubuntu in UEFI mode
2. Boot using a live CD/USB and use gparted to resize Xubunutu's ext4 partition (I also deleted swap, as I have 8GB of RAM installed) and create a new ext4 partition for the minimal mini.iso install. (this should also work for other Ubuntu variants)
side note: I was only successful using Win32DiskImager to make a USB which successfully installed mini.iso. For some odd reason, using any other method would fail at connecting to my internet, both wired and wireless.
3. Switch back to UEFI boot mode!! Create a live USB with Boot-Repair-Disk (must be 64-bit for use with UEFI)
4. Boot-repair will automatically run upon startup. The Automatic option worked perfect for me. This will install EFI GRUB, and should detect all operating systems.
5. This is the trial and error part. Remove the Boot-Repair-Disk USB, and then go into the UEFI boot options. Under boot order, at least on my Asus MB, there are several boot options and appear to be the same (I even have a duplicate). These may look like "P1: Seageate XXXX..." and "ubuntu: XXXX". Upon reflection, the first is probably legacy BIOS boot mode, and the latter is UEFI mode, as I had set Boot Device Mode under CSM set to "Both, UEFI first". Only the UEFI mode "ubuntu: XXXX" option worked.
6. Now GRUB should show upon boot.
7. To confirm both OSes are booting in EFI mode, go to a terminal and use 'sudo efibootmgr' command. If in EFI boot mode, this command will list boot devices, and give an error if not in EFI mode. Depending on what distribution you installed, efibootmgr may have to be installed using 'apt-get install efibootmgr'

Matt

---

### Post by oldfred on 2015-06-15
Glad that worked and good to know for sure that it does. :)

---

