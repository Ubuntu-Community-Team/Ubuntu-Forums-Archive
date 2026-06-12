---
title: "Run Linux off of USB hard disk?"
date: 2021-02-09
forum: Installation &amp; Upgrades
---

### Post by username2758 on 2021-02-09
Hello all,

So I've been thinking about the possibility of running an entire operating system off of a USB hard disk for testing purposes.

Is it possible?

Also, how would this set up conflict with my existing M.2. SSD which already has the GRUB files in order to boot properly?

No conflict at all?

Thanks!

---

### Post by C.S.Cameron on 2021-02-09
If you want a USB Hard disk that will boot on both BIOS and UEFI computers look at this [https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step)

---

### Post by tea for one on 2021-02-09
In order to avoid conflict with existing GRUB files on your M.2.SSD, then isolate, de-activate or physically remove the drive before installing Ubuntu on your USB hard disk.

Ubuntu will install GRUB on the first available drive, therefore it is better to only have the [COLOR="#0000FF"]target[/COLOR] drive accessible during installation.

Boot each system independently via UEFI boot screen 

Boot priority can be controlled by UEFI

Each OS should be installed in UEFI mode with GPT

Each drive should have EFI partition

Each drive should have grub (if both Linux)

Ensure that you have different UUIDs for each OS

---

### Post by username2758 on 2021-02-09
> **C.S.Cameron said:**
> If you want a USB Hard disk that will boot on both BIOS and UEFI computers look at this [https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step)

That  is a very good guide, thanks! Kind of intricate yes, but will give it a  try. It would be a good idea if somebody created a program or little  script to make a bootable USB device like this!

Apparently I can  only install operating systems on UEFI mode with my pre-built mini-pc  from Lenovo. Do you think it's still possible?

> **tea for one said:**
> In order to avoid conflict with existing GRUB files on your M.2.SSD, then isolate, de-activate or physically remove the drive before installing Ubuntu on your USB hard disk.

Is it possible to de-activate any disks (SSD or HDD) via BIOS settings?

I know one can manually set a list of booting device priority in the BIOS, but if I set a "USB-HDD" on the top of the boot list, why will it still conflict with my existing primary SSD?

Wouldn't it be the same situation as booting a Live CD or Live USB with an existing primary hard disk containing the bootloader?

---

### Post by tea for one on 2021-02-09
Just to clarify for future advice and to avoid confusion:-

[LIST]
[*]Are you interested in a live USB with persistence?
[*]Or, do you want a full separate installation with username, password etc?
[*]
[/LIST]
My comments are based on a **full** installation to a separate device.
> **username2758 said:**
> 

Is it possible to de-activate any disks (SSD or HDD) via BIOS settings?
Yes, that is perfect if your UEFI firmware has the setting.

> I know one can manually set a list of booting device priority in the BIOS, but if I set a "USB-HDD" on the top of the boot list, why will it still conflict with my existing primary SSD?

There will be no conflict [COLOR="#0000FF"]after[/COLOR] you have installed to your separate USB-HDD.
As I mentioned previously, the GRUB problem can occur [COLOR="#0000FF"]during the installation process of the second OS[/COLOR], therefore only have the[COLOR="#0000FF"] target[/COLOR] drive accessible.
> Wouldn't it be the same situation as booting a Live CD or Live USB with an existing primary hard disk containing the bootloader?
A live session will not overwrite or interfere with existing GRUB - unless you [COLOR="#FF0000"]explicitly[/COLOR] want to change, repair or re-configure GRUB.

---

### Post by username2758 on 2021-02-09
> **tea for one said:**
> Just to clarify for future advice and to avoid confusion:-

[LIST]
[*]Are you interested in a live USB with persistence? 
[*]Or, do you want a full separate installation with username, password etc? 
[/LIST]
My comments are based on a **full** installation to a separate device.

Of course I want a separate, full installation of Linux on a USB device. Guess I made that clear.

The only reason I asked about the possibility of conflict is because I never tried this before, and thought to myself "oh, if there are two different hard disks with each having its own bootloader, then could there be conflict?".

