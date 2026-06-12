---
title: "Installed Ubuntu 12.04 and have lost access to Windows 7."
date: 2012-09-13
forum: Installation &amp; Upgrades
---

### Post by rikimaru90 on 2012-09-13
I installed it using the first option, install along side Windows. And I  had 30GB of unallocated space on a separate hard drive than Windows. 

Now when I choose the Windows boot I get something like 'Invalid EFI  path.' I still need Windows because my family also use this PC.

[http://paste.ubuntu.com/1202156/](http://paste.ubuntu.com/1202156/)

And here is a screenshot of my partitions from gparted: [http://i.imgur.com/orDnB.png](http://i.imgur.com/orDnB.png)

I just tried boot repair and got this: 'GPT detected. Please create a  BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag).  This can be performed via tools such as Gparted. Then try  again.Alternatively, you can retry after activating the [Separate  /boot/efi partition:] option.'

Really need to sort this ASAP as my family use this PC and they are flipping out on me other this...

---

### Post by darkod on 2012-09-13
Do you know where is your win7 installation, on sda or sdb?

Looks like you might have win7 on the 1TB disk, but also it might be on the 2TB disk.

This looks to me like a mix up with the UEFI boot. If win7 is on sdb, it doesn't seem you were using UEFI, but you installed ubuntu in UEFI mode. Hence the confusion to boot windows now.

First start by explaining where is windows, then we will see.

---

### Post by rikimaru90 on 2012-09-13
Windows is in sdb.

It is one big unpartitioned drive, in NTFS and flagged as 'boot'.

---

### Post by darkod on 2012-09-13
So, how come you seem to be booting with UEFI now and you were not earlier?

We know that you were not because sdb has msdos partition table and win7 can only work on gpt table with UEFI boot.

Did you change something in BIOS? Go into bios, and make sure you disable the UEFI boot if possible.

Since you have no data in the new ubuntu yet, it's not a problem to reinstall. Just note that sda is with gpt table and BEFORE you reinstall ubuntu you will have to create a small 1MiB partition with NO filesystem (DO NOT format it with anything) and the bios_grub flag. That is needed for grub2 on gpt disks.

So, look around for disabling UEFI boot, and if you need help about the bios_grub partition before you reinstall ubuntu, ask.

---

### Post by rikimaru90 on 2012-09-13
I just went into BIOS and disabled UEFI boot, but it did not fix the problem. 

I have not changed anything, do you think maybe Ubuntu did during install?

Someone before told me to make that 1mb partition, then try boot repair again. Do you think I should try that?

---

### Post by darkod on 2012-09-13
Hold on, don't worry about ubuntu now, and it has little to do with win7 not booting.

You still have windows bootloader on both disks, but one of them might be wrong. So, try to boot from sdb as first option, if it doesn't work, try from sda.

All win7 boot files look correct, and the bootloader is there.

If the computer is trying to boot in the standard bios mode, it should work, either from one disk or the other. Check that out first.

PS. I'll be offline few hours, if win7 starts working, it's up to you if you want to wait for detailed instructions how to reinstall ubuntu, or go with it. Maybe someone else will jump in too. Don't be too impatient, especially if win7 starts working, it's better to do things right, than fast. :)

---

### Post by rikimaru90 on 2012-09-13
Ah okay, I can relax a little now, changing the boot priority to sdb completely bypasses the grub and boots into Windows.

So, I'd rather not uninstall Ubuntu and do everything again to be honest. I have already done so twice, as I installed it on Wubi, really liked it so I uninstalled and started again. Doing so again is an option, but one I'd rather avoid if possible. If not, I'll have to learn to do it right.

---

### Post by darkod on 2012-09-13
Small correction, you don't even have grub on any MBR. That was the UEFI boot manager giving you that error.

I didn't understand whether you want to continue with this installation, since it seems to me it was installed in UEFI mode and you don't boot in UEFI. So, I don't think you can count on using this installation.

If there is any important data there, you can boot into live mode with the cd and copy everything you need. After that I would delete all ubuntu partitions, then create the small 1MiB bios_grub partition, and then do the new installation.

---

### Post by YannBuntu on 2012-09-13
Hello

> **rikimaru90 said:**
> [http://paste.ubuntu.com/1202156/](http://paste.ubuntu.com/1202156/)

And here is a screenshot of my partitions from gparted: [http://i.imgur.com/orDnB.png](http://i.imgur.com/orDnB.png)

I just tried boot repair and got this: 'GPT detected. Please create a  BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag).  This can be performed via tools such as Gparted. Then try  again.Alternatively, you can retry after activating the [Separate  /boot/efi partition:] option.'

Your Windows is installed in Legacy (=non-EFI) mode, on a standard disk.
You installed Ubuntu on the other disk, which is GPT. Ubiquity (the Ubuntu installer) is not very clever, as it installed Ubuntu in EFI mode, when it should have installed it in Legacy mode.

What I would do:
1) disable EFI in your BIOS settings
2) via Gparted, delete your sda3 partition. Instead, create a BIOS-Boot partition (1MB, unformatted filesystem, bios_grub flag).
3) run Boot-Repair's Recommended repair, and indicate us the new URL that will appear please.

