---
title: "installation onto 2nd SSD"
date: 2016-02-12
forum: Installation &amp; Upgrades
---

### Post by mzimmers on 2016-02-12
Hey, all - this is probably a duplicate, but I couldn't find what I was looking for. I'm getting back into Ubuntu after a couple year hiatus. I have a PC with 2 SSDs. I'd like to install Ubuntu onto the 2nd (it's fine to wipe out anything that's on it).

Can someone link me to the instructions for doing this? I've already downloaded the .iso file onto my first SSD. I just can't find any specific instructions on installing "cross-device."

Thanks...

---

### Post by yancek on 2016-02-12
A very detailed tutorial on installing Ubuntu is at the link below.  Installing to a separate device (SSD) simply requires you knowing which device it is.  Linux names devices:  sda, sdb, sdc, etc.  If you are familiar with that naming convention and know the size of the specific device, you shouldn't really have any problem.

You haven't mentioned having any other operating system on this computer.  If you do that complicates things.  If you have a newer (8 +) version of windows, that adds another complicating factor.  You haven't mentioned having this so there's no point in giving additional explanations which may not be needed.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by mzimmers on 2016-02-12
Thanks for the reply, yancek. I should have said that currently I have Windows 7 on my main drive. My hope is to keep the two OSs on separate drives, and merely select one at hardware boot. I'm hoping this isn't too difficult a request.

And...I'm afraid I don't see the link you mention.

---

### Post by QIII on 2016-02-12
To avoid a ***Significant Emotional Event™***  I suggest keeping your Windows (I have taken the liberty to correct your misspelling above) drive unplugged when installing Ubuntu.

---

### Post by oldfred on 2016-02-13
QIII suggestion is the best to avoid issues.

But if not wanting to disconnect drive, then you need to use Something Else, not any of the auto install options. They all install grub to whatever drive is seen as sda, but you want to be sure to install the grub2 boot loader to the MBR of the drive that is Ubuntu. (Assumes system is BIOS/MBR not UEFI/gpt).

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
            Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by yancek on 2016-02-13
> And...I'm afraid I don't see the link you mention. 		

Added it to the post above.

---

### Post by mzimmers on 2016-02-13
Thanks for the warning, guys. I used LiLi to create a boot/install USB stick. Next I'll disconnect the SSD with Windows 7 on it, and try installing from the stick. I'll report back when I have something noteworthy...

---

### Post by mzimmers on 2016-02-14
Progress has been made. I disconnected my Windows drive before installing Ubuntu, then installed (successfully).

My current snag isn't exactly an install question, so maybe I should take it elsewhere, but now when I start the system and go into the BIOS setup, it only "sees" the Ubuntu drive (yes, I reconnected the old one). The Windows drive is still intact, and when I disconnect the Ubuntu drive, it boots off of it successfully.

I'm using SATA III cables for each SSD as well as for my DVD player. I've looked through the booklet that came with my MoBo, but it's short on information like this. If anyone has any ideas what I'm doing wrong, please share...otherwise, I'll find a hardware forum to ask about this. The MoBo is an ASROCK Z87E-ITX, by the way.

Thank you.

---

### Post by oldfred on 2016-02-14
That is an UEFI motherboard.
Are Windows & Ubuntu either both UEFI or both BIOS installs?
UEFI and BIOS are not compatible. Or you can only boot from grub menu other installs in same boot mode.
If not same, you should be able to use UEFI boot menu or one time boot key, often f10 or f12 to get just boot menu, check manual.

---

### Post by mzimmers on 2016-02-15
Hi Fred -

The Ubuntu install is from the 14.04 ISO file; I imagine that's UEFI. The Windows 7 install is from a DVD dated 2011, and doesn't indicate whether it's BIOS or UEFI.

The F11 shortcut to the boot menu does work, so I think I'm OK -- it just works a little differently than what I expected. Thanks for the information.

---

### Post by oldfred on 2016-02-15
Windows 7 default from DVD is a BIOS boot, you have to copy to a flash drive and move a few files around to make it UEFI boot.
Ubuntu install disk is both UEFI & BIOS. You choose in UEFI boot menu  which way to boot flash drive.

Both Windows & Ubuntu install in the same boot mode as you boot installer flash drive.

---

