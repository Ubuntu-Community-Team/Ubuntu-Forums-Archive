---
title: "install from hard disk"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by bricedebrignaisplage on 2007-08-24
I'm trying to install Ubuntu on my laptop. Can't boot from USB nor CD-drive. I have a floppy drive though and can boot from it. I installed SBM and found an external CD-drive but it's not recognized by SBM. I don't think I can do a netinstall because to access the network at my university I need to authenticate with ezXcess.

My computer runs under winME and the install from windows method failed. Probably due to some problem with accessing real DOS mode...

So I am trying with install from HD. I read [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) and [https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html) and some more already but couldn't find a working solution.

Here is what I did:
[LIST]
[*]copy hd-media/vmlinuz and hd-media/initrd.gz and the Ubuntu ISO (desktop-i386) to C:\
[*]boot from a GRUB floppy
```

# make2fs /dev/fd0
# mount -t ext2 /dev/fd0 /mnt
# grub-install --root-directory=/mnt '(fd0)'
# umount /mnt

```
[*]boot the kernel using /dev/ram as root
[/LIST]
Linux boots and the config screen appears, asking for language and keyboard.
But then it cannot find the ISO image! It tries to mount all my disks and search but doesn't find it. It seems that it keeps looking for a CD. I'm never given the option to point to the ISO manually.

Any solution?



Otherwise I am thinking about plugging my HD in a computer that can boot from CD and install from there, then plug back to the original computer. Does this have a chance to work?

---

### Post by Pumalite on 2007-08-24
Maybe.

---

### Post by pxwpxw on 2007-08-24
The iso can be on ntfs, fat32, ext2/3 partition, then the hd-media images should find it. 
grub cannot boot kernel from ntfs, but can from fat32, ext2/3.

 If the installer first finds another iso, which is not valid, it does not look for more, so unwanted *.iso files need to be renamed .isoxxx or removed.
  
Remeber you will be in trouble if the installer zaps the iso image before it has finished using it.

---

### Post by logos34 on 2007-08-24
> **bricedebrignaisplage said:**
> I'm trying to install Ubuntu on my laptop. Can't boot from USB nor CD-drive. I have a floppy drive though and can boot from it. I installed SBM and found an external CD-drive but it's not recognized by SBM. I don't think I can do a netinstall because to access the network at my university I need to authenticate with ezXcess.

My computer runs under winME and the install from windows method failed. Probably due to some problem with accessing real DOS mode...

Linux boots and the config screen appears, asking for language and keyboard.
But then it cannot find the ISO image! It tries to mount all my disks and search but doesn't find it. It seems that it keeps looking for a CD. I'm never given the option to point to the ISO manually.

Any solution?

Otherwise I am thinking about plugging my HD in a computer that can boot from CD and install from there, then plug back to the original computer. Does this have a chance to work?

I got a similar problem when I tried to use the alternate install cd with an install from hard drive (linux os).  It refuses to accept the iso and keeps looking for the CD.  

I'd try Wubi next.  [Claims to work with all versions of windows from '98 to vista]("http://wubi-installer.org/faq.php#requirements") (I've only tried it on XP x64).  Then convert to a permanent installation by transferring ubuntu onto a dedicated partition using [LVPM]("http://lubi.sourceforge.net/lvpm.html") method.  (Wubi will download the Feisty alternate install iso, but if you already have it you can save some time by copying it to the wubi folder.)

That's what I'd do, then as a last resort come back to the usb stick install or [floppy method]("https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies?highlight=%28installation%29").

---

### Post by Herman on 2007-08-24
> Otherwise I am thinking about plugging my HD in a computer that can boot from CD and install from there, then plug back to the original computer. Does this have a chance to work? That would be the simplest way by the sounds of things. Ubuntu will be set up with settings that suit the other computer, so when you put the hard drive back in your laptop again and boot it for the first time, you'll need to run [sudo dpkg-reconfigure xserver-xorg]("http://users.bigpond.net.au/hermanzone/p7.html"). After that everything should be okay.
It would be simplest if you remove the hard drive from the computer you want to use for an install computer and plug in you own hard drive by itself, as primary master. That way Ubuntu will automatically set itself up as /dev/hda1, and not include stuff in /etc/fstab and in /boot/grub/menu.lst that refers to partitions and OSes some other hard drive that isn't going to be there when you plug it back into your own computer.

That would be the easy way though, and it seems like a nice challenge you have there, I hate to spoil a good challenge by encouraging someone to cheat and take a shortcut. It might be more fun to try to figure out how to do it without resorting to the easy method. :)

Regards, Herman :)

---

### Post by logos34 on 2007-08-24
Hi Herman,

