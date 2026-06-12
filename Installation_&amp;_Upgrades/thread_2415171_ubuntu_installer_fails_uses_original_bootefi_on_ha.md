---
title: "ubuntu installer fails uses original /boot/efi on hardisk 1 when install to 2"
date: 2019-03-21
forum: Installation &amp; Upgrades
---

### Post by hawk.j on 2019-03-21
Example of problem: FYI GPT partitions used

Source Ubuntu install disk usb:

Computer: /dev/sda/ Linux Mint

New usb /dev/sdb
I have installed letting it replace an existing 16.04 setup. Once install has completed it puts Grub on /dev/sda desbite being told /dev/sdb. GRRRR
On reinstal I create my own structure
Drive /dev/sdb
part /EFI
Part Swap
Part /

Error message EFI mounted on two points i.e. /dev/sda1/boot/efi /dev/sdb/boot/efi  ok scratch scartch

Either there is a bug or something has changed use to be simple:
Drive /dev/sdb
partition 1 /swap
partition 2 /
grub /dev/sdb
Slam bam thanyou mam
I miss the old days

This system fails to allow a user to produce a bootable portable drive for service work.
Perhaps you can explain, point me in the right direction or confirm bug.

thanks
jhawk

---

### Post by yancek on 2019-03-21
I have seen a number of posts describing this situation.  The default install of Grub for Ubuntu ( and perhaps others?) is to install to the first EFI partition and if there is one on sda, that's where it goes.  If you want a separate EFI partition on sdb or another drive, dis-connect sda first and go through the process including creating an EFI partition there.

You replaced and existing Ubuntu 16.04, with what?  A newer Ubuntu?  Are you trying to create an Ubuntu install which you can use on multiple computers?

How/when do you get the message about EFI mounted at two points?  That obviously won't work.

---

### Post by hawk.j on 2019-03-21
You are correct it was in fact an upgrade. Let's think about this for a second, a friend comes over who wants to try Linux and as directed brings either a usb drive or usb stick and you are going to assist him in install of Ubuntu on his equipment. Based on this structure it is only good at your house. Unless you remove your personal hard drives. Great way to not spread the word about Ubuntu.
As for the EFI failure, I created a manual partion scheme as part of that I formated the first partition to 512MB Fat32 and mount point /boot/efi and remaining swap and root, this is the point the installer fails error 'you are trying to mount two drives to same partion or something of the sort. 

Previously, the installer accepted the directive to install to X drive and grub to X drive (i.e. overloading install to machine defined). They for some reason appear to have broken that needed ability.

I can't imagine a situation where anyone is going to remove drives to perform install, that is just simply beyond the pale in my opinion. FYI: 19.04 better driver support was cause of this mess.

I hope that explains my proplem.
jhawk

ps Version effected 16.04 18.04 18.04.2 19.04

---

### Post by oldfred on 2019-03-21
We have been complaining for years.
I recently installed 19.04 to sdb and ubiquity/grub again overwrote my main working install 18.04 using sda's ESP.
I told it not to use sda's ESP, to use sdb's ESP, changed combo box(which has only worked with BIOS installs). 
And during install it quickly flashes by that grub is installing to sdb with --force parameter. But it installed to sda.

       Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488)

---

### Post by hawk.j on 2019-03-21
Thank You
jhawk

---

### Post by yancek on 2019-03-22
> Previously, the installer accepted the directive to install to X drive and grub to X drive (i.e. overloading install to machine defined). They for some reason appear to have broken that needed ability

That always worked for me in the past.  THe difference is that now it is UEFI rather than a Legacy/MBR install which is the problem that has not been corrected.  I"m not a developer and have no idea how difficult it would be to change this but as pointed out by oldfred, there have been a lot of complaints about this with no changes yet made.

---

### Post by oldfred on 2019-03-22
It is some change Ubuntu's ubiquity does to grub.
I installed Fedora a year or two ago, just to see different. And it directly installed to ESP on sdb and booted without issue.

In viewing grub's code, they make a lot of changes to use "ubuntu" as the  "efi_distributor" variable, so they make a lot of changes to grub.
But I think issue really is something in Ubiquity, since now grub says installing to sdb during install.  And Boot-Repair seems to install to sdb, although I have not tested that myself.

---

### Post by hawk.j on 2019-03-24
[ATTACH=CONFIG]282844[/ATTACH]

---

### Post by oldfred on 2019-03-24
Do not know about Apple.
But it does not really break anything, it just is inconvenient. 
It adds a new folder in the sda drive /EFI/ubuntu and makes Ubuntu as default in UEFI boot order.

And while I can use newest install to boot my main working install, I do not want it to overwrite sda's ESP, but I would like an UEFI entry on sdb.
You can install with ubiquity -b to not install grub at all, but then must have another boot loader somewhere that you can update to find new install.

---

### Post by hawk.j on 2019-03-24
The real point is that Ubuntu made a conscious decision to 'Override the end users decision' thus removing a protective layer from the end user 'With Out Informing of Same'.
I don't care how big a company you are denying the end user an option that is included in your installer is 'Wrong" and potentially liable. Fails to pass the smell test and is beyond the pale!

Off my soapbox.
jhawk.

P.S. [COLOR=#000000]But it does not really break anything, it just is inconvenient. Since grub can't boot OS X I would call that broken. Yes, you can use the Option key but that equates to numerous boots i.e.broken.
Here is an example you might like:
    X company had your cars door locks changed. But sir it didn't break anything it just made it inconvenient. Would you live with that?[/COLOR]

---