But now I guess it's settled. According to you, the only possible GRUB issue can occur during installation, not initialization. Therefore, it's settled.

All that is left now is find that BIOS settings that disables the SSD or HDD completely. I never found one motherboard that has it. But if it does exist, then it would save a lot of time for sure.

---

### Post by oldfred on 2021-02-09
If you do not have UEFI setting to disable internal drive, then review this old bug report on where grub in UEFI boot mode installs.
My motherboard has disable as one of options on setting drives with AHCI & RAID.

I have installed multiple times to external flash drives & SSD. Bit surprised on how fast SSD was, expected USB3 port to be slower.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

Before I found above work around, it used to just install grub to my internal drive.
I found I could manually edit the 3 line grub.cfg in /EFI/ubuntu/grub.cfg with my main working install's ESP. And then added boot of external to 40_custom.
But external drives directly boot from UEFI using /EFI/Boot/bootx64.efi, just as the live installer does. Slightly different version of bootx64.efi with live installer & full install. You then must have an ESP on external drive & boot files in that ESP.

---

### Post by tea for one on 2021-02-09
> **username2758 said:**
> All that is left now is find that BIOS settings that disables the SSD or HDD completely. I never found one motherboard that has it. But if it does exist, then it would save a lot of time for sure.

It certainly does exist in many iterations of UEFI.

However, in your case, you will have to examine the settings/features/configurations of your Lenovo UEFI.

There does not seem to be any great consistency in UEFI firmware settings of individual vendors.

---

