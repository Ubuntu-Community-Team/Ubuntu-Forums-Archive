---
title: "ubuntu 22.04 fails to boot after installation - not a duel boot"
date: 2022-05-18
forum: Installation &amp; Upgrades
---

### Post by cemandt58 on 2022-05-18
Hi, thanks in advance. I have searched for an answer to this problem but still haven't found a solution. 

I performed a clean install of Ubuntu 22.04 but it fails to boot after install. This is NOT a duel boot and my computer uses BIOS. Ubuntu 22.04 only. 

Error message:  BootDevice Not Found
                          Please install an operating system on your hard disk 

As I've read, this is a problem with the bootloader GRUB. I performed this suggested fix using the Live USB: 

1. Edited the /etc/default/grub file to include the line:  GRUB_DISABLE_OS_PROBER= false 
2. Save and exit
3. sudo update-grub 

number 3 gave me this error message:  /usr/sbin/grub-probe: error: failed to get canonical path of '/cow'

I'm not sure what to do. 

This is my system info: 

HP ProBook 450 G2 

Current System BIOS Version:  M73 Ver. 01.42
Current BIOS Release Date: 09/26/2016 

Processor: Intel Core i7-5500u CPU,  2.40 GHz, 8 GB RAM 

I know the computer is a little old but it still does what I need to do very well. 
FWIW, I did not see the grub.cfg file in the /boot/grub directory. Should I have ? 

Thanks for your help. 

Chuck

---

### Post by Bashing-om on 2022-05-18
cemandt58; Hello - Welcome to the Forum

Yes !
the /boot/grub directory should have the file grub.cfg .

I show you my result on a 20.04 bios install:
```

 sysop@2004x-c:~$ ls -al /boot/grub
total 2392
drwxr-xr-x 4 root root    4096 May 10 17:22 .
drwxr-xr-x 4 root root    4096 May 11 13:33 ..
drwxr-xr-x 2 root root    4096 Dec 18 20:26 fonts
-rw-r--r-- 1 root root     712 Dec 18 20:25 gfxblacklist.txt
-r--r--r-- 1 root root   19335 May 10 17:22 [color=green]grub.cfg[/color]
-rw-r--r-- 1 root root    1024 May 18 14:04 grubenv
drwxr-xr-x 2 root root   12288 Dec 18 20:26 i386-pc
-rw-r--r-- 1 root root 2395475 Apr  4 13:49 unicode.pf2
sysop@2004x-c:~$ 

```

So I gather the next step on your system is to properly install the boot code (grub) :D

to that end - from the liveUSB in "try ubuntu" mode - run terminal commands:
The "#" character is for a "comment" --  not to be entered --
```

sudo fdisk -lu
#so you know the target to install to !

```
Now once you are sure of the target:
```

sudo mount /dev/sda1 /mnt ## where sda1 contains the "/" partition, change as required to you actual target if different
sudo grub-install --boot-directory=/mnt /dev/sda ## (Don't put a partition number in this command, just the HDD location a, b, etc.)

```
once the install of grub completes UNmount the target partition:
```

sudo umount /mnt

```

Reboot into the install and let's see what there is now :D

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by oldfred on 2022-05-18
That really is an UEFI system, but BIOS boot should work.
Check that default boot is not UEFI or UEFI with Secure boot. You need it set to Legacy/BIOS/CSM or whatever HP calls it.

HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216)

---

### Post by cemandt58 on 2022-05-19
The command: sudo mount /dev/sda1 /mnt   produced the following error message: 

mount: /mnt: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error. 

The command:  sudo fdisk -lu produce the following results: 


Disk /dev/loop0: 2.33 GiB, 2502324224 bytes, 4887352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 81.26 MiB, 85209088 bytes, 166424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 155.63 MiB, 163188736 bytes, 318728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 284 KiB, 290816 bytes, 568 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 61.89 MiB, 64901120 bytes, 126760 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 248.76 MiB, 260841472 bytes, 509456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 43.63 MiB, 45748224 bytes, 89352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: TOSHIBA MQ01ABD1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 16EDAB2B-304C-4798-A62E-07E7D52E4212

Device       Start        End    Sectors  Size Type
/dev/sda1     2048       4095       2048    1M BIOS boot
/dev/sda2     4096    1054719    1050624  513M EFI System
/dev/sda3  1054720 1953523711 1952468992  931G Linux filesystem


Disk /dev/sdb: 29.3 GiB, 31457280000 bytes, 61440000 sectors
Disk model: STORE N GO      
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: A09DB2B8-B5F6-43AE-AFB3-91E0A90189A1

