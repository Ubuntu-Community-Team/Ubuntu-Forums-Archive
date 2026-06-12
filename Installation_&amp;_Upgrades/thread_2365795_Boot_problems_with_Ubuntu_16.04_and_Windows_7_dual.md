---
title: "Boot problems with Ubuntu 16.04 and Windows 7 dual boot"
date: 2017-07-10
forum: Installation &amp; Upgrades
---

### Post by paul1764 on 2017-07-10
I am sorry if this is a question that has already been answered, but I  have tried many things based on this forum and stack exchange, with  nothing working. If I missed a post that anyone thinks would be helpful, I'd be happy  to read it.

I am trying to install Ubuntu 16.04.2  64-bit on a computer that already has Windows 7 installed. Windows 7 is  installed on an SSD, but the computer also has a HDD installed, which is  where I would like to install Ubuntu, because there is more space on  the HDD.

What I have  done:
[LIST=1]
[*]Checked that windows is installed in EFI mode  (there is an EFI partition on the  SSD) 
[*]Made an ubuntu liveUSB using [Rufus 2.15]("https://rufus.akeo.ie/") 
[*]The best Rufus settings  were:
[LIST=1]
[*]GPT for UEFI, DD image 
[*]And I had to  change my computer's boot mode to Legacy/CSM/BIOS  mode 
[*]If I didn't do 2.1 and 2.2, I could  not see the internal SSD and HDD during installation (I know that seems  contradictory, with a UEFI image and BIOS boot mode, but I tried many  other settings, and this was the  best) 
[*]Even with these settings, the ubuntu  installer never recognized that windows was installed (there was never  an "install alongside"  option) 
[/LIST]
  
[*]Installed  using custom partitions:
[LIST=1]
[*]One 50 GB partition for  / 
[*]One 8 GB partition for  swap 
[*]I told the installer to put grub on  the first partition of the SSD, which is the EFI partition according to  windows disk  management. 
[/LIST]
  
[*]Grub  installation failed, and then the installer would not respond, so I  killed it. 
[*]I then tried using boot-repair  to fix the lack of grub installation, both from my ubuntu liveUSB, and a  boot-repair USB (but I could never connect to the internet when booting from the boot-repair USB). 
[*]That never worked 
[*]After running boot repair, the most recent report I got is here: [paste2.org/PN5h6yw9]("http://paste2.org/PN5h6yw9") 
[/LIST]

I realize I have tried so many things that it may in fact be easier to start over at this point. If that is the case, I can erase my current installation, install again, and then run boot-info and ask for help again.

Any  help is appreciated, thank you in advance.

---

### Post by yancek on 2017-07-10
The default for windows 7 installs is to use MBR rather than UEFI and your boot repair output does show both windows 7 and Ubuntu as MBR install.  Problem is that you have windows boot code in the MBR and it is very difficult to boot any Linux from windows although possible.

Your output also shows that both windows 7 and Ubuntu are installed on the 465GB drive.  Is that what you meant to do?  It shows GPT partitioning which will not work with windows unless you use UEFI also.  I see in the output a 4GB and 8GB flash drive so I'm wondering what and where your SSD is?  Is there any unallocated space on it to install.

---

### Post by oldfred on 2017-07-10
@yancek
Boot-Repair uses bootinfoscript as first part of its report. And bootinfoscript does not include the newer NVMe drives in its parsing of all drives.
[https://github.com/arvidjaar/bootinfoscript/issues/5](https://github.com/arvidjaar/bootinfoscript/issues/5)

Others have had issues with NVMe drives, but some have had to update firmware on those drives and/or UEFI so drives are correctly seen in UEFI.

---

### Post by paul1764 on 2017-07-10
@yancek: I didn't think MBR and UEFI were exclusive, isn't MBR a partitioning scheme, and UEFI is a type of firmware? Or do you mean that they are incompatible?
The 465GB drive is the HDD, and ubuntu is installed there. Windows is definitely installed on the SSD, which is about 225GB, it is listed as /dev/nvme0n1, and on line 145 in the pastebin, you can see /dev/nvme0n1p5 is NTFS OS, which is the C:\ drive. So I think boot-repair is seeing my SSD, even though it is NVME. 

I had made some unallocated space on the 465GB HDD to install ubuntu, but that is no longer there because the install mostly completed, except for installing grub. You can see the root directory and swap partitions at sda3 and sda4

I will make sure the firmware for my NVME drive is updated.
Update: I checked using Microsoft Device Manager, and my NVME firmware is up to date.

---

### Post by oldfred on 2017-07-10
While not totally exclusive, the UEFI standard is gpt and the BIOS standard is MBR.
Windows is exclusive and only works that way.

Ubuntu can use MBR, the Ubuntu installer is often on MBR and can boot in either UEFI or BIOS boot mode. But MBR not really recommended for full installs in UEFI mode.

You can use gpt with BIOS boot mode. I did for years and had Windows XP on a separate MBR drive.

Boot-Repair seems to work with the NVMe drives as Boot-Repair is really just running Linux commands that all now support NVMe drives. It just is the summary report does not include all the info on a NVMe drive. The bootinfoscript is about the first 1/3 of the entire Boot-Repair summary report, and that is what is not yet updated.

---

### Post by yancek on 2017-07-10
> @yancek: I didn't think MBR and UEFI were exclusive, isn't MBR a  partitioning scheme, and UEFI is a type of firmware? Or do you mean that  they are incompatible?

With MBR, you need some small part of the boot code in the first sector of the drive which basically then points to the boot files.  MBR and GPT partitioning are different as with an older MBR system you are limited to 4 primary partitions while with GPT you can have up to 128 partitions, all primary.  Other factors dealing with UEFI and dual-booting are better explained at the site below which is the official Ubuntu documentation.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

On line 141 of your boot repair, you see an ESP (EFI) partition.  You don't have an EFI partition on the larger drive where you installed Ubuntu and I doubt you have the Ubuntu EFI files on the windows drive.  Not sure exactly what your intentions are but if you want windows EFI on the SSD and Ubuntu in Legacy/MBR on the other drive, you can do that but as far as I know, you would then need to select one of the drives on boot as you won't be able to boot the EFI (windows) drive from the other drive with Ubuntu/Grub nor will you be able to do the reverse.  I do that on my laptop with no problems although I don't use/boot the second drive very often so it's not that inconvenient.

Read the UEFI link above at the site above and if you have questions, post back.

---