### Post by C.S.Cameron on 2021-02-10
For a less complex alternative to the link I posted see: [https://askubuntu.com/questions/1300454/easy-full-install-usb-that-boots-both-bios-and-uefi](https://askubuntu.com/questions/1300454/easy-full-install-usb-that-boots-both-bios-and-uefi)

You can flash it to disk using mkusb, Rufus, Etcher, Disks or dd.

The image file was created by sudodus, (the creator of **mkusb**). It works with an SSD but overwrites the whole drive.

---

### Post by username2758 on 2021-02-10
> **C.S.Cameron said:**
> For a less complex alternative to the link I posted see: [https://askubuntu.com/questions/1300454/easy-full-install-usb-that-boots-both-bios-and-uefi](https://askubuntu.com/questions/1300454/easy-full-install-usb-that-boots-both-bios-and-uefi)

You can flash it to disk using mkusb, Rufus, Etcher, Disks or dd.

The image file was created by sudodus, (the creator of **mkusb**). It works with an SSD but overwrites the whole drive.
Oh my God, thank you Cameron! This looks much easier than the other method.

Just one question: with a full install USB drive of Ubuntu for example, will I be able to carry it around and plug it into any other motherboard and make it boot to the OS regardless of any driver compatibility issues? IIRC, with Microsoft Windows you can't do that because of either the motherboard or the previously installed drivers. Not sure though.

---

### Post by C.S.Cameron on 2021-02-10
This image should boot on any computer that a Live Ubuntu USB will boot from.
No proprietary drivers have been added.
It has been tested on a variety of computers, so far so good.
It would need to be modified if you want to use it for installing Ubuntu.
I can supply instructions for that also.
Let us know how it works for you.

---

### Post by C.S.Cameron on 2021-02-10
Oops! double post.

---

### Post by username2758 on 2021-02-10
> **C.S.Cameron said:**
> This image should boot on any computer that a Live Ubuntu USB will boot from.
No proprietary drivers have been added.
It has been tested on a variety of computers, so far so good.
It would need to be modified if you want to use it for installing Ubuntu.
I can supply instructions for that also.
Let us know how it works for you.
Thanks Cameron. I think I'm finally starting to understand how it all works: Full Install USB Vs. Persistence Install USB ([https://askubuntu.com/questions/1227845/running-live-usb-on-2-different-pcs](https://askubuntu.com/questions/1227845/running-live-usb-on-2-different-pcs)).

Just could not understand what you said here: "it [the image] would need to be modified if you want to use it for installing Ubuntu".

From the last link you posted containing a tutorial ([https://askubuntu.com/questions/1300...-bios-and-uefi]("https://askubuntu.com/questions/1300454/easy-full-install-usb-that-boots-both-bios-and-uefi")), the first reply reads as follows: "Install Ubuntu from a Pre-built Image File". Doesn't that mean it's already a Ubuntu image?

I would like to try a full installment of Ubuntu on a USB flash drive first, as I never tried this procedure before.

Sorry for my ignorance.

---

### Post by C.S.Cameron on 2021-02-10
> **username2758 said:**
> 
Just could not understand what you said here: "it [the image] would need to be modified if you want to use it for installing Ubuntu".

Many people use Live USB's to install Ubuntu. A Full install needs to be modified to install Ubuntu. For instance if you want to install Ubuntu on a friend's computer using the SSD. This is probably off topic for this thread. Sorry for the confusion.

> **username2758 said:**
> 
From the last link you posted containing a tutorial ([https://askubuntu.com/questions/1300...-bios-and-uefi]("https://askubuntu.com/questions/1300454/easy-full-install-usb-that-boots-both-bios-and-uefi")), the first reply reads as follows: "Install Ubuntu from a Pre-built Image File". Doesn't that mean it's already a Ubuntu image?

[https://phillw.net/isos/linux-tools/uefi-n-bios/dd_unb_ubuntu-20.04_15GB_2020-06-26.img.xz](https://phillw.net/isos/linux-tools/uefi-n-bios/dd_unb_ubuntu-20.04_15GB_2020-06-26.img.xz) Will download the image file, you can use Rufus, Etcher, mkusb, etc to flash it to SSD or USB.

> **username2758 said:**
> 
I would like to try a full installment of Ubuntu on a USB flash drive first, as I never tried this procedure before.

Good idea, Install should only take about half an hour. Minimum flash drive capacity is 16GB.

OS will run faster on SSD than on USB.

---

### Post by username2758 on 2021-02-10
> **C.S.Cameron said:**
> [https://phillw.net/isos/linux-tools/uefi-n-bios/dd_unb_ubuntu-20.04_15GB_2020-06-26.img.xz](https://phillw.net/isos/linux-tools/uefi-n-bios/dd_unb_ubuntu-20.04_15GB_2020-06-26.img.xz) 

Will download the image file, you can use Rufus, Etcher, mkusb, etc to flash it to SSD or USB.


Thanks again!

So just to make sure: If I follow [**this**]("https://askubuntu.com/questions/1300454/easy-full-install-usb-that-boots-both-bios-and-uefi") tutorial I will be making a full install of Ubuntu on a USB disk, not a persistent install. Correct?

Only asking because I saw a "Persistent live" option in mkusb, but no "Full install" option.

 [[IMG]https://www.howtogeek.com/wp-content/uploads/2019/05/mkusb_13.png[/IMG]]("https://www.howtogeek.com/wp-content/uploads/2019/05/mkusb_13.png")

I have a spare 120GB SSD for this procedure.

---

### Post by CelticWarrior on 2021-02-10
The option should be "cloning" in this case. The ISO is already an image of a full installation.
MKUSB's persistent live option takes a compatible live (and installation) Linux ISO, unpacks it and writes to the target alongside with a writable file system, the "persistent" side of the equation.

If you're using a 120GB SSD then you want to boot a live session after "burning" it and use GParted to extend the root partition.

---

### Post by C.S.Cameron on 2021-02-11
Yes as CelticWarrior says, just select option "c" **Cloning iso file...** for flashing the image to disk using mkusb. 

I will clarify the linked Ask Ubuntu answer.

---

### Post by username2758 on 2021-02-11
Thank you both! I will give it a try later today.

Out of curiosity, if I flash the proper modified .ISO using Startup Disk Creator from Ubuntu it won't work the same?

As it is not a Persistent Install but a Full Install on USB, do I really need mkusb or Rufus for this procedure to work?

---

### Post by username2758 on 2021-02-11
Hey it's me again!

Just trying this out and came up with a doubt...

Have already downloaded the modified .ISO and installed mkusb:

[[IMG]https://i.ibb.co/ZWwbqB3/mkusb1-2021-02-11-15-38-43-jpg.png[/IMG]]("https://ibb.co/ZWwbqB3")

Now after selecting option "Cloning iso file" and browsing for the downloaded modified image, mkusb asks me this:

[[IMG]https://i.ibb.co/rFmSPjX/mkusb2-2021-02-11-15-39-38-jpg.png[/IMG]]("https://imgbb.com/")

What is it? Can I proceed? I didn't need to decompress or extract anything after downloading the modified .ISO.

I'm sure the target device is correct (/dev/sdb). It is a USB SSD drive!

---

### Post by Dennis N on 2021-02-11
You need to install to a partition. sdb is a drive. sdb1 is a partition. Did you make the necessary partitions on the drive?
Edit: You can ignore this comment. It's not related.

---

### Post by username2758 on 2021-02-11
> **Dennis N said:**
> You need to install to a partition. sdb is a drive. sdb1 is a partition. Did you make the necessary partitions on the drive?
Edit: You can ignore this comment. It's not related.
Hey Dennis!

I didn't create no partitions or whatever on the spare drive, only formatted and deleted all previously existing partitions.

But hey, it worked! Yay! On this Sata-3 type SSD via USB it is working buttery smooth! :D

Now what if I want to dual-boot with another Linux distribution on this spare drive? Is this procedure possible? And if so, is it too difficult to do?

---

### Post by C.S.Cameron on 2021-02-11
> **username2758 said:**
> 
What is it? Can I proceed? I didn't need to decompress or extract anything after downloading the modified .ISO.


As you have discovered, the correct answer is to select "YES". No need to format or create any partitions or extract anything, mkusb's flash process will do everything. 

Do you want to dual boot Full installs of other Linux OS's? If so follow the instructions for dual boot on their homepage.

Another method is to install the other OS to a separate drive and then use GParted to copy/paste the other OS's root partition from it's drive to the SSD. once complete boot the SSD and run "sudo update-grub" to add the new OS to Ubuntu's boot menu.

It is easy to add multiple bootable OS ISO files to the Ubuntu SSD and boot them using Ubuntu's GRUB. Have a look here: [https://askubuntu.com/questions/1251729/20-04-booting-iso-from-grub-menu/1251782#1251782](https://askubuntu.com/questions/1251729/20-04-booting-iso-from-grub-menu/1251782#1251782)

---

### Post by username2758 on 2021-02-12
> **C.S.Cameron said:**
> Do you want to dual boot Full installs of other Linux OS's? If so follow the instructions for dual boot on their homepage.
I'm sorry, where?

I want to try and dualboot full installs of other Linux OS's and run them from a single USB device, like we just did here on this thread with Ubuntu and my 120GB SSD via USB.

Is it possible or do we still need to have a modified .ISO for each Linux OS?

---

### Post by C.S.Cameron on 2021-02-13
> **username2758 said:**
> I'm sorry, where?

I want to try and dualboot full installs of other Linux OS's and run them from a single USB device, like we just did here on this thread with Ubuntu and my 120GB SSD via USB.

Is it possible or do we still need to have a modified .ISO for each Linux OS?

The image file you flashed provides all the bootloader you need.

For each new Ubuntu based OS, create a new ext4 partition of adequate size, (8GB or more). 
Use the **Something else** option while installing. 
Select the new partition for / and select format.
Do not select format on any other partitions.
Select the USB for boot loader installation.
Run install giving location, username, password etc.

Other versions of Linux may have their own methods for creating a dual boot install. Please see their homepage for installation instructions, I only do Ubuntu.

If the new OS boots using GRUB2, another safe method of adding a different Linux OS to the SSD is first to install it to it's own USB drive and confirm that it is working.

Next create free space on the Ubuntu SSD a little larger than the new OS root partition..

Boot the computer using a Live Ubuntu or Live GParted USB. Plug in the new OS USB and use GParted to copy/paste the new OS root partition to the space created for it on the Ubuntu SSD.

When complete remove the USB's and boot Ubuntu. Run **sudo update-grub** to add the new OS to Ubuntu's boot menu.

---

