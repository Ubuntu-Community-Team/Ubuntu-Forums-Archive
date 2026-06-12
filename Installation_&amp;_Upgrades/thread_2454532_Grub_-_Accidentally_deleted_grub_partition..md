---
title: "Grub - Accidentally deleted grub partition."
date: 2020-12-01
forum: Installation &amp; Upgrades
---

### Post by sliwkahax on 2020-12-01
Hello, i accidentaly deleted the grub partition.
Now whenever i try to boot my pc it says: error: no such partition found, and it enters into rescue mode.
I have Mint 20, Ubuntu 20.04 and Windows 10 installed on the HDD.
On a flashdrive, i have a burnt Android x86 iso.

Any way to recover Grub?
Thanks.

---

### Post by CelticWarrior on 2020-12-01
There is NO "Grub partition". Grub is either installed in the boot drive's MBR (BIOS) or in the ESP (EFI System Partition) (UEFI).

What exactly have you done? And is your system and installation UEFI or BIOS?

---

### Post by sliwkahax on 2020-12-01
> **CelticWarrior said:**
> There is NO "Grub partition". Grub is either installed in the boot drive's MBR (BIOS) or in the ESP (EFI System Partition) (UEFI).

What exactly have you done? And is your system and installation UEFI or BIOS?

All systems are BIOS, i removed some very small partitions. When i rebooted the error appeared. I have kept the bigger partitions (Windows 10, Mint, Ubuntu). 
I have removed like 3 partitions, one was bootable, and one was extended , idk about the 3rd one.

---

### Post by Impavidus on 2020-12-01
There is a grub partition (or what is it called exactly?) if you have a bios/legacy install on a gpt drive. Windows doesn't boot in that configuration, but with Ubuntu only or Windows on a different drive it can work (although not very reliably).

