---
title: "Ubuntu installation on computers with Intel(R) RST enabled"
date: 2020-04-29
forum: Installation &amp; Upgrades
---

### Post by makem2 on 2020-04-29
Machine: DELL XPS 13 9300 UEFI powered

I have followed the instructions in Ubuntu Discourse to change to AHCI controller faithfully, checking every step before action. However, windows fails to boot.

I have followed the recovery instructions to the point where I need to find the partition containing the files needed to start (boot) windows.

Diskpart shows the following partitions:

0   C    OS                   NTFS   190GB
1   D   Unused                   NTFS   137GB
2   E   WINRETOOLS       NTFS   990MB
3         Image                     NTFS   14GB
4         DELLSUPPORT  NTFS   1563MB
5         ESP                        FAT32  180MB

The instructions tell me to switch to the partition conataining the needed files by selecting the partition letter. It is suggested the partition will be formatted as FAT32.

The partition ESP is formatted FAT32 (ESP) but how do I switch there as it does not have a letter?

---

### Post by makem2 on 2020-04-29
Just select the volume number in diskpart and use default settings to recover: bcdboot c:\windows

It took a couple of reboots and surprise! Winblows (oops) windows started up and I have AHCI controller :)

Hopefully xubuntu install easily as it usually does from here.

---

### Post by CelticWarrior on 2020-04-29
I don't do "Ubuntu Discourse" ;) so I don't know what exactly are you referring to but I'm surprise it didn't tell you that Windows would not boot after that change unless it had support for AHCI previously installed. In hundreds of posts here and elsewhere where me and other give that same information, change mode to AHCI, there's always a warning about Windows.

---

### Post by makem2 on 2020-04-29
I began the install of ubuntu in the same manner as I have for many years but this time I received a warning about RST and the warning had a Q code to scan on my phone.

This lead to a very detailed instruction set to install ubuntu on a machine using RST and how to change the controller to AHCI.

I followed the instructions there religiously and each time I thought it was finished it failed. There were some problems in the instructions and some things missing. At the very end when I was almost ready to give up I cracked it.

The instructions said use a drive letter but the partition I guessed windows was on did not have a drive letter. There were a number of switches in the command to reboot into windows as a last resort and I could not get any to work without a drive letter. I decided not to use any switches and use diskpart to address the correct partition (no drive letter) to see what happened, nothing to lose!

It worked and windows booted with the AHCI controller in use. Ubuntu is installed and both are happy.

AHCI was an option in the bios.

[https://ubuntuforums.org/showthread.php?t=2442054&p=13951842#post13951842](https://ubuntuforums.org/showthread.php?t=2442054&p=13951842#post13951842)

---

### Post by makem2 on 2020-05-05
@CelticWarrior

I have decided to return the machine and need to set it back to Windows 10 factory defaults.

All of the original partitions are intact and the only reason I can see there may be a problem is with the system being set to AHCI.

Can you tell me, if I use the Dell system to return it to factory setting will it be ok to leave AHCI set or should I change it back first?

TIA

---

### Post by CelticWarrior on 2020-05-05
If you're recovering the original image then it's likely it won't work with a different mode.

---

### Post by makem2 on 2020-05-05
> **CelticWarrior said:**
> If you're recovering the original image then it's likely it won't work with a different mode.

Are you able to assist in reverting it?

---

### Post by CelticWarrior on 2020-05-05
> **makem2 said:**
> Are you able to assist in reverting it?

Not really. I don't know your computer and I don't need to. But you should. It's the same UEFI settings you changed to AHCI that can be changed back to what it originally was, that's all.

---

