---
title: "Full USB pen drive installation not bootable"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by mojonba on 2008-11-07
Hello,

I have spent several hours trying to make a full (not live/persistent etc) installation to a usb drive but the installation is still not bootable. I have followed [_THESE_]("http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/") instructions especially the bootloader part. I have tried installing the bootloader to both /dev/sda1 as well as /dev/sda. The only other drive in my computer other than the pen drive is a usb cdrom from which im running the install. I'll post my fdisk -lu results below. Theres two things I did post installation to try to make this work one was to set the boot flag to /dev/sda1 partition and the other was to restore the mbr by using "install-mbr /dev/sda". None worked I am getting a "MBR FA:" after the mbr fix before i got "$%#:" prompt.

```
ubuntu@ubuntu:~$ fdisk -lu

Disk /dev/sdb: 2000 MB, 2000682496 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3907583 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00563840

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     3614624     1807281   83  Linux
/dev/sdb2         3614625     3903794      144585    5  Extended
/dev/sdb5         3614688     3903794      144553+  82  Linux swap / Solaris
```

Thanks for your help.

---

### Post by C.S.Cameron on 2008-11-07
If I have my hard drive unpluged I never bother with Part 9, selecting sda in Advanced, when I have tried I get into trouble.
It seems to figure it out where to write the boot loader  by itself.

---

### Post by mojonba on 2008-11-07
The thing is i dont have any hdd installed.

---

### Post by mojonba on 2008-11-08
any suggestions?

---

### Post by C.S.Cameron on 2008-11-08
Could the installer be seeing your USB CD as sda?
Is there an option to put the boot loader on sdb or sdb1?
It looks like this is where your o/s is.
When you try to boot and press Esc do you get a grub menu?

---

### Post by caljohnsmith on 2008-11-08
Your fdisk output clearly shows your pen drive as sdb, not sda, so you should tell Grub to install to /dev/sdb, not /dev/sda. Have you tried that?

---

### Post by mojonba on 2008-11-09
The sda/sdb differences are because i was playing with different pen drives when i took the fdisk snapshot. But naturally the pendive takes sda and the cdrom doesnt show up in fdisk. No and I havent been able to hit ESC to se if grub appears beacuse the bios is not booting the drive. I assume that Grub = bootloader at the advanced setup and yes i've tried installing it to both /sda & /sda1 with the same results. I'm going to try to this whole thing in another computer to see if there a difference and I'll post the results.

---

### Post by mojonba on 2008-11-09
Update: I tried in two different computers. Same thing happened in the second one, but the third was different. Different from the other two computer the install routine actually ended with restart now prompt. The other two computers the install ended by booting into a live cd session. After it booted to the desktop it also gave an ubiquity error which i didnt give any importance. I think the following is happening. The setup is not completing successfully in those other two computers so therefore the usb does not come out bootable afterwards, maybe the ubiquity error can shed some light on the problem. But Im still unable to get into the desktop with the install that did end successfully though. Im now getting a kernel panic error after the grub selection menu.

---

### Post by mojonba on 2008-11-10
To wraps things up and bump my post here what is happening when i do an install to usb. The setup doesnt not complete succesfully in 2 out of 3 computers. This does not happen when i install to and hdd. Instead of a restart prompt it goes to a live cd session and shows an ubiquity error. In the one computer that it does complete, when I try to boot it comes up with a kernel panic error after grub.

---

### Post by C.S.Cameron on 2008-11-10
Ok, I missed the part about using a 2G thumb drive for a full install. I do not think this is large enough for a full install of Ubuntu.

---

### Post by mojonba on 2008-11-10
Geez, so much time lost due to not reading. The pendrive linux tutorial i linked in the first post says a 4GB+ usb drive is required and I was trying to make it fit inside a 2Gb. Somebody should suggest installing a space check before installation to keep people like me doing dumb things.

---