On the other hand, you may be referring to the partition where grubs configuration is stored, typically the root partition. But the rescue prompt instead of the ordinary prompt suggests that more is missing. Have you got an Ubuntu live disk, preferably of the same version that you have installed? Can you use it to create a [boot repair](https://help.ubuntu.com/community/Boot-Repair) boot info summary?

---

### Post by sliwkahax on 2020-12-02
> **Impavidus said:**
> There is a grub partition (or what is it called exactly?) if you have a bios/legacy install on a gpt drive. Windows doesn't boot in that configuration, but with Ubuntu only or Windows on a different drive it can work (although not very reliably).

On the other hand, you may be referring to the partition where grubs configuration is stored, typically the root partition. But the rescue prompt instead of the ordinary prompt suggests that more is missing. Have you got an Ubuntu live disk, preferably of the same version that you have installed? Can you use it to create a [boot repair]("https://help.ubuntu.com/community/Boot-Repair") boot info summary?

All systems are BIOS, all 3 are on one drive. 
Unluckily, on the flashdrive i only have an "burnt" out Android x86 iso.
I have an idea, i could go to my friend house and burn out an ubuntu iso here. Then i would plug in the flashdrive to my pc and select try ubuntu. Then will i be able to manually re-install grub from here?

---

### Post by Impavidus on 2020-12-02
When you've got a live disk, you can reinstall grub and do whatever more is needed. Worst case scenario is that you have to reinstall all of Ubuntu, but even that isn't too bad. Right now we've got no idea of what's going on, hence the suggestion to create a boot info summary first. It should tell is exactly what partitions, operating systems and bootloaders are on your computer.

---

### Post by sliwkahax on 2020-12-02
> **Impavidus said:**
> When you've got a live disk, you can reinstall grub and do whatever more is needed. Worst case scenario is that you have to reinstall all of Ubuntu, but even that isn't too bad. Right now we've got no idea of what's going on, hence the suggestion to create a boot info summary first. It should tell is exactly what partitions, operating systems and bootloaders are on your computer.

I have said the operating systems, i dont exactly remeber the partitions, and my bootloander is grub, which is broken.
Reinstalling ubuntu won't be really bad for me, i dont keep important stuff here, same with windows and mint.
As i said before, will i be able to install grub from the try ubuntu option?
And if yes, what commands i need to type?

Anyway thanks for helping.

---

### Post by yancek on 2020-12-02
Are you unable to boot any of the 3 operating systems?  If that's the case, the best option is to get boot repair from the link in post 4 above.  You can either try to repair Grub or select the option to Create BootInfo Summary in boot repair and post the link you get here.  That will provide more detailed information for you to get some help.

---

### Post by sliwkahax on 2020-12-02
> **yancek said:**
> Are you unable to boot any of the 3 operating systems?  If that's the case, the best option is to get boot repair from the link in post 4 above.  You can either try to repair Grub or select the option to Create BootInfo Summary in boot repair and post the link you get here.  That will provide more detailed information for you to get some help.

I am unable to boot all of the OS. Whenever i boot the grub rescue screen appears. 
As i said above, will the Try Ubuntu method work? Aka. Can i reinstall grub from the Try Ubuntu option? If yes please give me the commands to install/repair it. 
If i cant do this ^ ill go for the boot repair.

---

### Post by ajgreeny on 2020-12-02
What I suspect you removed was a very small, 1-2M approx, FAT32 partition, flagged as **bios_grub** which is essential for using GPT partitioning in a BIOS/MBR system.

Using a legacy (not UEFI) live boot to any of the Ubuntu family of OSs run gparted and create again that small **bios_grub** partition, probably at the start of the disk though I think it can be anywhere on disk.  You may then be able to install grub again from the live system, using command ```
sudo grub-install /dev/sda
``` assuming you have only one hard disk /dev/sda.

I am assuming here that doing this in a GPT formatted system still works as it used to on msdos formatted system but you may wish to wait for more replies before going ahead with this final command.

---

### Post by sliwkahax on 2020-12-02
> **ajgreeny said:**
> What I suspect you removed was a very small, 1-2M approx, FAT32 partition, flagged as **bios_grub** which is essential for using GPT partitioning in a BIOS/MBR system.

Using a legacy (not UEFI) live boot to any of the Ubuntu family of OSs run gparted and create again that small **bios_grub** partition, probably at the start of the disk though I think it can be anywhere on disk.  You may then be able to install grub again from the live system, using command ```
sudo grub-install /dev/sda
``` assuming you have only one hard disk /dev/sda.

I am assuming here that doing this in a GPT formatted system still works as it used to on msdos formatted system but you may wish to wait for more replies before going ahead with this final command.
  ```
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Installing for i386-pc platform.
grub-install: error: failed to get canonical path of `/cow'.
```
?

---

### Post by sliwkahax on 2020-12-02
> **ajgreeny said:**
> What I suspect you removed was a very small, 1-2M approx, FAT32 partition, flagged as **bios_grub** which is essential for using GPT partitioning in a BIOS/MBR system.

Using a legacy (not UEFI) live boot to any of the Ubuntu family of OSs run gparted and create again that small **bios_grub** partition, probably at the start of the disk though I think it can be anywhere on disk.  You may then be able to install grub again from the live system, using command ```
sudo grub-install /dev/sda
``` assuming you have only one hard disk /dev/sda.

I am assuming here that doing this in a GPT formatted system still works as it used to on msdos formatted system but you may wish to wait for more replies before going ahead with this final command.

```
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Installing for i386-pc platform.
grub-install: error: failed to get canonical path of `/cow'.

```
??

---

### Post by Impavidus on 2020-12-02
We know that you deleted some partitions, making your system unbootable. We suspect that you deleted a bios_grub partition. That can be fixed. But something doesn't add up: A bios_grub partition is used to boot a legacy system on a GTP drive. That's fine with Ubuntu, but you write that Windows is installed on the same drive. The problem is, Windows cannot be booted from a GTP drive in legacy mode – at least, that's what I've always been told. So either Windows is on a different drive, or the drive isn't GPT partitioned, or the system is in UEFI mode.

Without knowing exactly what's going on, we can't give you a command that fixes your problem.

---

### Post by ajgreeny on 2020-12-02
As Impavidus  in post #4 it would make a lot of sense for you to run the boot info script, not a default repair, by following the instructions for Boot-Repair in my signature.
Post back the pastebin link you get and we will have much more detail about your system which may help sort out the many uncertainties seen so far.

---

