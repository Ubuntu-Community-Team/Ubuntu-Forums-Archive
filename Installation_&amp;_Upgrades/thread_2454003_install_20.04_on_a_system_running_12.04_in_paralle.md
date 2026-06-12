---
title: "install 20.04 on a system running 12.04 in parallel and on two separate hds"
date: 2020-11-21
forum: Installation &amp; Upgrades
---

### Post by dieter-erich on 2020-11-21
Hi,
   I have a system running 12.04, which I did so far not update. I now want to install 20.04 in parallel and make it double boot. There are several HDs attached, among them external USB disks. I want to install the 20.04 onto a 1GB solid state hd, which shows up as /dev/sdc. I have the corresponding ISO file but usb-creator-gtk just shows me the choice of 2 of the five disks, but not dev/sdc (i.e. the sshd is not in the list, the current system disk is!). 

What is the correct procedure? I believe that it is not necessary to first write the ISO on an USB stick and install from there; can I do it directly on the sshd followed by making it bootable, supposedly via the usb-creator-gtk routine or gparted.

Thank you for hints, best D-E.

---

### Post by CelticWarrior on 2020-11-21
Ubuntu 12.04 is EOL since April 2017. Anyone using it should have upgraded before that date.

---

### Post by ajgreeny on 2020-11-21
As CW says, you should avoid using 12.04 if possible, and as you have the iso for 20.04 already I recommend that you create a USB install disk and then install 20.04 from that.

I have never installed direct from an iso but always used a USB, so I am not sure how simple it is to do what you're trying to do, though I am not sure exactly what you mean by the comment that the sshd is not seen; is that when you try to install the system, or are you trying to create install medium on the sshd?

---

### Post by CelticWarrior on 2020-11-21
The way to do it is booting the ISO from an existent Grub, not to use the usual tools to burn the ISO into an USB. Those proactively omit anything that isn't a USB flash drive for obvious reasons.

---

### Post by yancek on 2020-11-21
>   I want to install the 20.04 onto a 1GB solid state hd

That won't work, need a lot more than 1GB even for the iso, is that a typo?

>   I believe that it is not necessary to first write the ISO on an USB stick and install from there

No, it is not and you won't need usb-creator-gtk (you're not using a usb) or GParted unless you want to create partitions in advance of the install.

Detailed information on the process from Ubuntu documentation at the link below.

[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

Ubuntu documentation on the process with examples are at the link below.

[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)

Basically you download the ubuntu iso (usually to your /home/user/Downloads directory), make an entry in /boot/grub/grub.cfg of 12.04 as shown in the above 2 sites pointing to the iso at the properlocation and reboot.  If you do it this way, do not run update-grub.  If you follow the instructions it should be no problem to do as you are installing to a separate dreive.  I expect 12.04 is not EFI but rather Legacy/MBR so check that first.

---

### Post by dieter-erich on 2020-11-21
Thanks all for the hints! Yancek's links are most useful and I think I can do it following them. BTW this was indeed a typo: I meant 1TB :-)

---

