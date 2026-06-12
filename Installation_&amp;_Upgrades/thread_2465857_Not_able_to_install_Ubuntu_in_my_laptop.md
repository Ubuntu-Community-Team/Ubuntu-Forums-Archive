---
title: "Not able to install Ubuntu in my laptop"
date: 2021-08-13
forum: Installation &amp; Upgrades
---

### Post by kumarsen26 on 2021-08-13
Hi Team,
I am not able to intall Ubuntu in my HP laptop. I would really like to install Ubuntu as my default operating system. But I couldn't succeed. 

Device and issue details is in below link
[https://askubuntu.com/questions/1295510/not-able-to-install-ubuntu-20-04-alongside-windows-10-pro-dual-boot?noredirect=1#comment2201070_1295510](https://askubuntu.com/questions/1295510/not-able-to-install-ubuntu-20-04-alongside-windows-10-pro-dual-boot?noredirect=1#comment2201070_1295510)

**Model:** HP ENVY Notebook - 15-ah151sa[B]
**Processor: **[/B]AMD A10-8700P Radeon R6[B][B]
**Operating system:**[/B][/B] Windows 10 Pro[B][B][B]
**Bootable device: **[/B][/B][/B]USB[B][B][B][B]
**RAM: **[/B][/B][/B][/B]8GB[B][B][B][B][B]
**Tool used: **[/B][/B][/B][/B][/B]Rufus (Tried almost all options in this tool)[B][B][B][B][B][B]
**Ubuntu downloaded: **[/B][/B][/B][/B][/B][/B]from offical site[B][B][B][B][B][B][B]
**Current OS: **[/B][/B][/B][/B][/B][/B][/B]Windows 10 Pro[B][B][B][B][B][B][B][B]
**UEFI capable: **[/B][/B][/B][/B][/B][/B][/B][/B]Yes**[B][B][B][B][B][B][B]**[/B][/B][/B][/B][/B][/B][/B]

Any help is appreciated.

---

### Post by yancek on 2021-08-13
Give some details on your hardware, at least how new/old it is, processor, RAM and video card.
Did you download Ubuntu from the official site?  Which release did you use?  What software did you use to create a bootable flash drive?  Are you using a USB or DVD?
Did you do an md5 checksum on the iso to verify the download?  Is there currently and operating system on this computer?  If so, what is it?  Is your computer UEFI capable and have you booted to install in UEFI mode? 

I have 2 HP laptops myself and had not trouble installing 20.04 on either so post the answers to the questions above and someone might be able to help.

---

### Post by kumarsen26 on 2021-08-13
Hi Yancek,


I have shared the link which I already posted in askubuntu with details. 
Anyways I am posting here again.


**Model:** HP ENVY Notebook - 15-ah151sa
**Processor: **AMD A10-8700P Radeon R6
**Operating system:** Windows 10 Pro
**Bootable device:** USB
**RAM: **8GB
**Tool used: **Rufus (Tried almost all options in this tool)
**Ubuntu downloaded:** from offical site
**Current OS:** Windows 10 Pro
**UEFI capable:** Yes

---

### Post by tea for one on 2021-08-13
First, have you backed up your Windows data?

Next, can you create your bootable usb with Rufus with the following options:-
GPT
UEFI
No persistence

Then check your Windows and UEFI settings:-

_UEFI settings_

Disable Secure Boot
Disable Fast boot 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver)
Disable TPM

_Windows 10_

Backup your data
Turn off Bitlocker 
Do not have any drives encrypted during Ubuntu installation process
Disable Fast Start Up i.e. Windows is not hibernating
Disable applications which manage Intel Optane memory & storage
Windows will have  an EFI partition (needed by Ubuntu later)
Use Windows tools to reduce Windows partition size and create free space
Reboot Windows to allow chkdsk to run
Windows may need AHCI driver
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)

Then boot into your USB and let us know when you are in a live session?

---

### Post by GhX6GZMB on 2021-08-13
> **kumarsen26 said:**
> 
**Tool used: **Rufus (Tried almost all options in this tool)


Don't. Use the defaults, they work. Your USB -drive should look like the attached pic after "burning" with Rufus.

If you don't get a boot, it's 99% a BIOS/UEFI setup problem. USB must be the first boot device, and what 'tea for one' listed as BIOS options are spot on.

---

### Post by kumarsen26 on 2021-08-13
In my BIOS, I am not able to enable AHCI option. Since I am not able to find the advanced setting option. I think it is hidden by HP. any idea how to enable that? and is it must to install Ubuntu? attached screenshot for the same
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288962&stc=1[/IMG]


