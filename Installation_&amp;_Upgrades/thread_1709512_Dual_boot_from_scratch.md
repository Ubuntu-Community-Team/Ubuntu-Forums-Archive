---
title: "Dual boot from scratch"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by nickjbanks on 2011-03-18
I want to set my laptop up for dual boot in Windows7 and Ubuntu. I could do with some help or pointing to a good on-line guide. I'm putting a new HDD in at the same time so I can set it up in any order. The plan is to have a partition for Ubuntu, one for windows and and larger one for documents/music/pisc/etc.

Should I partition it first using a usb caddy? If so what sizes would be good, its a 320Gb HDD but I want a lot of space for docs etc?

What goes on first Ubuntu or Windows?

---

### Post by Megaptera on 2011-03-18
Here's some basic reading to get you started. The version of Ubuntu in this one is an old one (colours give it away) but the process is the same in 10.04 [http://www.howtogeek.com/howto/9059/dual-boot-your-pre-installed-windows-7-computer-with-ubuntu/](http://www.howtogeek.com/howto/9059/dual-boot-your-pre-installed-windows-7-computer-with-ubuntu/)

Some basic partitioning info [http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/](http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/)

Scheme for sharing data 'tween Windows and Ubuntu [http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)
I'm sure others will post advice & help too.
Installing Windows and then Ubuntu is easier 'cos Ubuntu's grub (boot) will find Windows whereas the other way round is still possible but requires a bit more setting up. As you've got the choice I'd suggest Windows first then Ubuntu.

---

### Post by Dutch70 on 2011-03-18
> **nickjbanks said:**
> I want to set my laptop up for dual boot in Windows7 and Ubuntu. I could do with some help or pointing to a good on-line guide. I'm putting a new HDD in at the same time so I can set it up in any order. The plan is to have a partition for Ubuntu, one for windows and and larger one for documents/music/pisc/etc.

Should I partition it first using a usb caddy? If so what sizes would be good, its a 320Gb HDD but I want a lot of space for docs etc?

What goes on first Ubuntu or Windows?

Install windows first. It will take the entire drive. Then go into windows disk management tool & shrink windows to the size you want it. 

From there, you'll be doing everything else from Ubuntu. First download the live cd/usb. A usb stick is easier & faster if you have one. You can get everything you need here...
[[COLOR="Blue"]http://www.ubuntu.com/desktop/get-ubuntu/download[/COLOR]]("http://www.ubuntu.com/desktop/get-ubuntu/download")
Alternatively, you can use Unetbooting to create the usb stick.
[[COLOR="Blue"]http://unetbootin.sourceforge.net/[/COLOR]]("http://unetbootin.sourceforge.net/")

Boot into the live cd/usb. Choose "Try Ubuntu" to make sure it will work well with your hardware. Then Open Gparted & use the unallocated space to create an extended partition. You'll want to create at least 2 partitions. One for Swap equal to the size of your RAM. The rest for Ubuntu itself. Format it to ext4. 

ps. You can also make a separate /home partition. If you do, then make the partition for the Ubuntu system 10-20GB leave the rest for /home which is equal to documents & settings in windows.

Everything for Ubuntu will be logical partitions inside the extended partition.

I couldn't seem to find the how to I was looking for, maybe someone else will have a better one. These may come in handy though.
[[COLOR="Blue"]https://help.ubuntu.com/community/WindowsDualBoot[/COLOR]]("https://help.ubuntu.com/community/WindowsDualBoot")
[[COLOR="Blue"]http://lifehacker.com/#!5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony[/COLOR]]("http://lifehacker.com/#!5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")

---

