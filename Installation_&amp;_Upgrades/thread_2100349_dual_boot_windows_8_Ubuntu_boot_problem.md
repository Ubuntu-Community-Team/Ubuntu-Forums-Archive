---
title: "dual boot windows 8/ Ubuntu boot problem"
date: 2013-01-01
forum: Installation &amp; Upgrades
---

### Post by Mireille on 2013-01-01
Hello,
I have a problem after installing Ubuntu in dual boot with windows 8. I am not able to start neither Ubuntu nor Windows. I would be very grateful if you could help me.
Here is what I did:



[COLOR=#000000][FONT=times new roman]I have a new fujitsu A532 with windows 8 pro installed. 
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]I wanted to add ubuntu in dual boot.[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]In the Bios I disabled FastBoot.[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]SecureBoot is enabled (it can't be disabled it in the Bios; or at least I don't know how)[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]I first tried the install of Ubuntu with DVD but it didn't boot on the DVD even with DVD set in first boot order.[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]I  then tried the Live USB (with unetbootin-windows), Ubuntu-Secure 12.10  64 bits: the installation process started but then interrupted while  choosing the keyboard.[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]I then decided to install Ubuntu 12.10 (it detected the presence of Ubuntu-Secure and I  decided to delete Ubuntu-secure and do a new installation of ubuntu). The installation was successfull.[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]But then when rebooting it gives me following message:[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]"[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Secure Boot[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Image failed to verify with *ACCESS DENIED*[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Press any key to continue[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman][Continue][/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]and[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Warning[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Bootable Device was not found[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]{Continue][/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]"[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]and I am not able to launch neither Ubuntu nor Windows (I tried Ubuntu and windows as first boot order)[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]I then used boot repair with "recommended repair", but the problem remains.[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Here is the Boot info summary:[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]http://paste.ubuntu.com/1485617/[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]
[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]I would be very grateful if you could help me. Thank you very much in advance.[/FONT][/COLOR]
[COLOR=#000000][FONT=times new roman]Mireille Dondlinger[/FONT][/COLOR]

---

### Post by darkod on 2013-01-01
I am not sure about the Access Denied message, that is a secure boot message. 12.10 is supposed to be compatible with secure boot so that shouldn't be a problem, but it seems it is.

What I am worried about is that the fdisk partition list shows only the ubuntu partitions on the disk. It seems you installed ubuntu over windows, not next to it.

You said you deleted the Ubuntu Secure partitions, is it possible you deleted the windows partitions too?

Did you have any important data in windows?

---

### Post by presence1960 on 2013-01-01
Darkod is correct, it appears you wiped the windows 8 OS partition. Hopefully you have made recovery media or have made an image of your partitions.

When you try installing Ubuntu again make sure you boot the CD/DVD from UEFI mode since Windows 8 is in all probability installed in UEFI.

---

### Post by darkod on 2013-01-01
> **presence1960 said:**
> Darkod is correct, it appears you wiped the windows 8 OS partition. Hopefully you have made recovery media or have made an image of your partitions.

When you try installing Ubuntu again make sure you boot the CD/DVD from UEFI mode since Windows 8 is in all probability installed in UEFI.

There is uefi grub on the uefi system partition. I am trying to stay clear from uefi as long as possible so I haven't used it yet, but having it present on the uefi system partition should be evidence enough that ubuntu is installed correctly in uefi mode, right? Or not?

Looks like the installation was made correctly in uefi mode, but over windows instead next to it.

---

### Post by Mireille on 2013-01-01
Thank you for your quick answers. 
I am quite sure that when installing ubuntu secure I installed it in a newly created partition.
Then when installing Ubuntu I installed it over ubuntu secure.
Is there a way to check if windows is still there ?
I have no important data on it. Just a new installation of windows 8. 

Presence1960, you say "When you try installing Ubuntu again make sure you boot the CD/DVD from UEFI". How to do this ? I don't know in which mode I booted it.

Thank you for your help.
Mireille

---

### Post by presence1960 on 2013-01-01
> **darkod said:**
> There is uefi grub on the uefi system partition. I am trying to stay clear from uefi as long as possible so I haven't used it yet, but having it present on the uefi system partition should be evidence enough that ubuntu is installed correctly in uefi mode, right? Or not?

Looks like the installation was made correctly in uefi mode, but over windows instead next to it.

Didn't catch the second line that has grub on it.

---

### Post by darkod on 2013-01-01
The fdisk output is pretty clear, but you can double check. Boot the ubuntu cd in live mode (Try Ubuntu), and open Gparted.

Look at the existing partitions. Are there any NTFS partitions on the disk? You can post a screenshot of Gparted if you want, or if you have any questions.

Booting in uefi mode is considered when you boot the cd/usb in uefi mode. On systems that support uefi, the dvd drive will exist as two different bootable devices. Uefi dvd drive, and just dvd drive. It's usually best to use the boot menu of the computer (most new computers will show a boot menu if you hit F12 or another key immediately while booting up), if it has one, and you can select what you want to boot directly. Alternatively set it in bios. In that case, the uefi dvd needs to be before the legacy dvd.

---

### Post by Mireille on 2013-01-01
Here is in attachement the screenshoot of gparted. What is strange is that before installing Ubuntu, I had 
a drive C of 75G with windows
a drive D of about 300G
and a partition that I created for Ubuntu of 50G.
Looks as if one big partition was created after installing Ubuntu. 
No idea how this happened.
But in fact, it seems that I have to reinstall windows. 
Should I create a new partition before installing windows ?
And which version of Ubuntu install afterwards ? Secure or not, 12.04 or 12.10 ?

In boot menu I have
Ubuntu
Windows Boot Manager
CD/DVD Drive: Optiacc DVD RW AD/7760H
DriveO HDD: Toschiba
Network: LAN IPv4
USB CD|DVD
USB HDD
Floppy Disk Drive
 
no Uefi dvd drive.

Thank you for your help. I have to stop for today. Will be back tomorrow.
Mireille

---

### Post by Mireille on 2013-01-04
Hello,
In fact, I wiped the windows partition (grrr....)
I did now I complete new install of windows 8. I then shrinked the windows partition, added a new NTFS partition for my docs and left about 60G space unallocated.
I created a ubuntu secure remix 12.10 live USB.
When beginning the installation process of Ubuntu, I get the following message:*The installer has detected that the following disks have mounted partitions:*
*/dev/sda*
[I]Do  you want the installer to try to unmount the partitions on these disks  before continuing?  If you leave them mounted, you will not be able to  create, delete, or resize partitions on these disks, but you may be able  to install to existing partitions there. 
[/I]

I don't know if I have to reply Yes or No.
What I want is to preserve my windows partition and my docs partition and use the unallocated space to install ubuntu (in dual boot with windows) (SecureBoot is enabled and I can not disable it)

Thank you very much if you can answer me.
Mireille

---

### Post by darkod on 2013-01-04
Well, that message says some partitions from the disk are mounted. If you did mount any of the partitions in live mode before starting the install process, don't do that. The disk should not have any of the partitions mounted.

Start the install again with the ubuntu usb and see if you receive the same message.

I don't know how you installed win8, but if you did it in uefi mode you need to start the usb in uefi mode too. I hope you know that and you understand how to do it.

---

### Post by Mireille on 2013-01-04
Thank you for your answer.
I installed windows 8 using the fujitsu recovery DVD I got when buying the laptop (2 weeks ago).
I am quite sure it is in uefi mode.
I don't know what this means exactly: "did you mount any of the partitionss in life mode before starting the install process". I didn't do anything special.
I don't know if the USB starts in uefi mode. As I told before in the boot menu I choose USB HDD (it doesn't say if it is uefi or not). But when booting the usb I get a black screen with in the left top corner something like:
Try ubuntu without installing
Install ubuntu
...
It seems that this means that the boot was in uefi, or not ?