Device       Start      End  Sectors  Size Type
/dev/sdb1       64  7129427  7129364  3.4G Microsoft basic data
/dev/sdb2  7129428  7137923     8496  4.1M EFI System
/dev/sdb3  7137924  7138523      600  300K Microsoft basic data
/dev/sdb4  7139328 61439936 54300609 25.9G Linux filesystem


Disk /dev/loop8: 45.86 MiB, 48087040 bytes, 93920 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


I had a previous installation on the drive with Ubuntu and before that a dual boot with Windows. I thought a clean installation would erase all of that so that I could start over. Apparently not. It seems it still thinks there is a Windows partition. 

Not sure what to do. Delete the partitions and start over ? If I delete the partitions will the space be automatically freed up ? 

In the past I used the utility dban to completely erase the disk and then did a manual partition during installation using the "something else" option.

---

### Post by oldfred on 2022-05-19
Your sda drive has both a bios_grub partition which is used for BIOS/CSM boot on gpt partitioned drives and an ESP - efi system partition used for UEFI boot. But only one Linux partition. Did you install twice? Once BIOS and once UEFI?
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

Boot mode in UEFI must match how you have installed.

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)   &           
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by cemandt58 on 2022-05-19
Hi, thanks. 

Here is the link:  [https://paste.ubuntu.com/p/XV6gHjXWTv/](https://paste.ubuntu.com/p/XV6gHjXWTv/) 

Here is some history: 

Initially, I had a dual boot with Windows 7. I then upgraded, when offered, to a later version of Ubuntu that was not LTS. Can't remember which one but the install did not work and broke the install IIRC. Then tried again and Ubuntu installed on a really small partition. It was usable however so I decided to wait for the 22.04 LTS to be released. 

I really don't want a Windows install anymore. Prefer Ubuntu 22.04 LTS on the entire drive. 

Thanks for your help.

---

### Post by tea for one on 2022-05-19
[COLOR="#0000FF"]Line 42[/COLOR] - 0 OS detected

According to the boot-repair report, you do not have an Operating System installed.
Do you have backups of your personal data?

Your only option is to re-install.
Please choose UEFI mode and GPT.

Your PC is UEFI but you have booted the live session in old-style Legacy mode.
[COLOR="#0000FF"]Line 53[/COLOR] - BIOS/UEFI firmware: M73 Ver. 01.42(1.42) from Hewlett-Packard
[COLOR="#0000FF"]Line 54[/COLOR] - This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).

If you are unfamiliar with UEFI and GPT, please ask.

---

### Post by oldfred on 2022-05-19
Please reboot & run in UEFI mode. You show UEFI install of Ubuntu.
It also looks like you cut off report as a lot of info is missing. So re-run after reboot.

> This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).

---

### Post by cemandt58 on 2022-05-19
I'm kind of confused here. I went through the installation process by choosing the install option after "Try and Install". It went through a lengthy process of installation. After that it told me to reboot which is where I ran into problems. So where did the installation go ? 

I also don't remember it asking me about UEFI or anything else. At which point do I choose UEFI ? 

I have the data backed up so I don't mind reinstalling but at what point would the process be any different ? 

Additionally, I don't remember cutting off the report. All I did was copy and paste the link after it finished. Weird.

---

### Post by grahammechanical on 2022-05-19
> I also don't remember it asking me about UEFI or anything else. At which point do I choose UEFI ?

The Ubuntu installer does not ask us. With the machine switched off we plug in the USB memory stick with the Ubuntu installer on. We switch on the machine and enter the UEFI settings utility. We select to boot from the USB memory stick but we choose the mode to boot in - UEFI or BIOS/Legacy/CSM mode. Whatever mode we boot the installer in, then that will be the mode that Ubuntu will be installed in.

You must tell the installer where to install Grub. In your case it will sda2. The EFI System partition. Where do you intend to install Ubuntu - sda3 or sdb4?

Regards

---

### Post by tea for one on 2022-05-19
Thank you for confirming that you have backups.

You choose UEFI when you boot into a live session.
Your one-time boot menu (F9 for HP) should indicate the mode with UEFI:name of USB device Sandisk/Kingston etc (UEFI followed immediately by a colon)

Hopefully the screenshot will explain better.

---

### Post by cemandt58 on 2022-05-19
OK, I have three options from the settings utility on startup (Advanced): 

1. Legacy - (this was the default I believe) 
2. UEFI Hybrid (With CSM)
3. UEFI Native (Without CSM)

Not sure which one to choose - probably 2 or 3

Would like to install in sda3 

