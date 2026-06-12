---
title: "Installing Ubuntu to boot with USB for use on an old NetBook, anything I should know?"
date: 2015-07-07
forum: Installation &amp; Upgrades
---

### Post by poly2 on 2015-07-07
Hey! New to Ubuntu here. My primary workstation has been too full of distractions for me to do my creative writing and soon to do college work. I can't afford a good laptop for at least 6 months so I've decided to use my old Acer Aspire One netbook from 08' for the time-being. Booting it up for the first time in years to windows 95 brought some great memories. I don't want to install to the HDD, one of the main reasons being that the HDD is pretty old and has limited capacity. I just picked up a Corsair Voyager Go 64gb (default format Fat32) and I'd like to boot with that, which is nice considering I can easily boot using other computers if ever needed. 
Anyway, the USB drive should be here in a few hours (thank you, Amazon Prime). Is there anything I should look out for, in terms of compatibility? I'll be installing using the recommended Penidrivelinux from my primary PC when it gets here, but what version should I select? 32bit, I assume? 
Here's my [Netbook model]("http://www.engadget.com/products/acer/aspire/one/zg5/specs/"), please don't laugh at me.
Please be as clear as you can, I don't want to screw anything up.

Thank you!

---

### Post by ubfan1 on 2015-07-07
Yes 32 bit for that cpu.  With 1G ram, you better try Lubuntu instead of Ubuntu.  Use a Long term support version (14.04).  Do see if you can add another 1G of ram.  Should be OK, I have a similar MSI netbook and it's fine.  If you have trouble with pendrivelinux, try unetbootin.

---

### Post by poly2 on 2015-07-07
> **ubfan1 said:**
> Yes 32 bit for that cpu.  With 1G ram, you better try Lubuntu instead of Ubuntu.  Use a Long term support version (14.04).  Do see if you can add another 1G of ram.  Should be OK, I have a similar MSI netbook and it's fine.  If you have trouble with pendrivelinux, try unetbootin.

[Alright, about to install]("http://gyazo.com/5ea13fe6bc3c2f4bfce44b071bd4908e").
I downloaded the 32bit Lubuntu LTS Standard PC iso from [here]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu/LTS").
Should I use the option "Space used to preserve files across reboots?"

Thank you.

---

### Post by monkeybrain20122 on 2015-07-07
You should go for puppy-linux if you want to run off a usb drive and your machine is rather old. Pendrive linux is about running live session, not a real install (and you need persistence to save your data). You can install *buntu into the flash drive like you would to the internal hd but that would be slow and your old hardware is not helping (installing in external hd with usb2 connection can be as fast as internal though)

---

### Post by poly2 on 2015-07-07
> **monkeybrain20122 said:**
> You should go for puppy-linux if you want to run off a usb drive and your machine is rather old. Pendrive linux is about running live session, not a real install (and you need persistence to save your data). You can install *buntu into the flash drive like you would to the internal hd but that would be slow and your old hardware is not helping (installing in external hd with usb2 connection can be as fast as internal though)

So what was suggested above would not be what I need?

EDIT: I see what you mean. Yes, I'm trying to find out how I can do a full install on the USB, that saves data and software as you would expect from a normal HDD install. Can you explain to me how I can do this? I've found a lot of resources, but I've been getting lost in links.
I did come across a program called Refus, which from first glance appears to allow me to easily do a full install to a USB? Should I use Refus with a Puppy-Linux iso? 
Also, is puppy-linux compatible with Ubuntu software such as [this]("http://sourceforge.net/projects/plume-creator/") ?

Thank you.

---

### Post by ubfan1 on 2015-07-07
"Space used to preserve files across reboots?" sounds like persistence, used for your files and for some package updates (can't run all system updates with this).  With your USB fat32, you have a max file size of 4G, so since the persistence  file (named casper-rw) is limited to that, you might consider a separate partition labeled "casper-rw" with an ext2 filesystem (or ext4 with journaling turned off).  
  There are lots of threads here on optimizing performance on a live media, but most involve moving things into ram, which in your case is a limiting resource.  Try some, the "toram" option on the grub kernel boot line can be edited in to see if you have any free ram left after copying the compressed filesystem into ram.  Can't say much about Puppy, but I think it's doing pretty much the same think, moving into ram.  Pretty easy to to both and see what you like.  A full install of Lubuntu to the USB would run faster than the live media.

---

### Post by yancek on 2015-07-07
Another option is to burn the Lubuntu iso to a CD/DVD (depending upon size) and use another computer to do a standard install it to your 64GB flash drive if you have one available.   If that option isn't available, then doing an install with persistence and a separate casper-rw partition would be the best option.

---

### Post by oldfred on 2015-07-07
Some of the differences.
 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

A full install to any flash drive or external drive is just like any other install, but you need to use Something Else as that is the only option that lets you choose to install the grub2 boot loader to the external drive. Lubuntu screens will be similar, but not identical to examples below.

      
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

---

### Post by gordintoronto on 2015-07-08
Use Pendrivelinux to put Lubuntu on a small flash drive, then use the netbook to do a real install onto the big flash drive. It's going to take a long time, maybe approaching an hour. And the performance will never be good.

I'm running Xubuntu 15.04 from the hard drive  of an Acer Aspire One, and it's fine until I play video. Many frames are dropped, depending on the resolution of the video. (I just got a camera which records 720P, and it stutters badly.)

---

### Post by C.S.Cameron on 2015-07-08
I don't think pendrivelinux has a tool for doing Full installs.
Searching Sudodus in these forums will yield some nice Linux/Windows tools for writing 'buntu images to flash drives.
It is also easy making a Full install from scratch using the Live DVD.
When the install comes to format use "Something else".
Leave a Gig or so of FAT32 for the first partition so you can copy stuff from Windows computers when not using it to run them.
Make the second partition "/" and make swap as large as your RAM if you need hibernation.

---

