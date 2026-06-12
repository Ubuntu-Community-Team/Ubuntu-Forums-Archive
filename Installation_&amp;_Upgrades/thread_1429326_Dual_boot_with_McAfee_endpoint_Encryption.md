---
title: "Dual boot with McAfee endpoint Encryption"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by orbita on 2010-03-13
Hi, I'm a newbie Linux user.
 
My work laptop dual boots Vista and Ubuntu 9.10. Recently my company has forced installation of McAfee Enpoint Encryption (EEPC 5) which replaced GRUB2 with its own log on screen. The linux partition is not encrypted since I can access it with the LiveCD.
 
I don't want to mess up with EEPC mbr so I tried to install GRUB2 on Ubuntu partition boot sector (and to use Vista boot loader to boot Ubuntu) but it didn't work. 
 
$ sudo grub-install /dev/sda5
Could not find device for /dev/sda5
 
Is there a way to install GRUB2 to a USB drive and somehow point it to boot the installed Ubuntu partition? 
 
It'll be like whenever I want to use Ubuntu, I'd plug in the USB drive and the Linux partition on my hard drive would boot up. I don't like to install Ubuntu directly on the USB for performance reason.
 
I did read through GRUB2 documentation but couldn't make out much of it, especially the configuration section.
 
Thanks very much.

---

### Post by Herman on 2010-03-14
[How To Make a GRUB2 USB Disk]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB") - with an editable grub.cfg

 Try the link (above), and see if you can do it.
 
It doesn't matter if you already have files in the USB, GRUB2 will just install in a new folder beside your existing files and GRUB2 even works in NTFS file systems now so you don't even need to reformat or partition your USB drive. :D

If you have trouble understanding anything in that how-to just let me know and I'll try to explain and I'll improve the how-to for the next person who wants to use it.

---

### Post by orbita on 2010-03-14
Thanks Herman. Your link really helped :)

I'd like to share how I managed to dual boot Vista and Ubuntu with Safeboot (EEPC) installed on the Vista's partitions.

1. Install GRUB2 to the USB drive as described in Herman's post. Let's say USB drive is /dev/sdb

2. sudo fdisk -l    (to indentify the Ubuntu installed partition. Let's say it's /dev/sda5
    sudo mount /dev/sda5 /mnt
    sudo grub-install --root-directory=/mnt /dev/sdb
    
3. Configure BIOS to boot to USB hard drive first

Problem faced:

I was trying to configure the grub.cfg to add a entry of Ubuntu on my installed partition. It didn't work. There is no grub.cfg on my USB drive. 
Using "sudo grub-mkconfig -o /media/MyUSB/boot/grub/grub.cfg" didn't work either (it might be because I'm using the liveCD, not an actual Ubuntu).

I can get GRUB's boot OS options whenever I plug in the USB and I can see the Vista partition (encrypted) on it too. I don't dare to try it. Will choosing Vista in GRUB corrupt the EEPC's mbr? 
For now whenever I need Vista, I remove the USB and restart my laptop. Then I get something like "Boot device not found" when the laptop restarted (really scary :-SS). 

The laptop needs to reboot one more time then only can EEPC load.

I really have no idea why my steps above worked. Really appreciate if some one can point out what was really happening.

---

### Post by Herman on 2010-03-14
> Problem faced:

I was trying to configure the grub.cfg to add a entry of Ubuntu on my installed partition. It didn't work. There is no grub.cfg on my USB drive. 
Using "sudo grub-mkconfig -o /media/MyUSB/boot/grub/grub.cfg" didn't work either (it might be because I'm using the liveCD, not an actual Ubuntu).
The live CD doesn't have GRUB2 installed in it in the same way as an operating system does, it boots with syslinux, but it does contain a copy of GRUB2 files in it somewhere.
I suppose when I wrote that how-to I was working from another Ubuntu operating system in a USB so I didn't run into that problem. Okay, thanks, I'll need to fix that how-to.

So I guess you're getting GRUB's Command Line Interface. You should be able to boot Ubuntu by using the right commands, and then continue where you left off with the earlier how-to and install the configuration file from your installed Ubuntu ,  [GRUB2 How To Boot From CLI Mode]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html") -  NEW!  Rescue your System .

