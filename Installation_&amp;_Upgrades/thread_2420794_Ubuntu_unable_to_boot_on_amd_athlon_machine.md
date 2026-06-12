---
title: "Ubuntu unable to boot on amd athlon machine"
date: 2019-06-11
forum: Installation &amp; Upgrades
---

### Post by grunclepug on 2019-06-11
hello, i am trying to get ubuntu on a pc i build. the pc has been tested in windows and is fully functional.
specs:

cpu athlon x2 3800+
4gb ddr4 666ghz
ati hd5850

before ubuntu isntall it said "[0.28935] Spectre V2 : Spectre mitigation: LFENCE not serializing, switching to generic retpoline

after installing ubuntu with a different system, the system would beep once (short beep), and would just sit on a blank terminal with a flashing cursor in the top right (as if there is no boot media.

any help is appreciated thanks.

---

### Post by dino99 on 2019-06-11
No idea about the way you have made that install :(
example: [https://hackernoon.com/installing-ubuntu-18-04-along-with-windows-10-dual-boot-installation-for-deep-learning-f4cd91b58557](https://hackernoon.com/installing-ubuntu-18-04-along-with-windows-10-dual-boot-installation-for-deep-learning-f4cd91b58557)

---

### Post by grunclepug on 2019-06-11
to create the install, i downloaded ubuntu 18.04 off the website, and i wrote the iso to a usb drive. it wouldnt install on the athlon system so i plugged the ssd and my usb install into my mining rig and installed ubuntu onto the ssd. the ssd is brand new (got it 2 days ago from newegg), everything works on any of my systems, but when installed into the athlon system, it doesnt boot.


> **dino99 said:**
> No idea about the way you have made that install :(
example: [https://hackernoon.com/installing-ubuntu-18-04-along-with-windows-10-dual-boot-installation-for-deep-learning-f4cd91b58557](https://hackernoon.com/installing-ubuntu-18-04-along-with-windows-10-dual-boot-installation-for-deep-learning-f4cd91b58557)

---

### Post by yancek on 2019-06-11
What method (software) did you use to write the Ubuntu iso to the usb?
Did the second computer you used to install Ubuntu to the SSD have another operating system and if so, which one?  And to follow up, was it an EFI or Legacy install?

> after installing ubuntu with a different system, the system would beep  once (short beep), and would just sit on a blank terminal with a  flashing cursor in the top right (as if there is no boot media.

Which means the Grub bootloader was not properly installed.  More info is necessary so go to the site below and download and run the boot repair software.  When you download, use the 2nd option using the ppa with the live Ubuntu usb and select the Create BootInfo Summary option and when it finishes, it will give a link which you can post here and someone should be able to review it and make a suggestion. to resolve the issue.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by grunclepug on 2019-06-11
> **yancek said:**
> What method (software) did you use to write the Ubuntu iso to the usb?
Did the second computer you used to install Ubuntu to the SSD have another operating system and if so, which one?  And to follow up, was it an EFI or Legacy install?



Which means the Grub bootloader was not properly installed.  More info is necessary so go to the site below and download and run the boot repair software.  When you download, use the 2nd option using the ppa with the live Ubuntu usb and select the Create BootInfo Summary option and when it finishes, it will give a link which you can post here and someone should be able to review it and make a suggestion. to resolve the issue.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


i found out the beep is just the amount of usb devices connected. as for software, i used win32diskimager. I format my drives with SDFormatter before writing them (probably not necessary but I know raspberry pi has issues with the built in windows formatting which causes the image to not write properly, making it unbootable) the system i used to install it had no other drives as i disconnected it's ssd to connect the new ssd. i know grub is installed properly as it works fine, just not in my one particular system. I am not sure if it was efi or legacy, as I just plugged it in and booted the pc, I didn't have to select anything in the boot menu or bios

---

### Post by Bashing-om on 2019-06-11
grunclepug; Hey !

I too run dual core Athlon - and have upgraded the system to SSDs.
Now what I found in my endeavor is that AHCI must be enabled. I have Phoenix bios, and took me a long time to figure out how AHCI is enabled, For my bios I had to enable raid but not to activate on the devices ! 
Now all workie great and has lasted a long time.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by grunclepug on 2019-06-11
> **Bashing-om said:**
> grunclepug; Hey !

I too run dual core Athlon - and have upgraded the system to SSDs.
Now what I found in my endeavor is that AHCI must be enabled. I have Phoenix bios, and took me a long time to figure out how AHCI is enabled, For my bios I had to enable raid but not to activate on the devices ! 
Now all workie great and has lasted a long time.
[INDENT][INDENT]my bit to try and help
[/INDENT]
[/INDENT]


still no boot :(
thanks for the suggestion
ive never had this many issues trying to install linux

---

### Post by Skaperen on 2019-06-11
666ghz?  evil!!

---