It probably would be easier to do the 'ol disk-swap method.  Hopefully only the X server will need reconfiguring like you say.  I just hesitate to recommend doing it that way because I'm overly cautious.  (Although I am otherwise sympathetic to manhandling hardware, e.g. 'uplug-the-laptop-internal-hard-disk-before-installing-to-usb-drive' school of thought.  But that's a grub issue).  I'm not a big Wubi fan but I think it would also be an option here.

By the way I have a question: should I test Grub2?  I have a MintLinux install on a small partition I thought I'd use--it's expendiblle if I bork anything.  I notice Grub2 is even in the repos (1.95) but marked 'experimental'.  I know they've changed the partition numbering scheme (starts at 1 instead of 0),  Anything else to look out for?

---

### Post by Herman on 2007-08-24
Hi logos34,
I think your suggestion to try Wubi is a great solution. And you're right, it might not be such a good idea for me to advise people to go reaching inside their computers and messing around unplugging things. Some people would know what to do and be okay with that but others might not. Most laptop hard drives are pretty easy to exchange though, if the other computer is a laptop too. Probably not too much risk there, laptop hard drives are just inside a hatch underneath. The motherboard and other vital parts won't be exposed.  
What really happened was, your post arrived just as I was finishing mine and I didn't look first before I sent mine in. Then when I saw the you had beaten me by a few minutes I looked at the two different answers and I though I'd leave mine there and let bricedebrignaisplage decide what to do. No disrespect intended.   :)
>  By the way I have a question: should I test Grub2? Sure if you feel like it. I haven't yet but I really should. I'll PM you about that. :)

---

### Post by logos34 on 2007-08-24
> **Herman said:**
> Hi logos34,
I think your suggestion to try Wubi is a great solution. And you're right, it might not be such a good idea for me to advise people to go reaching inside their computers and messing around unplugging things. Some people would know what to do and be okay with that but others might not. Most laptop hard drives are pretty easy to exchange though, if the other computer is a laptop too. Probably not too much risk there, laptop hard drives are just inside a hatch underneath. The motherboard and other vital parts won't be exposed.  
What really happened was, your post arrived just as I was finishing mine and I didn't look first before I sent mine in. Then when I saw the you had beaten me by a few minutes I looked at the two different answers and I though I'd leave mine there and let bricedebrignaisplage decide what to do. No disrespect intended.   :)
 Sure if you feel like it. I haven't yet but I really should. I'll PM you about that. :)

Ok, thanks Herman. no problem. I just thought I'd ask about Grub2 before I jump...I realize there isn't a lot documentation on it yet (from what I can tell), but I was curious about it so I thought what the hell let's install it and find out!  Besides I'm bored and need something else to try (I'd do VMWare but I only have a trial version of x64 XP so it makes things kinda hard).  But I guess I should bring this up in a PM or another thread.

bricedebrignaisplage,

Let us know how it goes.

---

### Post by pxwpxw on 2007-08-25
Some more about hd-media installs - having just re-run some

I have had no problem with the ubuntu704 hd-media install for i386 or for mac ppc, and it is fast. But there have been some problems along the way which might cause failure to find/accept and mount the CD iso image (loop mount on /cdrom):

These include: 

In previous 610 release there was a bug that caused failure to loop mount the iso.
(missing /dev/loop ) can be fixed manually.

The install images and the iso need to be matching version, but this won't prevent the iso being mounted.

If the installer first finds another iso, which is not valid (say a ppc iso on an i386, it does not look for more, so unwanted *.iso files need to be renamed  *.isoxxx, or removed.

The install images can handle ntfs, fat32 and ext2/3 when running iso-scan and load-iso, but I would not expect  reiser and LVM.
And grub can boot images from fat32 or linux, but not from ntfs.

---

### Post by bricedebrignaisplage on 2007-08-26
Thanks to all of you for your  interest and your sympathy.

I had a burst of  hope after reading pxwpxw's post: I have 2 ISO on my HD: one for ubuntu and the other for xubuntu (which I'm trying to install), and I am using the kernel and initrd found on the ubuntu repository. So maybe a matching problem.

But no. I tried again after removing the xubuntu ISO but it still fails. The funny thing is that the ISO is found and mounted on /cdrom. But still the installer complains:
> There was a problem reading data from the CD-ROM. Please make sure it is in the drive. If retrying does not work, you should check the integrity of your CD-ROM.

I'll keep posting on that thread and hopefully manage to find a working solution,

---

### Post by bricedebrignaisplage on 2007-08-26
btw, what is boot.img.gz in ubuntu/dists/feisty/main/installer-i386/current/images/hd-media ?

---

### Post by pxwpxw on 2007-08-27
> **bricedebrignaisplage said:**
> Thanks to all of you for your  interest and your sympathy.

I had a burst of  hope after reading pxwpxw's post: I have 2 ISO on my HD: one for ubuntu and the other for xubuntu (which I'm trying to install), and I am using the kernel and initrd found on the ubuntu repository. So maybe a matching problem.

But no. I tried again after removing the xubuntu ISO but it still fails. The funny thing is that the ISO is found and mounted on /cdrom. But still the installer complains:


