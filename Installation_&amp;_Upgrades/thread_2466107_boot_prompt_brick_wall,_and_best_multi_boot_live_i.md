---
title: "boot: prompt brick wall, and best multi boot live iso tool?"
date: 2021-08-19
forum: Installation &amp; Upgrades
---

### Post by degarb on 2021-08-19
I had a computer go down last week, and have come to realize that every external usb drive should have lubuntu and windows 10 installation iso, installed, in addition to being your backup. 

I ruled out thumb drive, after days of trying to install 9 operating systems, linux, and get a usable computer.  They all pretty much constantly freeze up when running live, can't get past the boot: prompt, wouldn't pick up the network card.  Ubuntu wasn't usable with the 3.0 flash drive, neither was manjaro, due to sluggish freezing. Lubuntu, on the other hand picked up the wifi card and only firefox would constantly freeze every 90 seconds.  lubuntu got way more useable after following all the stuff on a blog by steve hanov, about optimizing a usb for linux. 

I spent hours looking at thumb drives, 3.0, 3.1,3.2 and decided from reviews that they all suck.  Likely the best, isn't as good as an external harddrive.   

So, I got ahold of a windows 10 iso and wanted Rufus to embed both into the drive.  No luck.  So I tried 4 other supposed multi os flashers, including sardu. But no luck.  Sardu is flakey, and at best, lubuntu gets hanged up at boot: prompt.  winsetupfromusb no luck.   No efi for lubuntu that works. 

It is a shame, because sardu has a really good concept. 

Is there any way to get past the boot: prompt?   slacks, slitaz, and some others, could get past this prompt when trying to use rufus.  

Is there a good mutiboot tool?

---

### Post by C.S.Cameron on 2021-08-19
- Format your external drive GPT and create the number of partitions you have operation systems. An external SSD is probably best.
- If you are installing Windows install it first.
- If no windows, create bios_grub and boot,esp partitions per [https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step) This will allow booting the drive on both BIOS mode and UEFI mode computers.
- Install your operating systems using the 'Something else' option. the above link may be helpful.
- Full installs are generally not useful for installing operating systems. If you need OS install disks you can store them on the drive as ISO files and boot them using GRUB.

If you just want to boot Live or Persistent operating systems this link might be useful: [https://askubuntu.com/questions/1269462/bios-uefi-template-image-for-booting-iso-files](https://askubuntu.com/questions/1269462/bios-uefi-template-image-for-booting-iso-files)

---

### Post by not-published on 2021-08-25
> They all pretty much constantly freeze up when running live, can't get past the boot: prompt

they shouldn't:  so perhaps you have a different problem altogether.  and if you are rescuing Ubuntu why aren't you using the Ubuntu install disk or an ubuntu rescue disk download?

if you install anything make sure "EFI or UEFI" is enabled in BIOS first (in some BIOS it is not default ON).  that will help you allot down the road.

as far as Rufus - that's not an ubuntu install or installation question and should be asked on Windows 10 forums.  rufus certainly isn't the only way to get an Ubuntu install USB while using windows10

infact:  with little info to go on (your PC model, ubuntu version your rescuing, etc):  rufus is on the list of PROBLEMS that must be excluded, I would say

---

### Post by oldfred on 2021-08-26
Years ago I burned CD/DVDs for install ISO, but also wanted many repair ISO like gparted, Supergrub, Knoppix, parted rescue etc. So had many CDs. But then each program/ISO updated so had to burn another.
But then flash drives came down in price. And I live near a Microcenter store and they have their house brand flash drives behind counter. Now have lots of flash drives.

But started using grub2's loopmount to directly boot ISO. So just have to copy ISO onto flash drive and can boot as many ISO as will fit on flash drive. Issue often is getting drive order & path correct as it is seen before any system mount. While hd0 in grub is usually sda, a flash drive as sdc is not hd2 when used as boot drive but will be hd0. Boot drive is always hd0.

[https://wiki.archlinux.org/index.php/Multiboot_USB_drive#GParted_Live](https://wiki.archlinux.org/index.php/Multiboot_USB_drive#GParted_Live)
[https://manpages.debian.org/jessie/live-boot-doc/live-boot.7.en.html](https://manpages.debian.org/jessie/live-boot-doc/live-boot.7.en.html)

ISO boot & link to examples
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
more examples
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[https://gist.github.com/Pysis868/27203177bdef15fbb70c](https://gist.github.com/Pysis868/27203177bdef15fbb70c)

Recently updated SSD to NVMe. And put SSD into USB3 to SATA adapter. While a more expensive solution, it is fast. Almost as fast as internal SSD.
I have full install of Ubuntu & then several ISO for loopmounting on external drive. And some of my most important data, but not enough space for all my data.
Since I have lots of flash drives, may do another external SSD.

---

### Post by C.S.Cameron on 2021-08-26
duplicate

---

### Post by C.S.Cameron on 2021-08-26
@not-published

One of the main purposes of Ubuntu Forums is to help people convert from Windows to Ubuntu.
Rufus is one of the best Windows tools for doing this.
How can you even say Rufus is an Ubuntu install or installation topic?
Rufus has been on topic in Ubuntu Forums since it was first created.

---

