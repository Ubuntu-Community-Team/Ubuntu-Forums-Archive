---
title: "Can't access Windows 8.1 boot loader after dual booting with Ubuntu 14.04"
date: 2016-02-23
forum: Installation &amp; Upgrades
---

### Post by blakeborgna on 2016-02-23
Hi
I just installed Ubuntu 14.04 and now I can't boot into the Windows 8.1 OS that was originally on my computer. I have tried to run boot repair using:
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

I then ran the recommended repair and I got a message saying:
"GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag).  This can be performed via tools such as Gparted. Then try again."

I then created a bootinfo summary which is located at : [http://paste.ubuntu.com/15177759/](http://paste.ubuntu.com/15177759/)

Can someone please give me some advice as to how I can regain access to the windows boot system so that whenever I start my computer I will have a choice about whether I want to boot into Windows 8.1 or Ubuntu? I would really appreciate any help.
Thanks

---

### Post by oldfred on 2016-02-23
Was this pre-installed Windows 8 or did you install?

You are showing a gpt partitioned drive.
And you have Ubuntu in MBR for BIOS boot, with with gpt that needs a bios_grub partition to work as Boot-Repair explains.

But Windows only boots from gpt partitioned drive with UEFI.
And Windows only boots from MBR(msdos) partitioned drives with BIOS.

So Was Windows really UEFI? You do show an ESP - efi system partition. But it is saying it is NTFS, which is not correct. ESP must be FAT32 formatted with boot flag.
Or was Windows BIOS/MBR and you converted drive to gpt at some point.

You must be consistent. Always BIOS or always UEFI.

Also your Windows is not showing the /Boot/BCD which it requires whether UEFI or BIOS. Only Windows repairs will fix that. So you need a Windows repair disk or installer and its repair console.

But first you must resolve drive partitioning.
I think you had Windows in BIOS mode as you do not have the Windows system reserved which it normally creates and ESP is not configured correctly.

Only run this if Windows is BIOS install.
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

Then run Windows repairs to fix Windows and make sure it boots. That will reinstall Windows boot loader to MBR. 
Then use Boot-Repair to reinstall grub to MBR to dual boot in BIOS mode.

If really UEFI then totally different instructions are required.

---

### Post by blakeborgna on 2016-02-28
Thanks for the reply.  Windows 8.1 was pre-installed and I am not totally sure if it was BIOS or UEFI but I couldn't access the UEFI options through settings when I was trying to install ubuntu (I instead had to access the boot options during start up) so I am thinking that it would have been using BIOS.  Does this sound right? I guess I will try what you suggested and hope for the best.
Thanks

---

### Post by oldfred on 2016-02-28
Windows 8 and later if pre-installed by Mfg. then it is UEFI and secure boot is on. You do not have to (currently at least) have to have Secure boot on. Ubuntu will boot with Secure boot, but grub menu will not dual boot Windows if secure boot is on. You can dual boot from UEFI one time boot menu, often f10 or f12, check your manual.

If Windows was pre-installed then the boot partition is not NTFS but FAT32.
Lots of links and more info on UEFI in link in my signature.

---