There are other ways to boot Ubuntu even if you don't like using the command line, you can alternatively use a GRUB@ Super Grub Disk, sublinked from that link I just gave you. The last time I checked the GRUB2 version of Super Grub Disk was able to boot Ubuntu okay, but it didn't have the number of options and menus in it as the old Legacy GRUB Super Grub Disk. I'm not sure but it might boot your Ubuntu from a menu. Otherwise you'll still need to use the Command Line Interface but from Super Grub Disk instead.

---

### Post by Herman on 2010-03-14
> Problem faced:

I can get GRUB's boot OS options whenever I plug in the USB and I can see the Vista partition (encrypted) on it too. I don't dare to try it. Will choosing Vista in GRUB corrupt the EEPC's mbr? 
For now whenever I need Vista, I remove the USB and restart my laptop. Then I get something like "Boot device not found" when the laptop restarted (really scary :-SS).by 'GRUB's boot OS options' I'm guessing you mean [GRUB's Command Line Interface]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20CLI%20Mode%20Commands.html")?
You should be able to boot Vista by chainloading either the hard disk's MBR or even Vista's boot sector, either way Vista should boot, or at least most Vista installations shoudl. I don't know anything about how your McAfee Enpoint Encryption (EEPC 5) will affect the boot sector.
GRUB doesn't install anything when it boots another operating system, so you can boot Vista with GRUB, a lot of other Vista users have already been doing that for years so I think it's quite safe.
GRUB will do as you tell it to though, so you needed to be careful when you installied GRUB to the USB make sure it installed to the USBs MBR and not the hard disk's MBR. From now on you don't have anything to worry about. :)

---

### Post by Herman on 2010-03-14
> Problem faced:

For now whenever I need Vista, I remove the USB and restart my laptop. Then I get something like "Boot device not found" when the laptop restarted (really scary :-SS). I'm guessing, (and hoping), it's only because you forgot to reset your BIOS disk order and you didn't accidentally install GRUB to MBR in your hard disk drive.
It can be tricky installing GRUB in a USB because while most copmnuters automatically list a USB drive as the last drive number in the boot list, there are a few which give the USB automatic priority, meaning the USB will become drive number1. That means if somebody is installing GRUB in such as situation they need to install GRUB to drive number 1 instead of drive 2, which will be the computer's hard drive in that particular computer. My Eee PC is like that.

In steps 5 and 6 of the how to, [How To Make a GRUB2 USB Disk]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB") I showed using the blkid command to dicover which is the USB and which is the hard disk, but at the time when that was made, GRUB2 was only for experts. I need to review that part of it and emphasize the importance of getting that part correct for people who may not be so experienced with Linux.
> The laptop needs to reboot one more time then only can EEPC load.Oh, okay, so yours is installed to the right MBR, but your PC's BIOS takes an extra reboot for the P.O.S.T. in the BIOS to detect there's no USB anymore and decide to boot the first hard disk maybe. :)

---

### Post by Herman on 2010-03-14
> I really have no idea why my steps above worked. Really appreciate if some one can point out what was really happening.I'll have to get back to you on that. Right now it's early on a Monday morning in my part of the world so I'm on a time limit right now, to get ready for work.
However I'd be happy to come back later and explain more about GRUB and MBRs, boot sectors, BIOS boot order, and all that kind of stuff for you, whatever you want to know about.
Sorry to keep you waiting, I'll be back soon.  :D

---

### Post by Herman on 2010-03-15
```
sudo fdisk -l    (to indentify the Ubuntu installed partition. Let's say it's /dev/sda5
    sudo mount /dev/sda5 /mnt
    sudo grub-install --root-directory=/mnt /dev/sdb
```> I really have no idea why my steps above worked. Really appreciate if some one can point out what was really happening.     The grub-install command made a /boot/grub, directory in /mnt which contains all of the files that GRUB needs.
The only file it doesn't have yet is the configuration file, /boot/grub/grub.cfg.