I have tried without doing AHCI changes. Below are the steps I followed.
I have used Rufus to create bootable image.
Bitlocker disabled.
No encryption.
I booted the USB, First it checked for error.
Then no error found screen came
Then now stuck in loader (if i press down arrow below is the message)
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288965&stc=1[/IMG]

---

### Post by tea for one on 2021-08-14
If you have no obvious setting for AHCI, then I reckon that it is probably OK.

The image is not an error message, it is a picture of your UEFI Settings (System Configuration).

---

### Post by kumarsen26 on 2021-08-14
>  The image is not an error message, it is a picture of your UEFI Settings (System Configuration).

Sorry Now attached the error screen
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288968&stc=1[/IMG]

---

### Post by tea for one on 2021-08-14
There seems to be a certain amount of internet traffic concerning HP & ACPI difficulties.

Some suggest updating the UEFI Firmware for the PC - Is your firmware up to date?

Other suggestions include adding a parameter to grub when you boot the live USB.

When you reach the Grub screen, press E to edit the parameters and add one of these after [COLOR="#0000FF"]quiet splash[/COLOR]

```
acpi=off [COLOR="#0000FF"]or [/COLOR]noacpi [COLOR="#0000FF"]or[/COLOR] acpi=strict
```

I don't know which is better, perhaps try one at a time.

See if this boots into a live session first.

---

### Post by kumarsen26 on 2021-08-14
Thank you..

I have checked, my BIOS is latest version.
I have tried acpi=off. I am able to use live session without installing, But I got error as attached. Is this something needs to worried?
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288969&stc=1[/IMG]


When I try to install with acpi=off, I got below error. 

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288970&stc=1[/IMG]

How do i continue from here? Do I need to try other options as well?

---

### Post by yancek on 2021-08-14
In the second image of your last post, you have an error message "no root file system defined.  Close that message window and in the large window behind it, click on the plus sign in the center left of the window.  You should then get an Edit partition window where you can set the filesystem type (default would be ext4), set  the size of the partition and the Mount point on the right which should be '
If you want a separate /home of /data partition, go through the same process.

---

### Post by kumarsen26 on 2021-08-14
Sorry, There is no action when I click + in the below window

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288971&stc=1[/IMG]

---

### Post by GhX6GZMB on 2021-08-14
Well, your boot is successful and you're in the installer. Congrats.

I use Lubuntu and my installer is a bit different, but still:
Select the /dev/sda field with the mouse, this should enable the "New Partition Table" button. Click that.
Then take it from there.

---

### Post by tea for one on 2021-08-14
> **kumarsen26 said:**
> Sorry, There is no action when I click + in the below window

The gparted screenshot should display the [COLOR="#0000FF"]existing Window[/COLOR]s partitions.

Did you create free space on your disk using Windows tools before starting the installation?
Did you reboot into Windows to allow chkdsk to run?

Is Windows 10 in hibernation state?

---

### Post by GhX6GZMB on 2021-08-14
I don't think that's gparted. It's the Ubiquity installer.

---

### Post by tea for one on 2021-08-14
> **ml9104 said:**
> I don't think that's gparted. It's the Ubiquity installer.

Yes, it is the Ubiquity installer and it is the screen from gparted where existing partitions should appear.

---

### Post by GhX6GZMB on 2021-08-14
> **tea for one said:**
> Yes, it is the Ubiquity installer and it is the screen from gparted where existing partitions should appear.

I get you now, it's unfortunately not clear from the thread that the OP wants a dual-boot system. 
I don't use those and would normally simply flatten the HDD with partitioning/formatting to the desired Linux filesystem.

---

### Post by mIk3_08 on 2021-08-14
> **kumarsen26 said:**
> Sorry, There is no action when I click + in the below window

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288971&stc=1[/IMG]


Here are some easy steps and guide in installing Ubuntu Operating System in your machine.
Just choose which guide you want to successfully install Ubuntu Operating System 
in your machine. This guide helps you a lot in installing Ubuntu System in your machine.
I have used one of this guide and it helps me to successfully install Ubuntu Operating System in my machine.
So Good Luck and enjoy.

BootFromUSB
[HTML]https://help.ubuntu.com/community/BootFromUSB[/HTML]

Installation/FromUSBStickQuick
[HTML]https://help.ubuntu.com/community/Installation/FromUSBStickQuick[/HTML]

Installation/FromUSBStick
[HTML]https://help.ubuntu.com/community/Installation/FromUSBStick[/HTML]

BootFromSD
[HTML]https://help.ubuntu.com/community/BootFromSD[/HTML]

