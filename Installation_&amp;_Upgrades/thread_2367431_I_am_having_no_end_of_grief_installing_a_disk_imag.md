---
title: "I am having no end of grief installing a disk image to usb stick,drive, or a disk!!!!"
date: 2017-07-30
forum: Installation &amp; Upgrades
---

### Post by helen-ms on 2017-07-30
I have a G552vw asus p. c.  it has 8 logical processers and runs win 10.

Th problems is when I try to create a bootable media as in all of the above,  windows boot manager wil not boot reliably into a usb or disk drive. Even if one sets up the bios to boot into the disk drive or usb. 

But  it does enough times for the ununtu to report that two files are corrupted with out fail, regardless of what media I am trying to use.

 I am using rufus for usb stick or disk drive (1 tetra) or infrarecorder for the cddisk drive. I have tried several downloads as well.

I am wondering why every attempt produces two unamed corrupt files?

One possiability  is while i transferr the files to the bootable media the windows file explorer starts, I have wondered if the explorer is corrupting the files concerned. Unfortunatly I do not know how to turn this app off during the file transfer, if indeed it is the problem.  Gee would i like the package in the normal format!

one desprate could have been Ubuntu user
Helen

---

### Post by BenginM on 2017-07-30
Salutations!

Hiya Helen .. So all these attempts only on a MS Windows or within Ubuntu GNU/linux as well ..!

regardless , did you checked the hashes before burnin' to the media 

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

whilst brunnig usin' infrarecorder , after SHA256sum/Md5sum check the hashes on the iso , make sure the burn speed is at 2x or 4x maximum , not above!

I don't know about rufus , try with [Unetbootin]("https://unetbootin.github.io/") , the usb media should be formatted as a FAT32 ..

if you're flyin' a GNU/lunx OS , all you have to do is format the usb media to FAT32 using gparted , and then umount the usb , then dd or cat the iso :

# cat mini.iso > /dev/sdX 
# sync

---

### Post by johndough2 on 2017-07-30
Hi

Adding to the above...

Consider the possibility that the copy is not corrupt.

Consider a BIOS setting where you disable secure boot.

The 2 unnamed files, if I were to guess, would be efi related, possibly shim.efi and MokManager.

If you are really desperate consider buying a linux magazine with a coverdisk, this eliminates the windows 10 part.

Get someone else to try on a non-related machine.  It probably is not you at fault.

PS: Maybe W10 is trying to add some autorun.inf to the disk and off course this will be invalid on a boot device.

---

### Post by gordintoronto on 2017-07-30
It might help people help you if you said what version you have? For example, 64-bit Ubuntu 17.04, obtained from the Canonical site.

Since the laptop is pretty new, 17.04 might work better than 16.04.

---

### Post by TheFu on 2017-07-30
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0) is the "official" method to create a USB flash drive boot with Ubuntu from Windows.

There is similar tutorial if you are running Ubuntu, but I usually just 'dd' it.

I've heard that HP adds extra hoops to jump through to boot non-Windows OSes. Don't think that applies to Asus, but it would be good to search for any issues - "ubuntu asus G552vw" would be my search term. The results seem to imply there are some tricks needed and a few grub options.

---

### Post by oldfred on 2017-07-31
You may need UEFI updates & firmware updates and  boot parameters like pci=nomsi.

 ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273)
ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)

---