I'll keep posting on that thread and hopefully manage to find a working solution,

Yes that is exactly what happens if there is something wrong with the iso - not necessarilly an errror at that stage..It gets it mounted and then gives up, it might be doing a release check or md5sum check. You can list the files it has mounted on  /cdrom  to make sure it is mounting the correct one.

I assume you are using the hd-media installer images, and running expert install.
======

re your 2nd post about boot.img.gz
Installation Guide - Section 4. - for usb or floppy boot, not your problem here
[https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html)

---

### Post by bricedebrignaisplage on 2007-08-27
> **pxwpxw said:**
> Yes that is exactly what happens if there is something wrong with the iso - not necessarilly an errror at that stage..It gets it mounted and then gives up, it might be doing a release check or md5sum check. You can list the files it has mounted on  /cdrom  to make sure it is mounting the correct one.


It is mounting the correct one. Is there any way I can force it to carry on? I downloaded the ISO again, thinking that the md5sum check error might come from a corrupted download but it resulted in the same problem.

> **pxwpxw said:**
> 
I assume you are using the hd-media installer images, and running expert install.

I am using the hd-media installer images. I don't think I am doing an expert install. At no point I am asked if I want to go expert. I repeat for clarity: I am using initrd.gz and vmlinuz downloaded from [http://ftp.science.nus.edu.sg/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/]("http://ftp.science.nus.edu.sg/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/") and the ISO image from [http://ftp.science.nus.edu.sg/linux/ubuntu-ISO/feisty/ubuntu-7.04-desktop-i386.iso]("http://ftp.science.nus.edu.sg/linux/ubuntu-ISO/feisty/ubuntu-7.04-desktop-i386.iso")  all of them in C:\ (FAT partition). I boot the kernel using GRUB (on a floppy):
```

root (hd0,0)
kernel /vmlinuz root=/dev/ram ramdisk_size=12000 rw
initrd /initrd.gz
boot

```
The installer menu then appears and I follow the installation procedure. I'm never asked about going expert...

---

### Post by pxwpxw on 2007-08-27
I think the problem may be the Desktop CD version. I have only ever used the Alternate or Server version, both are straight install iso, with text based menu installers. I think the hd-media images are expecting the alternate or server version (there are some different files).
I dont know how they would handle a Live Desktop cd.
Also I doubt that the extra kernel args "root=/dev/ram ramdisk_size=12000 rw" are necessary, but if they work, leave them (I have not used them).
You probably dont need the expert option, you can always have a trial run to see how it goes.
You may need to specify the boot partition, but it should cope with windows / linux dual booting.

Alternate version
[http://ftp.science.nus.edu.sg/linux/ubuntu-ISO/feisty/ubuntu-7.04-alternate-i386.iso](http://ftp.science.nus.edu.sg/linux/ubuntu-ISO/feisty/ubuntu-7.04-alternate-i386.iso)

The server version has no desktop, you install that later, its just quicker if you are testing.
[http://ftp.science.nus.edu.sg/linux/ubuntu-ISO/feisty/ubuntu-7.04-server-i386.iso](http://ftp.science.nus.edu.sg/linux/ubuntu-ISO/feisty/ubuntu-7.04-server-i386.iso)

---

### Post by bricedebrignaisplage on 2007-09-04
I finally managed to install Kubuntu to my Sony VAIO laptop with no bootable CD drive: I had to unmount my hard disk and plug it to another laptop with a bootable CD drive! Initially I wanted to install Xubuntu to save some resources, but I had problems on the way: I think the CD drive on the host laptop has flaws so I had problem running the installer from the live CD.

I tried to install from the HD following that guide [https://help.ubuntu.com/community/Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux") using Knoppix but it didn't work either: the installer hanged after the partitioning stage while detecting file systems. weird!

Anyway, I managed to install from the Kubuntu live CD, and when I plugged back my HD in the original laptop it worked.

I'm still having one problem: I can't connect to the network. The card is recognized and the wireless network detected with a good signal strength. However, impossible to connect, it seems DHCP can't get an IP address. Is it possible that it comes from the fact that the laptop I used for installation had a different HW? It had a built in wireless interface and mine uses a PCMCIA wireless card.

---

### Post by pxwpxw on 2007-09-05
Yes I would say thats the problem, you need driver for the PCMCIA wireless, but sorry I cant help with that one. Maybe a new thread with "wireless and pcmcia" in the title?

---

### Post by Herman on 2007-09-05
Yes, here's how I fixed mine if it's any help (by getting help from others), 
[Setting up my Acer Aspire Notebook for Wireless Networking in Ubuntu]("http://users.bigpond.net.au/hermanzone/p11.htm#wireless_network_configuration").
Wireless networking isn't my field of expertise, but there are lots of others around here who should be able to help you I think.
Regards, Herman  :)

---