LiveUsbPendrivePersistent
[HTML]https://wiki.ubuntu.com/LiveUsbPendrivePersistent[/HTML]

Installation/LVMOnRaid
[HTML]https://help.ubuntu.com/community/Installation/LVMOnRaid[/HTML]


WindowsDualBoot
[HTML]https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs[/HTML]

---

### Post by kumarsen26 on 2021-08-14
I have installed Ubuntu Dual boot in another HP laptop without any issues which is based on Intel i5 processor. But with this laptop I am struggling to install which is having AMD. 

@tea for one.. I am checking the chkdsk.. will try installing again after that is completed. Also I used **shutdown /s /f /t 0** to completely shutdown

---

### Post by GhX6GZMB on 2021-08-14
I have to agree with tea for one.
I think you've forgotten to shrink your Win10 disk partition before starting this.

---

### Post by tea for one on 2021-08-14
> **ml9104 said:**
> I get you now, it's unfortunately not clear from the thread that the OP wants a dual-boot system. 

Yes, I agree that it is not clear. 
I simply assumed a dual boot is the objective because that is generally the desired result.

It is a good idea to mention that an Ubuntu only PC remains a good choice.

---

### Post by kumarsen26 on 2021-08-14
Still stuck at same place.
1. checked chkdsk, found no error.
2. did complete shutdown of windows using shutdown /s /f /t 0
3. Created(Shrinked) 500GB unallocated space 

Not sure what I am missing. I am ok if only ubuntu can be installed, if that is straight forward.

---

### Post by kumarsen26 on 2021-08-14
Also in Live Session, when I open Gparted only pendrive is showing. No hard disk as shown below
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288974&stc=1[/IMG]

---

### Post by tea for one on 2021-08-14
I am equally as perplexed as you.

Does gnome-disks show any useful info?

Or even via a terminal:-

```
sudo parted -l
```
```
sudo fdisk -l
```

---

### Post by kumarsen26 on 2021-08-14
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288975&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=288976&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=288977&stc=1[/IMG]Attaching the results

---

### Post by GhX6GZMB on 2021-08-14
Obviously, your HDD is not being identified/detected.
But what's all the/dev/loop garbage doing on your USB stick? Somehow cr*p (sorry, snap) is present there. Why? Where did that come from? Never seen that before.
I'm beginning to question the source of your .ISO file.

In your place, I'd reformat the USB drive to FAT32 completely, get a new .ISO from a reputable source, burn it with Rufus using defaults and redo from start.

You've mastered the UEFI boot issue already, it can only get better.

---

### Post by kumarsen26 on 2021-08-14
I have verified the downloaded ISO file with SHA256 checksum.. It is giving expected output. (ubuntu-20.04.2.0-desktop-amd64.iso: OK)
Now I have tried with fresh burning of ISO into USB again. But still the same result  for sudo fdisk -l.

---

### Post by GhX6GZMB on 2021-08-14
I'm stumped as well now. Sorry.
Did you format the USB completely? Not just fast format, but really brute force?

UPDATE:
Just for fun, I did a live boot on one of my laptops and executed the parted and fdisk commands as suggested by tea for one. Here are the outputs:
```
lubuntu@lubuntu:~$ sudo fdisk -l
_**Disk /dev/loop0: 1.59 GiB, 1697615872 bytes, 3315656 sectors  **_                                                                               
Units: sectors of 1 * 512 = 512 bytes                                                                                                        
Sector size (logical/physical): 512 bytes / 512 bytes                                                                                        
I/O size (minimum/optimal): 512 bytes / 512 bytes                                                                                            

Disk /dev/sda: 223.58 GiB, 240057409536 bytes, 468862128 sectors                                                                             
Disk model: KINGSTON SUV5002                                                                                                                 
Units: sectors of 1 * 512 = 512 bytes                                                                                                        
Sector size (logical/physical): 512 bytes / 4096 bytes                                                                                       
I/O size (minimum/optimal): 4096 bytes / 4096 bytes                                                                                          
Disklabel type: dos                                                                                                                          
Disk identifier: 0x7e408a68

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048  61442047  61440000  29.3G 83 Linux
/dev/sda2        61442048 456273919 394831872 188.3G 83 Linux
/dev/sda3       456273920 468857024  12583105     6G 82 Linux swap / Solaris

Disk /dev/zram0: 983.9 MiB, 1031671808 bytes, 251873 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/zram1: 983.9 MiB, 1031671808 bytes, 251873 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

```
```

lubuntu@lubuntu:~$ sudo parted -l
Model: ATA KINGSTON SUV5002 (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  31.5GB  31.5GB  primary  ext4            boot
 2      31.5GB  234GB   202GB   primary  ext4
 3      234GB   240GB   6443MB  primary  linux-swap(v1)

Model: Unknown (unknown)
Disk /dev/zram1: 1032MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1032MB  1032MB  linux-swap(v1)

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: HL-DT-ST DVDRAM GSA-U10N (scsi)                                    
Disk /dev/sr0: 1818MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      1811MB  1815MB  4096kB               EFI

Model: Unknown (unknown)
Disk /dev/zram0: 1032MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1032MB  1032MB  linux-swap(v1)

```

