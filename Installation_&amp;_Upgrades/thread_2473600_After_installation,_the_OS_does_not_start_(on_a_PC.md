---
title: "After installation, the OS does not start (on a PC 2 OS)"
date: 2022-04-08
forum: Installation &amp; Upgrades
---

### Post by onnivia on 2022-04-08
My tasks:
1. There are windows, I want to install a second OS ubuntu 20.04 lts, I have always had only windows.
2. I want the PC to ask me which OS to enter when I turn it on.
3. I have 2 disks (physically these are also different disks). Drive C has windows on it and drive D has just files on it and I want to allocate space on it for ubuntu. I want access to disk space with files from both OSes in half, so that I can use both OSes without difficulties, use the same files.


My ubuntu installation process:
1. An OS image is written to the USB flash drive.
2. Installation parameters:
- 45 gigabytes were taken from drive D with the setting of the "ntfs journaled file system" parameter and the /windows label. After that, they were listed as free space.
- 24 gigabytes set as logical, space start, label /
- 21 gigabytes set as logical, start space, label /home
- a device for installing the efi bootloader


What happened during installation:
- gave an error "Installer terminated abnormally" - reasons were not specified.
- I click close. After that, oddly enough, the ubuntu OS started up.
- I turn off the PC to check if it prompts me to select an OS.
- windows updates started.
- only windows starts, ubuntu is not offered to start.


What happened to windows:
- my disk D, the remaining 700 gigabytes, became known as disk F. and disk D became known as a new space of 500 megabytes, I didn&#8217;t have it before.
- I changed the disks back, since my windows programs were on the D drive and this is necessary for them to work.
- you can see 2 volumes, those / and / house, but you can&#8217;t see the files there from windows.


Starting the OS through bios:
- If you select the disk on which the label drive D is located, then it says: uncknow filesystem entering rescue mode grub recue
- if you select the disk on which I have windows, then windows starts


Help run ubuntu!
What is wrong with my setup. I saw that ubuntu works, that it is. But I'm not prompted to run it.

---

### Post by tea for one on 2022-04-08
As you can start Windows, can you see all your data on the second drive?
If you can, then the first priority is to backup all your personal data from your Windows drive and the second drive?

Ubuntu can be re-installed or repaired after you have confirmed that you have backed up your files.

---

### Post by onnivia on 2022-04-08
I can see my windows data is working without problems. The task is to make ubuntu work too. So that I can run two OSes of my choice. ubuntu started automatically once after the installation was completed and it doesn't start anymore, I don't know how to start it.

---

### Post by ajgreeny on 2022-04-08
Without knowing where you really have got to so far it is impossible to give good advice on where to go next, so go to **Boot-Repair** in my signature below and follow the instructions there to run the ***Boot-Info-Script***.	

***Do not run the default repair just yet*** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by onnivia on 2022-04-08
As I understand it is a script for Linux. I only have access to windows

---

### Post by tea for one on 2022-04-08
> **onnivia said:**
> As I understand it is a script for Linux. I only have access to windows

You run boot-repair from a live Ubuntu session, info herewith:-
> 2nd option : install Boot-Repair in Ubuntu

- either from an [COLOR="#0000FF"]Ubuntu live-session[/COLOR] (boot your computer on a Ubuntu live-USB then choose "Try Ubuntu") or from your installed Ubuntu session (if you can access it)

- connect to the Internet

- open a new Terminal, then type the following commands (press Enter after each line):
```

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt update
sudo apt install -y boot-repair && boot-repair
```

---

### Post by yancek on 2022-04-08
>  As I understand it is a script for Linux. I only have access to windows 		 

You have Ubuntu  Linux on your flash drive which you are using to install.  If you have an internet connection when using Ubuntu on the flash drive, you can go to the boot repair site and download and run it.  When you are at the boot repair page, use the 2nd option described on that page to add a PPA.  You should be prompted to run it and use the option to Create BootInfo Summary.  When it finishes, you should get a link to post here so that members can review the information and assist you.  If you don't see a prompt after downloading boot repair, open a terminal and type:  boot-repair and hit the Enter key.

You neglected to indicate which version of windows you are running which is important information so do that.
Is  this an UEFI install?  Are both windows and Ubuntu installed UEFI?  Do you know what UEFI is?
If you want to share data between windows and Ubuntu, you need an ntfs filesystem as windows default is not capable of accessing a Linux filesystem.  You  can see the Linux partitions from Disk Management in windows but a default windows will not read or view data on a Linux filesystem.

Not sure why your drive letters changed but windows does not assign drive letters to Linux filesystem partitions and Linux does not use drive letters.  

When you boot, can you access the BIOS firmware and if you are using UEFI, select Ubuntu from Boot Options.

---

### Post by onnivia on 2022-04-08
Do not attach files here. Link to google drive: [https://drive.google.com/drive/folders/1en_JtxnPZ_eCKOPFJbQeJPGEP24XWG0v?usp=sharing](https://drive.google.com/drive/folders/1en_JtxnPZ_eCKOPFJbQeJPGEP24XWG0v?usp=sharing)

[ https://paste.ubuntu.com/p/n32GnMPrBC/]("https://paste.ubuntu.com/p/n32GnMPrBC/") The link that the system down, but it seems to be a link with an error

---

### Post by grahammechanical on 2022-04-08
This is what concerns me.

> - 24 gigabytes set as logical, space start, label /
- 21 gigabytes set as logical, start space, label /home
- a device for installing the efi bootloader


"Logical?" A logical partition would be on a drive with Master Boot Record (MBR) partitioning scheme. An EFI boot partition is required for drives that have a GUID partition table (GPT) and if the OS is install in UEFI mode. 

When using the Something Else option the installer requires us to set a mount point of / and /home for the partitions we want to use as / and /home. A label is useful for recognising partitions but the mount point is necessary for the installer.

Regards

---

### Post by onnivia on 2022-04-08
> **grahammechanical said:**
> This is what concerns me.



"Logical?" A logical partition would be on a drive with Master Boot Record (MBR) partitioning scheme. An EFI boot partition is required for drives that have a GUID partition table (GPT) and if the OS is install in UEFI mode. 

When using the Something Else option the installer requires us to set a mount point of / and /home for the partitions we want to use as / and /home. A label is useful for recognising partitions but the mount point is necessary for the installer.

Regards

I didn't get it =(

---

### Post by tea for one on 2022-04-08
[COLOR="#0000FF"]Line 90 [/COLOR]- 1 OS detected
[COLOR="#0000FF"]Line 92[/COLOR] - OS#1:   Windows 10 or 11 on sdb2

No sign of Ubuntu in the report (as you mentioned in post no. 1 [COLOR="#FF0000"]"gave an error "Installer terminated abnormally" - reasons were not specified"[/COLOR].)

[COLOR="#0000FF"]Line 13[/COLOR] - Windows 7/8/10/11/2012 is installed in the MBR of /dev/sdb

Your Windows OS is installed in old style BIOS/MBR yet your PC is EFI compatible as detailed here
[COLOR="#0000FF"]Line 103[/COLOR] - The firmware is EFI-compatible, and is set in EFI-mode for this live-session.

In order to have have a robust dual boot for the future, my suggestion is:-
Back up all your personal data
Re-install Windows 10/11 on one disk in UEFI mode with GPT.
Restore Windows data and check if everything is OK

Disconnect, de-activate, isolate via UEFI settings or physically remove existing Windows OS drive so that only the second target drive is accessible
Boot Ubuntu live and check that you are in UEFI mode
Open a terminal and enter:-
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
Create GPT on your target disk using gparted
Open gparted > Device > Create Partition Table > Select gpt
Allow the installer to automatically create the necessary partitions (or your preferred configuration)
Double check that an EFI partition will be created

Boot each system independently via UEFI boot screen
Boot priority can be controlled by UEFI

You can later create a partition (ntfs format) to share between each OS if desired.

---

