---
title: "Formatting Linux Partition"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by ZorroSwordsman on 2007-08-27
Hi all, I'm new to the community and new to Linux altogether (4 days and counting). Before reading further, try to remember that I'm stuck on dial up and can't make a bunch of large downloads to fix my problem. Ok, Recently I installed Ubuntu on my HP laptop and have a total of four partitions. In cfdisk they are listed as:

sda1 | | Primary | Linux ext3 | 64996.17
sda2 | | Primary | NTFS | 1365.40
sda3 | | Primary | W95 FAT32 (LBA) | 12584.68
sda4 | Boot | Primary | Unknown (D7) | 1077.52

sda1 is the Linux installation partition
sda2 is the Swap partition
sda3 is the HP Recovery partition
sda4 is the Quickplay partition (for the Quickplay buttons on my laptop)

When I bought my laptop the HP Recovery CDs didn't come with it, and I didn't have 13 CDs to want to burn them. So, Ubuntu is installed and I'd like to restore my recovery partition (sda3) and wipe Ubuntu off the drive. I really like it, but I'm going to install Ubuntu on my desktop with a dual-boot setup (with XP) and leave my laptop with XP-only on it.

So, when Grub boots up I select a boot from my recovery partition and it launches the recovery thingy. But it says that there's not enough space on the "user" partition to restore it, so it exits. I stick my Ubuntu LiveCD in and run *sudo cfdisk*, delete my Linux and Swap partitions, and write it as NTFS; reboot. Bam! Grub is broke and I can't find a way to boot from the recovery partition. Bing! I reinstall Ubuntu and everything boots up fine, but now I'm back where I started.

So now to the question. How do I delete sda1 & sda2 and format them as NTFS with a partition name of "user" and then boot from my recovery partition and restore everything to the "user" partition? Also, if I run the LiveCD again and use cfdisk to erase the Linux and Swap partitions and make them NTFS, and then select my recovery partition to "boot," will it format my recovery partition like it says it *might*?

Please remember I'm on dial up, so no big downloads for me. :(

---

### Post by Magneticgravity on 2007-08-27
So, you want to format the Linux Partitions?

Have you got the Xp Disc? If so, pop it in, reboot, then go through the steps until you get to the Partitioning step. There you can format any of your current partitions.

Then simply exit.

---

### Post by ZorroSwordsman on 2007-08-27
Ok, I put an XP disk in that I had setting around and after it loaded the setup files and stuff and asked if I wanted to install XP or repair it, both selections came back with a message saying that it can't find my hard drive. Yet Ubuntu is booting up and working fine. What's happened? Simply put, all I want to do is use my HP Recovery partition to reinstall everything to the factory setup, but it doesn't seem to be that simple. :confused:

So how come Windows XP setup can't find my hard drive when I'm running Ubuntu without any problems?

---

### Post by ddrichardson on 2007-08-27
There are a number of threads reporting similar problems. The easiest thing to do is:

1. Backup the drives - particularly the HP recovery partition.
2. Check the BIOS for settings regarding how SATA is handled - Windows seems to have a problem when its set to behave as IDE.
3. Use the Ubuntu Live CD to delete the Ubuntu partitions and leave the unpartioned space.

---

### Post by ZorroSwordsman on 2007-08-27
I deleted the Ubuntu installation and swap partitions using the LiveCD. I went into the Bios and *disabled* SATA support, and then booted with a Windows XP CD. It then recognized my hard disk fine. Weird, it's the opposite of what you suggested, ddrichardson, but it's only because you brought it up that I tried it - so thanks for the suggestion.

Anyways, I managed to boot from my HP Recovery Partition and did a destructive recovery, meaning it's now *supposed* to be just like it was when it shipped. However, now when I boot up it says Operating System Not Found. Yet when I boot from the Windows XP CD and look at the partitions, everything is setup like it was when I got my laptop - so **all factory settings are there, it just isn't booting up right**.

So when I go to the Windows XP Recovery Console through the XP CD, I get four options:
D:\minint
D:\WINDOWS
C:\MiniNT
F:\WINDOWS

I tried a fixmbr and fixboot D: and fixboot F: and none of them worked - I still get the Operating System Not Found on bootup. I know this is past the Ubuntu setup and I'm back in the realm of Windows, but I think you guys are smarter then the Microsoft crowd so if you have any suggestions, please share them.

P.S. I'm definetly putting Ubuntu on my Desktop since I have a Windows XP Recovery CD (with all drivers, but no junk software) so a dual boot will be more practical and Linux will be an easier switch.

---

### Post by ddrichardson on 2007-08-27
I couldn't remember which way around the option was in BIOS ;-)

Have you changed it back now that everything is installed?

---

### Post by maybeway36 on 2007-08-27
Try getting your hands on a Windows98 or FreeDOS boot floppy with fdisk on it. First run:
```
fdisk /mbr
```
Then just type "fdisk" to open it up in interactive mode, and make the Windows XP partition active.

---

### Post by ddrichardson on 2007-08-27
No don't do that - Win98 was pre-NTFS, it'll cause more problems than it'll solve. You can restore an MBR from the console - I'm looking through the MSDN at the moment because I can't remember how ;-)

Infact Vista's loading mechanism is different to older OS versions anyway: found the link - [here]("http://support.microsoft.com/kb/919529").

---

### Post by ZorroSwordsman on 2007-08-27
Is there a way I can use something like _[diskpart]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/dm_active_partition.mspx?mfr=true")_ from the Windows XP CD? If making the main partition active is the way to fix this that is (or whatever partition is supposed to be active)... I'm really lost here guys, I've never done anything like this before and I'd sure hate to spend $30 or whatever on some recovery disks from HP (I hate the junk software that comes with it, but at least it can be uninstalled and there are no driver issues to deal with).

Once again, I know this is now out of Ubuntu's realm, but I'm so lost at the moment as to how to get rid of the "Operating System Not Found" error at bootup. Help! :-({|=

---

### Post by ddrichardson on 2007-08-28
Did you read the link?

**RESOLUTION**

To resolve these issues, follow these steps.

**Note** You can run the commands in the following procedure by using the command prompt. If you run these commands in Windows Vista, run them at a command prompt that has elevated user rights. To do this, click **Start**, click **Accessories**, right-click the command-prompt shortcut, and then click **Run as Administrator**. 1.Use Bootsect.exe to restore the Windows Vista MBR and the boot code that transfers control to the Windows Boot Manager program. To do this, type the following command at a command prompt: Drive:\boot\Bootsect.exe /NT60 All

In this command, Drive is the drive where the Windows Vista installation media is located.

**Note** The boot folder for this step is on the DVD drive.2.Use Bcdedit.exe to manually create an entry in the BCD Boot.ini file for the earlier version of the Windows operating system. To do this, type the following commands at a command prompt.

**Note** In these commands, Drive is the drive where Windows Vista is installed. &#8226;Drive:\Windows\system32\Bcdedit /create {ntldr} /d "Description for earlier Windows version"

**Note** In this command, Description for earlier Windows version can be any text that you want. For example, Description for earlier Windows version can be "Windows XP" or "Windows Server 2003".&#8226;Drive:\Windows\system32\Bcdedit /set {ntldr} device partition=x:

**Note** In this command, x: is the drive letter for the active partition. &#8226;Drive:\Windows\system32\Bcdedit /set {ntldr} path \ntldr&#8226;Drive:\Windows\system32\Bcdedit /displayorder {ntldr} /addlast

---

