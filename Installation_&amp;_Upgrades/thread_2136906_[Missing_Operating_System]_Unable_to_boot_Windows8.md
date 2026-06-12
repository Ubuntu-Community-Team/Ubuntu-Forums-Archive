---
title: "[Missing Operating System] Unable to boot Windows8 after installing Ubuntu"
date: 2013-04-19
forum: Installation &amp; Upgrades
---

### Post by cherismaticanas on 2013-04-19
Hello ,

I installed **Ubuntu 13.04** using 'Universal Usb Installer' on my **windows8** laptop in C:/ drive. Every time I restart my computer, and even when I try to boot from BIOs, it just takes me to my Ubuntu login. I have assigned the Cd drive as primary boot device, and it still wont boot, even when I manually try to boot from CD, it just takes me to the Ubuntu login.
And it showed 'Missing Operating System' after i clicked on something in *Gparted Partition Editor* by mistake.
I tried to repair using windows8 disk but it didnt load . I installed both windows and ubuntu in same drive and it is not accessible now . when i click on the drive it shows ;

Unable to access “105 GB Volume”

Error mounting /dev/sda2 at /media/ubuntu/8AB0F007B0EFF799: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmas k=0077,fmask=0177" "/dev/sda2" "/media/ubuntu/8AB0F007B0EFF799"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.


If someone could help me to mount and remove universal usb installer, it would be great.

Anas Mohammed

---

### Post by bart.a on 2013-04-19
Just to get things straight..

You split up the HDD into two partitions (Ubuntu - Win8) during the installation process?
What software did you use to try to boot from CD?

Last time I messed up my grub, I first tried the 'windows rescue disk' which did exactly squat..
Then I found ['super grub2 disk']("http://www.supergrubdisk.org/") and that restored my bootloader without a hitch.. (note! that was Ubuntu 12.04 and Win7)
Maybe you could give it a whirl..

---

### Post by darkod on 2013-04-19
Did you notice the message "windows is hibernated" when you tried to open the partition from ubuntu? You should never hibernate one OS and try to boot the other one. It should be completely shut down.

Now, with win8 this might not be your error since the wonderful developers in Microsoft decided to make win8 hibernate when you try to shut it down. They do this so it can boot faster the next time and look like they made it boot faster.

But when people want to dual boot like you, it creates them big problems. You need to google around how to disable this feature of win8 and make it shut down when you select shut down, not to hibernate.

On another note, what exactly did you do in Gparted? Gparted is a very powerful tool and mistakes can really mess up your system. You need to be more precise what you did.

To start with, can you open terminal in ubuntu and post the output of:
```
sudo parted -l
```

There is no need to use super grub2, at least not yet. The ubuntu cd/usb is enough to fix all you need, and it will install the correct version of grub2 while super grub might not. The problem here might be what you did in Gparted because you say the missing OS message showed up after that. If you deleted some partition, no super grub disc can help you anyway.

---

