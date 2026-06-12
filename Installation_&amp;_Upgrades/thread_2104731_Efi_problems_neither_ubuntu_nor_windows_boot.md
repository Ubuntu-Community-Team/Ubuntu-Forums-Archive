---
title: "Efi problems: neither ubuntu nor windows boot"
date: 2013-01-14
forum: Installation &amp; Upgrades
---

### Post by hamiltonpb on 2013-01-14
I had Windows 7 pre-installed in my laptop. (So, I do not have any  recovery DVD). When trying to install Ubuntu 12.10 somehow my bootloader  went broken. I've tried to use Boot-repair's recommended repair.  However, it didn't find sda7 after I wrote the instruction on terminal. [http://paste.ubuntu.com/1529385/](http://paste.ubuntu.com/1529385/) 
So, I am able to boot neither Windows 7 nor Ubuntu. 

Any suggestion?

---

### Post by oldfred on 2013-01-14
I cannot read all of Boot-Repairs suggestions. But you have Windows 7 in UEFI mode with an efi boot partition. Your partitions are gpt based on Windows only boots from gpt partitioning with UEFI.

If you have a fast boot setting in UEFI menu turn it off.

Windows looks like it should boot in UEFI mode. Did you resize Windows from Windows MMC or the Ubuntu installer. Best to resize with the MMC and reboot Windows a couple of times as it wants to run chkdsk and make other repairs for its new size. 

But you installed Ubuntu in BIOS  mode and it created bios_grub to install in BIOS mode. You have two bios_grub partitions which may be why it does not boot in BIOS mode? You should should not need either. 

Boot the Boot-Repair in UEFI mode from UEFI menu. Do not have system set for BIOS boot.

Boot-Repair can convert a BIOS install to UEFI install by uninstalling grub-pc and installing grub-efi. It will also create a correct chain load entry to Windows efi partition as grub still has a bug and creates the old BIOS type entries.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

After running Boot-Repair, go back into UEFI menu and boot the ubuntu entry.

---

### Post by hamiltonpb on 2013-01-15
Let me see if I understood. (I need an explanation for dummies.)

1. I checked that UEFI is on. However, starting boot-repair, it tells me that the laptop is in Legacy mode. 
2. How boot-repair converts bios install into UEFI install? Please, give datailed instructions. 

Many thanks!

---

### Post by hamiltonpb on 2013-01-15
PS: Boot-repair "recommended repair" is not able to make any change in laptop's boot.

---

### Post by oldfred on 2013-01-15
You also need to boot the Boot-Repair in UEFI mode. It does have some capability to force changes when in BIOS mode, but best to be in UEFI mode.

Some of the latest updates are to be sure the new secure boot works and different vendors have different ways you have to do work arounds.
       How Boot-Repair works with UEFI systems - post 687 Dec 15, 2012