---

### Post by rikimaru90 on 2012-09-14
Thanks, do you mean UEFI? In BIOS I have an option to disable it. What are the pros and cons of using UEFI? Am I missing out on anything by disabling it?

---

### Post by black veils on 2012-09-14
> What are the pros and cons of using UEFI? Am I missing out on anything by disabling it?

perhaps [COLOR=Blue]**[this]("https://www.linux.com/learn/tutorials/588498-uefi-secure-boot-big-hassle-questionable-benefit")**[/COLOR] information will help, or from [COLOR=Blue]**[wikipedia]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface")**[/COLOR]

---

### Post by rikimaru90 on 2012-09-14
> **YannBuntu said:**
> Hello



Your Windows is installed in Legacy (=non-EFI) mode, on a standard disk.
You installed Ubuntu on the other disk, which is GPT. Ubiquity (the Ubuntu installer) is not very clever, as it installed Ubuntu in EFI mode, when it should have installed it in Legacy mode.

What I would do:
1) disable EFI in your BIOS settings
2) via Gparted, delete your sda3 partition. Instead, create a BIOS-Boot partition (1MB, unformatted filesystem, bios_grub flag).
3) run Boot-Repair's Recommended repair, and indicate us the new URL that will appear please.

Okay here is the link.

[http://paste.ubuntu.com/1204421/](http://paste.ubuntu.com/1204421/)

When it asked me where to install GRUB I was not sure, I thought it would be that 1mb space you asked me to make, but that wasn't an option so I just chose sda.

---

### Post by darkod on 2012-09-14
You chose correctly, it should be /dev/sda. It only saves it's core.img file on sda3.

In this case, I don't agree it was better to run boot-repair. Sometimes it's much better to do things manually than with one-click tools, although I have total respect for boot-repair designed by Yann.

I am saying this because boot-repair also installed grub2 on /dev/sdb and it would have been nice to keep windows bootloader there. You saw it yourself, it came handy when you selected to boot from /dev/sdb and it booted windows right away.

But that's not a big issue anyway, you can always return windows bootloader on /dev/sdb, you can even use the boot-repair for that. If you ever need it.

Actually, thinking about it, if you told boot-repair to install grub2 on /dev/sda, why is there grub on /dev/sdb too and it wasn't there before?
Yann, any ideas?

Aside from this, if you boot from /dev7sda now, do you get a correct grub boot menu? If you select ubuntu and windows, do they boot OK?

---

### Post by rikimaru90 on 2012-09-14
Well yes, I can now boot into Windows from Grub. And I can boot into Ubuntu now too.

Only thing is, it stops when loading up ubuntu now and says '/boot/efi is not ready or is not present' And I have to press 'S' to skip it. Then it boots seemingly correct. I believe that was sda4 which I deleted right?

---

### Post by darkod on 2012-09-14
That's why I suggested a new clean install. Last time ubuntu was installed in UEFI mode, not in standard BIOS mode, and it is now looking for the grub-efi location. Which it doesn't even need because you are not booting in UEFI now.

If it's only this, no problem. But if in the future other issues start coming up, you never know. I think you are OK, it's simply looking for the /boot/efi.

Take a look in /etc/fstab, I think it's trying to mount it with an entry there, which you can disable. What is the output of:
cat /etc/fstab

---

### Post by rikimaru90 on 2012-09-14
This is the results of that:

owner@owner-System-Product-Name:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda4 :
UUID=58fe00fb-0262-4be8-adb6-4424d78aea12    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda3 :
UUID=F4B7-489A    /boot/efi    vfat    defaults    0    1
#Entry for /dev/sda2 :
UUID=46C29470C2946649    /media/YAY!    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.UTF-8    0    0
#Entry for /dev/sdb1 :
UUID=8ECC6480CC646505    /media/sdb1    ntfs-3g    defaults,locale=en_GB.UTF-8    00
#Entry for /dev/sda5 :
UUID=3eaba369-618c-42be-b51e-dd212a47329a    none    swap    sw    0    0


owner@owner-System-Product-Name:~$

---

### Post by darkod on 2012-09-14
> **rikimaru90 said:**
> This is the results of that:

owner@owner-System-Product-Name:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda4 :
UUID=58fe00fb-0262-4be8-adb6-4424d78aea12    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda3 :
[COLOR=Red]UUID=F4B7-489A    /boot/efi    vfat    defaults    0    1[/COLOR]
#Entry for /dev/sda2 :
UUID=46C29470C2946649    /media/YAY!    ntfs-3g    defaults,nosuid,nodev,locale=en_GB.UTF-8    0    0
#Entry for /dev/sdb1 :
UUID=8ECC6480CC646505    /media/sdb1    ntfs-3g    defaults,locale=en_GB.UTF-8    00
#Entry for /dev/sda5 :
UUID=3eaba369-618c-42be-b51e-dd212a47329a    none    swap    sw    0    0


owner@owner-System-Product-Name:~$

You see the above? It has an entry trying to mount the old sda3 to /boot/efi.
Just open fstab as sudo, and put the # symbol at the front of that line. That disables the entry, it makes it like comment.
To open as root with gedit, you can use for example:
gksu gedit /etc/fstab

Save the change and close. Reboot and it should be fine.

It's also safe to delete that entry in fstab, but lets disable it for a start first.

---

### Post by darkod on 2012-09-14
I also see you are mounting your windows system partition, sdb1. While in most cases it works fine, sometimes windows can start complaining if linux touches the system partition.

I would disable that entry too, and only mount sdb1 temporarily when I need to read or copy something. Not at every boot.

But the choice is yours.

---

### Post by Mohan1289 on 2012-09-14
> **rikimaru90 said:**
> This is the results of that:


#Entry for /dev/sda3 :
UUID=F4B7-489A    /boot/efi    vfat    defaults    0    1

owner@owner-System-Product-Name:~$

Isn't this is the efi location which the system is searching?? correct me if i'm wrong

---

### Post by Mohan1289 on 2012-09-14
can't we give the location of EFI location which is in /boot/sda3 to the system by editing the file in the Ubuntu file system..

---

### Post by rikimaru90 on 2012-09-14
Right, commenting that line out fixes the problem, so problem solved I guess now haha. 

Thanks guys I can now enjoy Ubuntu and my family can continue to be unhappy on Windows lol.

---

### Post by darkod on 2012-09-14
> **Mohan1289 said:**
> can't we give the location of EFI location which is in /boot/sda3 to the system by editing the file in the Ubuntu file system..

You didn't read the thread correctly. The problem to solve is not to make the efi partition available.

The computer is not using EFI boot but ubuntu is looking for that /boot/efi partition from when it existed earlier. So the solution is simply to comment it out in fstab, so that it doesn't look for it any more.

---

### Post by YannBuntu on 2012-09-14
> **rikimaru90 said:**
> Thanks, do you mean UEFI?

Yes. [UEFI =~ EFI]("http://en.wikipedia.org/wiki/Uefi")

> **rikimaru90 said:**
> What are the pros and cons of using UEFI? Am I missing out on anything by disabling it?

No. Indeed you just can't use your current Windows if you don't disable it.

---