The interesting thing is right at the top: the /dev/loop0 device. A "loopx" something is a storage device that has no partition.
I only have one here, and that's my live boot/installation DVD.

But your USB drive seems to be so filled with dirt that it's unusable for installing Ubuntu. Clean it up first, then we can try helping you.

Period.

---

### Post by tea for one on 2021-08-14
Your flash drive San Disk 16GB has a msdos partition table.

You should remake the boot drive with:-

GPT
UEFI

See if it makes a difference

---

### Post by kumarsen26 on 2021-08-15
1. Formatted(full format) the Pendrive.
2. Reinstalled windows with newly created bootable image (in another pendrive) 
	Secureboot off
	Shrinked drive to get unallocated space.
3. Created new bootable image again using Rufus (GPT, UEFI, FAT32)
4. Tried installing Xbuntu. 


None of the above listed the hdd.


@ml9104 Not sure, even after did full format (not quick format), I can see still all loop0,loop1...


Is it something due to below error ? this error comes only after adding acpi=off
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288982&stc=1[/IMG]

---

### Post by tea for one on 2021-08-15
From your screenshot [COLOR="#0000FF"]Device not added due to errors[/COLOR] could be a clue.
It could be due to [COLOR="#0000FF"]acpi=off[/COLOR] but I do not know.
Also [COLOR="#0000FF"]Is the iommu enabled?[/COLOR] is another clue.

Do you have a UEFI/BIOS setting for iommu?
Try with one of the other acpi parameters?
Also try with Secure Boot on?

---

### Post by kumarsen26 on 2021-08-15
1. I tried with Secure boot turned on 
2. Other params which you have shared not working (brings back the original issue)
3. No, I don't have iommu settings 