[http://ubuntuforums.org/showthread.php?t=1769482&page=69](http://ubuntuforums.org/showthread.php?t=1769482&page=69)
How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

---

### Post by hamiltonpb on 2013-01-16
oldfred,

first of all, many thanks!

Almost everything is working now. However, I can only load Ubuntu or Windows by accessing bios setup. That's my problem now. The instruction in the setup ask for

fs0:\path\filename.efi

but it does not work at all!
[http://paste.ubuntu.com/1537780/](http://paste.ubuntu.com/1537780/)

---

### Post by hamiltonpb on 2013-01-16
I think the problem happens because boot-repair considers the laptop in Legacy mode, although the bios setup says it is in EFI mode!

---

### Post by oldfred on 2013-01-16
Every vendor's UEFI seems to be different. Some have secure boot on/off, UEFI on/off and legacy/BIOS on/off, but then depending on choice other options may not be available. 
Others may have a UEFI on which means secure boot off, but not legacy boot.

You do have to boot installer or repair flash drive in UEFI mode, and then from UEFI menu should be able to choose the ubuntu entry. Then it should reboot with ubuntu as the default until you change it in the UEFI menu. And Boot-Repair will create a correct chain entry to Windows.

Line 724 says this:
BootOrder: 0002,0005,0003,0004
Boot0005* ubuntu
But you have another entry at 737:
BootOrder: 0000,0002,0003,0004
Boot0000* ubuntu

You want ubuntu first in Boot order, not sure why you have two different entries shown. Is that somehow an option in your UEFI menu?

---

### Post by hamiltonpb on 2013-01-16
I suppose that happened while installing Ubuntu 12.04. (Now I am using 12.10) It correctly detected the UEFI and created a partition for booting in uefi mode. But it didn't worked. 

I tried also to fix my boot from Windows, using a repair Cd. However, after trying both 64 bit and 32 bit version (my system is 64 bit), both send the message:
"This version of System Recovery Options is not compatible with the version of Windows you are trying to repair. Try using a recovery disk that is compatible with this version of Windows".

So, there is something wrong in the Windows installation. I was not planning to upgrade to Windows 8, but maybe this can solve this problem. What do you think?

I did not understood your suggestion above. What do you mean by booting installer? 

Accessing bios setup I see two different entries for Ubuntu. I suppose that they are attached to \EFI\Boot\bootx64.efi and EFI\ubuntu\grubx64.efi. If so, they where created by Boot-repair. I can not edit these lines from bios setup.

Once more, many thanks.

---

### Post by oldfred on 2013-01-16
I think even with Windows 7 you need the fat32 version of Windows repairs like Windows 8. That is the only way it will boot with UEFI.
       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

    
Both Windows & Ubuntu have  \EFI\Boot\bootx64.efi, I do not know if they really are the same file or not. UEFI has a mode like a command line to run some things and I think that is just the UEFI shell?

If you boot Ubuntu do you not get the grub menu? And does it have the efi chain load entry from Boot-Repair, not the os-probers boot entries to a partition as those do not work.

---

### Post by hamiltonpb on 2013-01-16
Yes, if I boot Ubuntu I do get the grub menu. I see:
Ubuntu
Advanced Options for ubuntu
Windows boot UEFI Loader
efi/EFI/Microsoft/Boot/bootmgfw.efi
efi/EFI/Bootx64.efi
Windows Recovery Environment

---

### Post by hamiltonpb on 2013-01-16
The fourth and fifth options (efi/EFI/...) do not work.

---

### Post by oldfred on 2013-01-16
Boot-Repair creates the entries in 25_custom. But the last two are wrong? Not sure if old entries?

There should work as the UUID is for sda1 your efi partition.
```
menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 5E81-001E
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root 5E81-001E
chainloader (${root})/EFI/Boot/bootx64.efi
}

```Not sure where these came from as the UUID is a Linux partition sda6, you can just delete them if you want.
```
menuentry "efi/EFI/Microsoft/Boot/bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root b20bc021-b062-4fec-909d-c8cde3c12c66
chainloader (${root})/efi/EFI/Microsoft/Boot/bootmgfw.efi
}

menuentry "efi/EFI/Boot/bootx64.efi" {
search --fs-uuid --no-floppy --set=root b20bc021-b062-4fec-909d-c8cde3c12c66
chainloader (${root})/efi/EFI/Boot/bootx64.efi
}
```       gksudo gedit /etc/grub.d/25_custom
Then do:
sudo update-grub

---

### Post by hamiltonpb on 2013-01-16
Well, since I was able to see the options to load the system only after the use of boot-repair, the entries could be old... 

Typing the commands you gave above, I received a error message: unexpected token `('.

I am flattered by your attention.

---

### Post by oldfred on 2013-01-16
If you edited 25_custom is there a mis-match on {} or () somewhere.

In my post above I left out the ending }, in the two boot stanza to delete. 

It used to tolerate some typos, now any entries you add must be correct.

---

### Post by hamiltonpb on 2013-01-16
I received the message in the first entry of your command, not in those to be deleted.

---

### Post by oldfred on 2013-01-16
Copy all the commands from you terminal and post. I will not be back on line until tomorrow am.

---

### Post by hamiltonpb on 2013-01-16
hamilton@hamiltonN:~$ sudo su
[sudo] password for hamilton: 
root@hamiltonN:/home/hamilton# menuentry "Windows UEFI bootmgfw.efi" { search --fs-uuid --no-floppy --set=root 5E81-001E chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi }
bash: erro de sintaxe próximo do `token' não esperado `('

---

### Post by hamiltonpb on 2013-01-17
> **oldfred said:**
> Boot-Repair creates the entries in 25_custom. But the last two are wrong? Not sure if old entries?

There should work as the UUID is for sda1 your efi partition.
```
menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 5E81-001E
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root 5E81-001E
chainloader (${root})/EFI/Boot/bootx64.efi
}

```Not sure where these came from as the UUID is a Linux partition sda6, you can just delete them if you want.
```
menuentry "efi/EFI/Microsoft/Boot/bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root b20bc021-b062-4fec-909d-c8cde3c12c66
chainloader (${root})/efi/EFI/Microsoft/Boot/bootmgfw.efi
}

menuentry "efi/EFI/Boot/bootx64.efi" {
search --fs-uuid --no-floppy --set=root b20bc021-b062-4fec-909d-c8cde3c12c66
chainloader (${root})/efi/EFI/Boot/bootx64.efi
}
```       gksudo gedit /etc/grub.d/25_custom
Then do:
sudo update-grub

Would you mind to explain the difference between the 2 first command lines and the last two menu entries?

I suppose you are editing the menu entries. In the first, you are telling that \dev\sda1 is to be set as root and directing the load to the Windows 7 boot. Is that right?

The second one is the same, but it directs to Ubuntu, is that right?

Now the problem are the following ones: they direct the menu entries to \dev\sda 6 . But I do not see how these entries are being deleted... To me, they appear exactly as the two first menu entries.

---

### Post by hamiltonpb on 2013-01-17
One thing more. 

I would expect the menu entry to be set to /sda1/EFI/ubuntu/grubx64.efi  in order to boot both Ubuntu and Windows from Ubuntu loader.

Excuse me my insistence: I am trying to learn.

---

### Post by oldfred on 2013-01-17
The menu entries are already in 25_custom, you do not type them at the terminal. You can edit 25_custom with gedit as I posted above.

The first two have the correct efi partition' UUID' in the search .... set = root 

UUID are in BootInfo report or you can see just the UUIDs with this command. 

       ls -l /dev/disk/by-uuid/
    OR
       # To clear cache and get new view:
sudo blkid -c /dev/null -o list

    
And the second two have a Linux partition but want to use Windows files, not sure how that combination would even occur unless there is a new bug in Boot_Repair.

---

### Post by hamiltonpb on 2013-01-17
It is now working like a charm! At first boot, however, it didn't worked and I had to acces bios setup to boot ubuntu. However, starting the system again, everything was fine.

Many thanks for your patience.

---

### Post by oldfred on 2013-01-17
Glad it is working. :)

---