I don't know why the sdb device is there and why I need it. I'd prefer to get rid of it for simplicity. I noticed that sdb1 and sdb3 say "Microsoft basic data" . How did that get there and what does it mean ? 

I am not familiar with GPT or UEFI for that matter. 

Thanks for your help thus far.

---

### Post by oldfred on 2022-05-19
Your sdb looks like the live installer flash drive.
Any NTFS or FAT32 partitions may be identified as Windows.
UEFI is the replacement for BIOS, but many vendors still call it BIOS.
Microsoft has required vendors to install in UEFI boot mode to gpt partitioned drives since 2012 & release of Windows 8. So hardware since then is all UEFI based. Old BIOS still offered more to allow new systems to be installed onto older hardware. Now even 10 year old hardware is UEFI.

Lots of links in info on UEFI & gpt in link in my signature. See Acronyms nearer bottom for definitions & links to more details.

---

### Post by tea for one on 2022-05-20
The sdb device in the boot-repair report [COLOR="#0000FF"]Line 107[/COLOR] is your USB - [COLOR="#0000FF"]sdb:31.5GB:scsi:512:512:gpt:Verbatim STORE N GO[/COLOR]

As you have data backups and you only want Ubuntu, there is nothing to lose.
Therefore, you can install from scratch.

Can you double-check some UEFI settings (if applicable)?
Disable Secure Boot (Some vendors require an Admin password to access the Secure Boot setting)
Disable Fast Boot 
Disable Legacy mode 
Check that Legacy USB Support is enabled

Choose [COLOR="#0000FF"]3. UEFI Native (Without CSM)[/COLOR] and boot into a live session.
When you are in a live environment, open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```
Hopefully, the output is UEFI mode. 
(If not, you will have to reboot the live session in UEFI mode - this is essential.)

Open gparted > Device > Create Partition Table > Select [COLOR="#0000FF"]gpt
[/COLOR]
Install type via [COLOR="#0000FF"]Erase Disk and Install Ubuntu[/COLOR]
The installer will create the EFI and System partitions automatically.
You do not have to worry about installing to sda3 because it is a single OS system.

Any success?

---

### Post by cemandt58 on 2022-05-26
Yes, thanks ! It looks like it's working now. Thanks for your help.

---

### Post by tea for one on 2022-05-26
You solved by a new install?
If so, it is beneficial to mark the thread as solved to help other users/searchers.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by ockelz on 2022-07-12
> **tea for one said:**
> The sdb device in the boot-repair report [COLOR=#0000FF]Line 107[/COLOR] is your USB - [COLOR=#0000FF]sdb:31.5GB:scsi:512:512:gpt:Verbatim STORE N GO[/COLOR]

As you have data backups and you only want Ubuntu, there is nothing to lose.
Therefore, you can install from scratch.

Can you double-check some UEFI settings (if applicable)?
Disable Secure Boot (Some vendors require an Admin password to access the Secure Boot setting)
Disable Fast Boot 
Disable Legacy mode 
Check that Legacy USB Support is enabled

Choose [COLOR=#0000FF]3. UEFI Native (Without CSM)[/COLOR] and boot into a live session.
When you are in a live environment, open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```
Hopefully, the output is UEFI mode. 
(If not, you will have to reboot the live session in UEFI mode - this is essential.)

Open gparted > Device > Create Partition Table > Select [COLOR=#0000FF]gpt
[/COLOR]
Install type via [COLOR=#0000FF]Erase Disk and Install Ubuntu[/COLOR]
The installer will create the EFI and System partitions automatically.
You do not have to worry about installing to sda3 because it is a single OS system.

Any success?

No succes here installing 22.04 on an HP Elitebook 1040 Folio neither in Legacy mode or UEFI mode. Booting from USB in UEFI mode confirmed, GPT partition created. Whole installation wiping complete disk went flawless, but after rebooting i was still confronted with a missing operating system.
I had multiple previous flavours of linux installed and they all ran perfect on this machine for years. Never had any problem. I ended up frustrated installing 20.04.4 in legacy mode.

---

### Post by ubfan1 on 2022-07-12
Wasn't HP the vendor that did strange things with their UEFI Boot, like only booting files named bootmgfw.efi or maybe named "Boot Manager for Windows"?  The default grub install should have also set up the device boot in EFI/Boot/bootx64.efi (a copy of shimx64.efi) with EFI/Boot/grubx64.efi also present, with the EFI/ubuntu/grub.cfg a stub pointing to the root's maintained /boot/grub/grub.cfg

---

### Post by coffeecat on 2022-07-12
The OP has marked this thread as solved. If anyone needs help with a similar problem, please start your own thread.

Thread closed.

---

