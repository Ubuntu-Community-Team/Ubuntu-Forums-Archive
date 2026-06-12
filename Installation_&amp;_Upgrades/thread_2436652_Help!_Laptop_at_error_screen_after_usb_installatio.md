---
title: "Help! Laptop at error screen after usb installation"
date: 2020-02-10
forum: Installation &amp; Upgrades
---

### Post by mbindy1 on 2020-02-10
I used Ubuntu years ago, but I am not an advanced techie! I wanted to install Ubuntu on an old laptop and uninstall Windows 10. I followed steps from a video on how to do it. I downloaded Ubuntu. Then I downloaded Power Iso. After installing Power iso, I inserted a USB drive and went to installation, answering YES to uninstalling Windows 10. Ubuntu came up, ran fine, and after awhile I shut it down. I started up the laptop and got a purple screen with GNU Grub at the top and within just seconds, it went to a black/white screen with lines and lines of info, "kernel not syncing," etc, a flashing cursor and I cannot type anything. [ATTACH=CONFIG]284998[/ATTACH][ATTACH=CONFIG]284999[/ATTACH]So, at this point, I have an unusable laptop. I am also unsure that the USB flash drive still has Ubuntu, since it seems to do nothing if I try to insert it before starting the laptop.
Should I order a Ubuntu disk or USB drive and start over? 
Thanks so much!

---

### Post by yancek on 2020-02-11
You don't need to "uninstall" operating systems but rather format the partitions on which they reside.  I've never used Power ISO so don't know what to expect with it.  You indicate you followed some tutorial online but neglected to post a link to it so if there was incorrect information on it, no one would be able to tell you.  Did you boot the Ubuntu usb and use it?  Did you use it and go through the entire installation process from the usb?  Not really clear exactly what you did.  If you insert the usb before starting/booting the laptop, you would need to set the usb to first boot priority in the BIOS for it to boot.

---

### Post by mbindy1 on 2020-02-11
This is video I watched and followed: [https://www.youtube.com/watch?v=vt5Lu_ltPkU](https://www.youtube.com/watch?v=vt5Lu_ltPkU)
I believe I followed all the steps he suggests to at least 4:30 in the video. After that his voice and directions seemed to be on to more complicated things for those more advanced than I. I do remember going to the BIOS and choosing to boot from my USB drive.

---

### Post by yancek on 2020-02-11
I'm sure you are aware that nothing on YouTube is vetted so anyone can  post anything there.  So I would suggest that if you want to try and use  official Ubuntu sites when possible.  Ubuntu is very well documented  and has good support here and elsewhere.

If the poweriso method  didn't work for you (and as I said, I've never used it so...?) I would  suggest using more commonly used software for the purpose of creating a  bootable usb such as Rufus or Etcher.
You posted the link I asked for but failed to answer the other 2 questions which are just as significant.

 Did you boot the Ubuntu usb and use it? 
Did you use it and go through the entire installation process from the usb?

You don't have to do updates and install 3rd party software.  That is optional and will increase the install time significantly.
Which Installation type option did you select?  If you want only Ubuntu the first option to Erase disk and install Ubuntu would be best.
If you do not know what LVM is do not use the 2nd encrypt option.  Best option is Something Else which is simply a manual install.  If you don't feel confident enough to do that, use the Erase option.
The rest of the tutorial basically shows you how to use unallocated space on a drive to create partitions on which to install Ubuntu.  I don't know what you have now but if you can boot the Ubuntu  usb, do that with the Try Ubuntu option and when you get to the Desktop, open a terminal and run the following command and post the output here so it lists your partitions:  sudo parted-l

The link below is the Ubuntu installation guide which would be useful to read although it has far more detail than you need.  The 2nd link is the official Ubuntu documentation on installing Ubuntu UEFI with windows 10 which should be good to read although you can ignore the parts about dual booting as you don't want/have windows.  Since you had windows 10 installed it was almost certainly a UEFI install so read those parts carefully.  It would also be useful to indicate which Ubuntu release you are using.

[https://help.ubuntu.com/lts/installation-guide/amd64/index.html](https://help.ubuntu.com/lts/installation-guide/amd64/index.html)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The link below

[https://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/how-to-install-ubuntu-18-04-lts-bionic-beaver-on-uefi-and-legacy-bios-system.html](https://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/how-to-install-ubuntu-18-04-lts-bionic-beaver-on-uefi-and-legacy-bios-system.html)

---

### Post by mbindy1 on 2020-02-11
I did boot with the USB drive that I had made with Ubuntu and I did go through the installation, uninstalling Windows 10. I chose the latest ubuntu, which I think was 18.04

---