Thank you for your kind help.
Mireille

---

### Post by Mireille on 2013-01-04
I now started the install again. This time no message about mounted disk, but it says:
"This computer currently has no detected operating system"
I can choose:
- erase disk and install ubuntu 
- something else (resize and create partitions yourself...)
Surely its the second choice I have to do. But it intrigates me that windows is not detected. May this give problems afterwards ?
Or do I have to do something before starting installation ?
Thanks,
Mireille

---

### Post by darkod on 2013-01-04
Yes, if windows is not detected it will be an issue later.

1. Do you have Secure Boot enabled in bios?

2. Is the disk in win8 Basic or Dynamic? You can see this in windows Disk Management.

Yeah, if the usb showed you the black grub menu, it should be in uefi mode.

---

### Post by Mireille on 2013-01-04
1. SecureBoot is enabled. I can not disable it in the Bios. I can  disable/enable other options in the Bios but not SecureBoot. It seems to  me that on this laptop it is not possible to disable secureboot when  windows8 is installed. But 12.10 should be compatible with SecureBoot,  isn't it ?
2. The disk is in Basic
Anything to do. Or should I try the installation ?

---

### Post by darkod on 2013-01-04
Yeah, 12.10 should be compatible with secure boot.

If the disk is in basic, that's good.

I have no idea why it can't see windows as installed. Whether you continue the install or not is up to you.