The same command also installed the new GRUB to MBR in /dev/sdb, which is your USB drive's MBR.
We say it 'installed GRUB to MBR' because it's quick and easy to say that and most people know what we mean. However, that's not true at all. We installed GRUB in the USB's new /boot grub directory, and we installed code in the USB's MBR to make it point the BIOS to GRUB files in the /boot/grub directory.

At this stage if you had tried booting the USB disk, you would see GRUB's Command Line Interface because there's no boot/grub/grub.cfg file yet to tell GRUB how you would like your GRUB Menu to look and what commands it should include.

You should be able to boot Ubuntu just about any operating system using GRUB's Command Line Interface if you know that right commands.

---

### Post by Herman on 2010-03-15
Once you have Ubuntu booted up and running you could then run 'sudo grub-mkconfig -o /media/MyUSB/boot/grub/grub.cfg', and from that time on you should have a GRUB Menu to make booting a lot easier for you.

---

### Post by orbita on 2010-03-19
Thanks so much, Herman. Your posts are super insightful ;)

---

### Post by paulrf on 2010-04-07
I have a similar issue, but I already had Ubuntu 9.10 installed before I installed XP and encrypted it with Mcafee Endpoint Encryption.  I'm now trying to figure out how to configure the XP drive in Grub2.  It's installed as my second drive.  I created a MBR from the Windows drive:
[FONT=comic sans ms]dd if=/dev/sdb of=/usb_drive/safeboot.mbr bs=512 count=1[/FONT] as noted in: [http://mcafee-ext.hosted.jivesoftware.com/thread/19902?tstart=-2](http://mcafee-ext.hosted.jivesoftware.com/thread/19902?tstart=-2) , and I created a 11_xp file in the /etc/grub.d directory.  After update-grub2, Windows XP appears in my Grub menu, but it's not recognizing the mbr file as valid.  I don't know if A) the mbr is invalid, or B) my snytax is invalid or if it's just impossible to run Mcafee End Point Encryption from within Ubuntu 9.10.

Example of grub.d file:

#!/bin/sh -e
echo "Adding Windows XP to GRUB 2 menu"
cat << EOF
menuentry "Windows XP Work" {
set root=(hd1,1)
chainloader (hd0,1)/safeboot.mbr
}
EOF 

Again I have two drives..  Ubuntu 9.10 is on /dev/sda1 and the encrypted XP is on /dev/sdb1

Any help would be much appreciated...

Thanks
Paul

---

### Post by Herman on 2010-04-07
:) Probably one of the greatest tips anyone can give another person who's interested in boot loaders and booting is to learn how to use GRUB in Command Line Mode. 
You can enter CLI Mode by pressing your 'c' key from your GRUB Menu. 
GRUB is almost lile a mini operating system by itself. It doesn't take much to get the hang of it and when you do it makes it really easy to try things you're not sure of and find out what commands will work, then when you get a successful boot you can 'set those commands in stone' later by writing them to your GRUB files. [GRUB2 CLI Mode]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20CLI%20Mode%20Commands.html"). 

Further, since you have two hard disk drives, you can probably skip that tutorial and just chainload your second hard disk's MBR from GRUB,
```
[FONT=Bitstream Vera Sans Mono]#! /bin/sh -e
echo "Adding Windows XP to Grub2 menu" >&2
 cat << EOF
[/FONT][FONT=Bitstream Vera Sans Mono]menuentry "Chainload Windows XP" {
    set root=(hd1)
    chainloader +1    
}[/FONT][FONT=Bitstream Vera Sans Mono]
EOF[/FONT]
```That's an interesting tutorial though, thank you for the link, I have it bookmarked.

Regards, Herman :)

---

### Post by paulrf on 2010-04-07
Thank you very much for your reply.  I'm sure your suggestion would work fine if I had a normal copy of XP on my second drive.  Unfortunately, since I have Mcafee Endpoint Encryption installed, I now get "safeboot has been corrupted (err92h) when I attempt to boot.  If I disconnect the drive for Ubuntu, the XP drive loads fine by itself.  There is some part of the master boot record that I'm not replicating with grub2.  That is interesting to know about the grub2 cli though... I'll play around with it some.  

If anyone else has solved the mystery dual boot with Mcafee Endpoint Encryption, I would appreciate info...

Thanks

---

