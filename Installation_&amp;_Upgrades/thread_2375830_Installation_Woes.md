---
title: "Installation Woes"
date: 2017-10-27
forum: Installation &amp; Upgrades
---

### Post by Shmoogly on 2017-10-27
Hi everyone!

Trying to install Ubuntu and having some issues.

I've installed Linux Mint in the past, but that was a long time ago so I don't remember all the details and can't find the disc for checking how I made the bootable device etc.

I'm using Windows 7 on a computer that's from 2010.

I want to install Ubuntu onto a new HDD not external that I just purchased. I'll be putting Mac on there as well, but one step at a time.

I partitioned the new HDD into two sections and then formatted the first one for Ubuntu. I only had the option of NTFS. I'm reading that when you install Linux, you get the option to format the HDD to ext4.

I then used Rufus to create a bootable USB with the settings as per screenshot.

[ATTACH=CONFIG]277300[/ATTACH]

I selected my USB drive as the bootable device from BIOS, but when I get past POST, all I see is it getting stuck at "Verifying DMI Pool Data".

The USB drive seems to be detected by BIOS just fine - it pops up when I go about selecting which HDD to boot from.

Any ideas about what I'm doing wrong?

---

### Post by uRock on 2017-10-29
Could be an issue with the USB creation or the downloaded image. 

Does it make it to the selection screen to select whether you want to install or boot Live?

I would redownload and rewrite the USB.

---

### Post by Shmoogly on 2017-10-29
No doesn't get to the selection screen. It just sits at the BIOS screen "Verifying DMI Pool Data" with a blinking underscore. So looks like it's not booting up from the USB. But sounds like my settings are appropriate. Hmm... Might have to try re-creating the USB.

---

### Post by sudodus on 2017-10-29
Please check with md5sum, that the downloaded iso file is good,

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If still no luck, and you are running linux, I suggest that you try with another tool, for example mkusb according to this link

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

If you run standard Ubuntu, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb mkusb-nox usb-pack-efi
```

Otherwise, if you are running Windows, I suggest that you try again with [Rufus](https://rufus.akeo.ie/)

or with the cloning tool [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by Shmoogly on 2017-11-04
Win32DiskImager did the trick. Worked straight away thanks for that :).

---

### Post by vasa1 on 2017-11-04
[How to mark threads [SOLVED] or [UNSOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Shmoogly on 2017-11-04
Some more installation problems:

I installed Ubuntu, but I got the error "boot loader failed to install" so obviously I can't boot into it. Then watched some more videos and figured out how to use the partition screen so I created the three required partitions, one for root '/', one for swap area (I know, not mandatory) and then one for the boot loader. Selected the partition that I created for boot loader in the drop down box asking which partition to use to install the boot loader, clicked install... aaaaand...

This is the result:

[ATTACH=CONFIG]277409[/ATTACH]

Any ideas on what to do now?

I tried to follow this tutorial: [https://community.linuxmint.com/tutorial/view/245](https://community.linuxmint.com/tutorial/view/245)

But when I went into disk partition to install the grub loader manually, I got these error when the disk partition was opening and loading the different disks:

[ATTACH=CONFIG]277410[/ATTACH]

---

### Post by ubfan1 on 2017-11-04
For a 2010 machine, that's a legacy machine, not UEFI.  You'd expect an MSDOS partition table on a legacy machine, but maybe GPT could work.  With MSDOS, make a swap, root, and forget any /boot partition (that's not for the bootloader anyway) unless you are using encryption or something other than a plain ext4 file system for the root.  Install grub to the device, /dev/sdg, not a partition like /dev/sdg3.     If you actually used a GPT partition table on the disk, then yes, you will need a 1M unformatted partition with the grub-bios flag (or bios-grub I can never remember which way).  The install still needs to go to the device.

---

### Post by Shmoogly on 2017-11-04
hmm, installation went fine, but not getting a boot screen, just goes straight to Windows. I've got many drives, maybe sdg isn't correct? I've got an SSD that has Windows on it, then I've got a RAID 10 setup with 4HDDs which is the data drive for Windows and now I have an additional 1TB that I want to split into two partitions, one for Linux one for MacOS.

Here's a vid of my partitions:

[https://www.youtube.com/watch?v=GLXQzRIzgRM](https://www.youtube.com/watch?v=GLXQzRIzgRM)

I'm guessing I need to install the boot loader into the last partition in the list? Is it smart enough not to overwrite anything and wreck my Windows install? Not in the mood to re-install my Windows.

---

### Post by ubfan1 on 2017-11-04
Can your machine actually boot off sdg?  If not,no use putting grub on it.  Can you make sdg sda?  That would allow you to put grub into a bootable position, and keep your Windows bootloader on sdd just in case.

---

### Post by Shmoogly on 2017-11-06
I'll be honest, I'm not really sure what any of those partitions mean. It's greek to me. Which one is which is a bit of mystery. I know SD probably means storage device and then a b g etc that's the name of the drive, but they are completely different to what they are called in windows so the ones that don't have any sizes next to them, make no sense to me, so no idea which one to use to install grub on.

In terms of which one I can boot from... they should all be bootable, just need to be set in BIOS?

EDIT: Well everything works. I changed the boot order to sdg which is apparently the new hdd, so it goes into ?GRUB? and then gives me the option to select whether to boot into Ubuntu or Windows. Now I just need to figure out how to make Windows default.

EDIT2: Doneskies, changed Grub order, haven't tested it yet, but looks like I'm ready to rock. Thanks for the help guys.

---