---

### Post by YannBuntu on 2013-01-04
hello
[QUOTE=Mireille;12438328But 12.10 should be compatible with SecureBoot,  isn't it ?[/QUOTE]



First use Windows tools to reduce the Windows partition to 60GB, then reinstall Ubuntu alongside Windows (via the "Something else" option at [this screen]("https://help.ubuntu.com/community/GraphicalInstall#Installation_type")).
Then reboot the pc. If any problem, run Boot-Repair's Recommended Repair and tell us the new URL that will appear.

FYI, 12.10 is SecureBoot compatible for some systems, but on some systems it still has problems, so you may need to disable UEFI, we will tell you later if necessary.

---

### Post by Mireille on 2013-01-05
Thank you for the answers.
I have still another question:
On the "installation type" screen I now have this: see photo of the screen attached.
Concerning the "device for boot loader installation" is /dev/sda the right choice, or should it be /dev/sda7 ?
Sorry for all this questions, but I really want to avoid to do the same mistakes again and having to reinstall windows again.
Thank you very much for your help,
Mireille

---

### Post by Mireille on 2013-01-05
I would be very grateful if somebody could give me an advice about this:
Should I choose as "device for boot loader installation":
- /dev/sda
- /dev/sda7 (ubuntu partition)
- a boot partition (and add an entry for ubuntu in windows 8)( as explained in this tutorial
[http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/](http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/)
Thank you for your help,
Mireille

---

### Post by darkod on 2013-01-05
No, you don't need separate /boot partition. I can't see what would be its use.

As for the bootloader location, I don't think it matters on uefi system since you will not be using grub2 to boot. You will be using the uefi boot manager.

I haven't installed on uefi so far, so I can't tell you 100%, but leave the bootloader destination as /dev/sda, the MBR of the disk. Let it put grub2 there even though it will not be using it. I would try it like that.

---

### Post by YannBuntu on 2013-01-05
> **darkod said:**
> leave the bootloader destination as /dev/sda, the mbr of the disk. Let it put grub2 there even though it will not be using it.

+1

---

### Post by Mireille on 2013-01-05
Hello,
I am back again ;-)
I first tried installing ubuntu secure. This failed giving an error message during loading of the files [error 5] input/ouput error. Same message as first time I tried the install, even as I did a new download of ubuntu secure.
Then I deleted the ubuntu partition and did a new installation of ubuntu (not secure).
The installation was successful.
I am not able to boot ubuntu, but I am able to boot windows.
Boot repair gives this result:
[http://paste.ubuntu.com/1500627/](http://paste.ubuntu.com/1500627/)
and this screen: ubuntu_screenshot_error.jpg

Can you please tell me how to do this:
create a partition /boot/efi start of the disk ?
Image gparted_screenshot shows my partitions.
To create the new partiton I suppose I have to shrink a partition to create unallocated space. But which partition to shrink ? And "start of the disk", does this mean the partition has to be the first partition of the disk ?

Another question: in boot-repair advanced options: should I check SecureBoot (as secureboot is enabled in my Bios?)

Thanks again for your help,
Mireille

---

### Post by darkod on 2013-01-05
You already have UEFI System Partition, that's /dev/sda2. You don't need to create another one.

But it seems grub2 didn't install. Maybe that error message mentioning Locked ESP is the reason. If the UEFI System Partiiton is locked (for some kind of protection), that might have prevented grub2 to be installed.

I don't know if boot-repair can help you in this case, probably Yann will know better.

You could try to use chroot to enter into the installation from live mode and try to add grub2. Lets see what Yann says and if all else fails you can try the chroot.

---

### Post by YannBuntu on 2013-01-05
> **Mireille said:**
> Boot repair gives this result:
[http://paste.ubuntu.com/1500627/](http://paste.ubuntu.com/1500627/)
and this screen: 
```
An error occurred during the repair.

Locked-ESP detected. You may want to retry after creating a /boot/efi partition (FAT32, 100MB~250MB, start of the disk, boot flag). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot/efi partition:] option of [Boot Repair].

```

Your current EFI partition (sda2) is read-only, this prevents GRUB from installing in it. Boot-Repair suggests to create a 2nd EFI partition for installing GRUB in it. You can mark yourself "Affected" by this bug: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)

> **Mireille said:**
> which partition to shrink ? And "start of the disk", does this mean the partition has to be the first partition of the disk ?

If possible, it should be included inside the first 130GB of the disk.

Currently you have:
```
Number  Start   End    Size    File system     Name                          Flags
1      1049kB  316MB  315MB   ntfs            Basic data partition          hidden, diag
2      316MB   420MB  105MB   fat32           EFI system partition          boot
3      420MB   555MB  134MB                   Microsoft reserved partition  msftres
4      555MB   105GB  105GB   ntfs            Basic data partition
5      105GB   430GB  325GB   ntfs            Basic data partition
6      430GB   434GB  4000MB  linux-swap(v1)
7      434GB   500GB  65.6GB  ext4
```

I recommend you reduce sda4 in order to create 200MB free space, then create your new EFI partition (FAT32, 'boot' flag) in it. Write on a paper the name of this new partition (probably sda8).
Then run Boot-Repair --> Advanced options --> "GRUB location" tab --> select "Separate /boot/efi: sda8". Tell me the new URL that will appear.
Then reboot and tell me what you observe.

---

### Post by Mireille on 2013-01-06
I did as suggested:
I created a new efi partition (sda8).
Then selected in Boot-repair Separate /boot/efi: sda8
After clicking apply, it installed grub.
Here is the url
[http://paste.ubuntu.com/1503553/](http://paste.ubuntu.com/1503553/)
When rebooting I get the message:
" 
Secure Boot 
Image failed to verify with *ACCESS DENIED"
Press any key to continue
[Continue]
"
After pressing a key, windows starts.

I have not done the following (as do not know how):
"Please do not forget to make your BIOS boot on sda8/EFI/ubuntu/grubx64.efi file!"

In the Bios ubuntu is set at first boot order.

What should I do now ?
Thanks for your help.
Mireille

---

### Post by YannBuntu on 2013-01-06
Via Gparted, remove the 'boot' flag from sda2. Then run the Recommended Repair again.

---

### Post by Mireille on 2013-01-06
I removed boot flag from sda2 and run boot-repair again.
(I selected again "Separate /boot/efi: sda8"; it was again sda2 by default; don't know if this is normal)
[http://paste.ubuntu.com/1504256/](http://paste.ubuntu.com/1504256/)
When booting the laptop:
Same message "Secure Boot ..." as before, then a short screen saying something like "analyse and verification ..." during a few seconds, then windows starts.

Shouldn't I try to check SecureBoot in Bootrepair ?

Thanks,
Mireille

---

### Post by YannBuntu on 2013-01-06
Your pc continues to boot on sda2 even though it has no 'boot' flag ! this does not comply with UEFI specifications :-(

You seem to have both a locked ESP and a locked BIOS... 

Please disable SecureBoot and FastBoot/QuickBoot in your BIOS, then run Boot-Repair again (with the sda8 option), and tell the new URL, then reboot and tell what you observe.

---

### Post by Mireille on 2013-01-08
First, to reply to YannBuntu's last message:
- FastBoot was already disabled
- SecureBoot is enabled and I can not disable it
I was near from giving up, when I gave it a last try.

Here is what I did:
- I did a new installation of Ubuntu

- I run Boot repair with the bootrepair SecureBoot option checked
This started a process during with I was asked to type several commands in the command terminal.
All the steps finished successfull.
[http://paste.ubuntu.com/1507339/](http://paste.ubuntu.com/1507339/)
After booting the laptop I get the following screen: ubuntu_screen1.jpg
When I choose "Ubuntu" Ubuntu starts :)
When i choose one of the two windows options I get the following error message: ubuntu_screen2.jpg
So I am able to start Ubuntu but not windows.

- when I run bootrepair with the bootrepair secureboot option unchecked ( [http://paste.ubuntu.com/1507493/](http://paste.ubuntu.com/1507493/)  )
and then boot the laptop, I first get the usual "[COLOR=#000000][FONT=times new roman]Secure Boot[/FONT][/COLOR][COLOR=#000000][FONT=times new roman] Image failed to verify with *ACCESS DENIED*[/FONT][/COLOR]" then after pressing continue Windows starts.

So now I am able to start as well windows as ubuntu, but I have to run boot-repair between each switch (which is of course not a good solution)

I am rather sure that the reason why I can't start ubuntu in the second case is because of the secureboot that I can not disable.

But in the first case why windows can't start ?

Thanks again very much for yor help,
Mireille

---

### Post by YannBuntu on 2013-01-08
> **Mireille said:**
> But in the first case why windows can't start ?


Maybe because Windows doesn't like to be loaded from grub-efi? no really i don't know.

I suggest you run Boot repair with the bootrepair SecureBoot option checked, then go into your BIOS ("boot order" screen), there should be an entry to boot Ubuntu and another to boot Windows. Please tell us if both work?

---

### Post by Mireille on 2013-01-10
After running bootrepair with secureboot option checked.
In the Bios, when selecting to boot ubuntu or windows boot manager, in both cases I return to the same grub screen with 
ubuntu
advanced options for ubuntu
windows uefi bootmgfw.efi

I will stop now. From what I read on the net, I see other people having the same issue. The only solution seems to be to disable secureboot. I wrote a mail to fujitsu support to tell me how to disable secureboot on my laptop. I hope this is possible. 

Anyway, thank you very much for your help. You really do a great job.

---

### Post by shettysid on 2013-03-21
Hi 

Thanks very much for sharing your experience. 
I went through the same steps but did not see light at the end of the tunnel! 

Anyway I have logged my experience as I went through this, you can find it at :
[https://docs.google.com/document/d/1oUkQIR-Ud3EnYzHqFGbiuzjvhZwwDj7apSy5YvHVAXQ/edit?usp=sharing](https://docs.google.com/document/d/1oUkQIR-Ud3EnYzHqFGbiuzjvhZwwDj7apSy5YvHVAXQ/edit?usp=sharing)

Hoping to get more inputs from the community...

cheers
sid

---

### Post by axept on 2013-04-18
Did you get answer from Fujitsu? Have a Laptop and cant disable "Secure Boot". So when trying to boot "Ubuntu" (#1 bootmenu) I get the "Access Denied" msg.

EDIT: Managed to disable the Secure Boot option in BIOS (UEFI).. Had to set "Supervisor password" first..

Disabeled it and now it boots directly to Ubuntu..

---

### Post by oldfred on 2013-04-18
Microsoft has required vendors to enable turning off secure boot if you have hardware access to system. But only some still will boot Windows 8 with secure boot off.
Ubuntu has the Microsoft key and you can install with the signed versions of grub & kernels to boot with secure boot on.
And a few vendors have modified UEFI (against UEFI standard) to only boot the Windows efi file. But Boot-Repair automates a renaming function to make system think it is booting the Windows efi file, but really boots grub2's shim file that has the Microsoft key. Then from grub menu you boot Windows.

---