but no luck :(

---

### Post by tea for one on 2021-08-15
Did you disable TPM in your UEFI settings?

Probably under Security tab?

---

### Post by kumarsen26 on 2021-08-15
I cannot see TPM settings

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288983&stc=1[/IMG]

---

### Post by tea for one on 2021-08-15
TPM might be Intel only - I'm not sure as I do not have an AMD device.

What is that choice [COLOR="#0000FF"]Administrator Password[/COLOR]?

Does that allow access to more settings?

---

### Post by kumarsen26 on 2021-08-15
No that to set administrator password..

---

### Post by tea for one on 2021-08-15
Well, although we are not making much progress at the moment, I'm pretty sure that there is some way of making the installer recognise your internal HDD.
I have temporarily run out of suggestions.

In the meantime, I would consider installing Ubuntu to an external USB drive.
Perhaps, one of these [COLOR="#0000FF"]tiny non-obtrusive[/COLOR] devices:-

Sandisk Ultra Fit USB 3.1 Flash Drive

[https://shop.westerndigital.com/en-gb/c/usb-flash-drives.SD.SDP](https://shop.westerndigital.com/en-gb/c/usb-flash-drives.SD.SDP)

---

### Post by kumarsen26 on 2021-08-15
Ok.. I also left with no option.. 

Thank you for your time and suggestion.  Let me know if you got some suggestions later.

---

### Post by tea for one on 2021-08-15
The [COLOR="#0000FF"]iommu[/COLOR] issue may be key to this dilemma.
I'm not sure what it is or what it does exactly, but I have seen grub parameter references for AMD devices.
```
amd_iommu=on [COLOR="#0000FF"]and/or[/COLOR] iommu=pt
```
I'm sure that there are other variations

Perhaps, try and include them in a live session when you have time.

---

### Post by kumarsen26 on 2021-08-15
Sorry where to add these params?

---

### Post by tea for one on 2021-08-15
Grub parameters - similar to where you added acpi=off, I think?

---

### Post by yancek on 2021-08-15
One reason a Linux system will not show a windows partition is that hibernation is turned on.  That is the default in windows and some updates in windows will turn it back on if the user had previously turned it off.  Windows won't inform the user this is being done.  In  post 30, you indicate you reinstalled windows so you might try going to the power setting in windows and turning it off to see if windows is then recognized in your Ubuntu installer.  If that doesn't wori, I don't really have any other ideas.  Pretty unusal situation.

---

### Post by oldfred on 2021-08-15
Does system have Optane?  That is more an Intel drive, so may not be on AMD system?
[https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483](https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483)

Have you updated SSD firmware? 
Many systems (even new) need both UEFI firmware & SSD firmware updates. At least check if most current version.

Another HP, needed multiple boot parameters
[SOLVED] HP Envy Ubuntu Windows 10 dual boot
[https://ubuntuforums.org/showthread.php?t=2448727](https://ubuntuforums.org/showthread.php?t=2448727)

---

### Post by kumarsen26 on 2021-08-15
Finally I have installed Ubuntu using Legacy mode in BIOS, since UEFI mode is not allowing me to install. 
But I read UEFI is better than legacy. 


I have used acpi=off though


anything else I need to do?

---

### Post by tea for one on 2021-08-15
> **kumarsen26 said:**
> Finally I have installed Ubuntu using Legacy mode in BIOS, since UEFI mode is not allowing me to install. 
But I read UEFI is better than legacy. 
I have used acpi=off though
anything else I need to do?

Well, that is a complete surprise but I doff my hat to you.

Did you remove Windows 10 completely because that would have been installed in UEFI mode?
You are aware of mixed mode dual boot systems?
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by kumarsen26 on 2021-08-15
Yes I removed windows completely.. as you said it is with UEFI. 

But now can I change ubuntu to UEFI? or it is fine with Legacy mode..

---

### Post by tea for one on 2021-08-15
I would be more interested in another little bit of research.

Can you boot into a live session in UEFI mode again?
Having removed Windows, does the installer find the internal HDD?

---

### Post by kumarsen26 on 2021-08-15
I have tried.. but no.. its not detecting..

---

### Post by tea for one on 2021-08-15
> **kumarsen26 said:**
> I have tried.. but no.. its not detecting..

Thank you for trying.

I wouldn't bother converting to UEFI mode because I suspect that will only lead to unresolved problems already experienced during this thread.

I'm pleased that you have persevered and finally installed Ubuntu.

Legacy Mode **1** -v- UEFI Mode **O** 
A result that will encourage UEFI advocates, like myself, to modify their opinions.    :)

---

### Post by kumarsen26 on 2021-08-16
Yes, I have been tried different options. finally installed it.. but Now I feel Ubuntu is slow. 

and i think it is using only 1 core out of 4. So CPU is always 100%. Though lot of Memory(RAM) is free. 

anything I need to change?

---

### Post by ubfan1 on 2021-08-16
I've seen the acpi=off cause only one CPU to be visible, but the need for that to even boot went away when the firmware was updated.  See [https://www.kernel.org/doc/Documentation/admin-guide/kernel-parameters.txt](https://www.kernel.org/doc/Documentation/admin-guide/kernel-parameters.txt) for another half dozen values you can try instead of "off".  iommu does seem to be a solution I have seen for problems like these.  Did you check the ssd firmware? HP might still require a specific name (bootmgfw.efi?) instead of grubx64.efi, but the /EFI/Boot/bootx64.efi default device boot can get around that.

---

### Post by petescomp on 2021-11-21
i have an 15-ah150na model with the same a10-8700p and have tried a few  times to no avail. Recent talk of win11 and discovering that it would  not be available to me thought i'd better get it working as a backstop  in case support ceases for win 10. After many trials and reboots i have a  method that worked for me. As the laptop now belongs to the Mrs my  install is to an external usb3 disk (a safer option than certain death  if anything went wrong). Anyhow here goes:-

1 update to latest bios in my case F.22
2 Set legacy support to enabled in the bios.
3 Boot a live stick of ubuntu 18.04.6LTS with noacpi nomodeset (this  will hopefully boot the live cd properly so that you be able to make  sure everything works ok)
4 Install as you wish (in my case to the external drive with the grub install to the same external disk)
5 Restart when finished as required.
   Note if your bios is like mine f9 at startup will bring up a boot  menu which has an option to boot from the external disk as the 4th or  5th option.
6 After restart i then updated and then upgraded up to 20.04lts using the software updater.

i now finally have a system that will boot 20.04lts so i'm happy i even installed xubuntu desktop and that works too.

i have tried many different configurations of options and this is the  only one that would work so i'm afraid that's the only information i can  offer. It worked for me but obviouslyi can't guarantee it will work for  you but i think there's a good chance it might. Of course I would  advise you back up your data before doing anything and everything you do  is at your own risk.

Hope that helps and it works for you because i know what it's like banging your head against a brick wall with this stuff.

---

