---
title: "Install 12.10 on Asus P8H77-V not working"
date: 2013-02-12
forum: Installation &amp; Upgrades
---

### Post by Eontraveler on 2013-02-12
I am trying to Install 12.10 on Asus P8H77-V motherboard and It's not working. Mainly there is no drivers for the NIC, Video and sound.
ASUS support say's, no support for this motherboard.
Ok then I have to stay with the Win 7.

Martin Masvike
{removed email}

---

### Post by dino99 on 2013-02-12
**** drivers for the NIC, Video and sound   ***

which are they ?  google around them (ubuntu+thatchip : lspci will list them)

note: you might need the latest kernel & video driver

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc7-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8-rc7-raring/)
- into an empty folder, download the 2 headers & the 2 images  (i386 or amd64)
- then from that folder ; ```
sudo dpkg -i *
```

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
- pick up the video driver you need, install it, then deactivate that ppa & update

That way you will get the latest kernel & video driver

note: in case  of huge trouble, boot into recovery mode (hit "shift" key at bios end process to get the grub menu on a single OS system, then select the second line)

---

### Post by oldfred on 2013-02-13
Removed email so you do not get spammed. We also are a forum so we want all info posted so others can also find the details to solve their issues.

You should not need drivers from the vendor. 

What video do you have?

Is system in BIOS or UEFI mode?

Have you downloaded live installed and booted it to see if it works?

       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

