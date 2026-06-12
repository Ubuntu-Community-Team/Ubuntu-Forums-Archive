---
title: "Errno 5 Input/output error The Installer encountered an error copying files"
date: 2016-08-22
forum: Installation &amp; Upgrades
---

### Post by nxr564 on 2016-08-22
Edit: Nevermind. I checked the md5 checksum of the  .iso I downloaded and it turned out that they didn't match; it was  probably corrupted, so that may explain why it didn't work properly.  Anyway, I downloaded the 64-bit .iso from somewhere else and it worked.

Ok, so I did some research through Google and found that I had to download unetbootin. I have Windows 7 Home Premium and VMware Workstation Player 12.1.1. I downloaded unetbootin. I have two problems. The first problem started when I used unetbootin to download Ubuntu 16.04 Live (32-bit). I downloaded that and I had Ubuntu installed on my USB flash drive, which is 16 GB. And then I created a VM using the PLOP Manager .iso. I chose 100 GB of hard disk space and 4 GB of RAM. I stored the VM somewhere on my external hard drive, which is 1 TB. So I went to the VMware Player, started up the VM, and then I connected the flash drive to the VMware Player. And then I chose to connect to USB and it brought up unetbootin. I choose "Install". The installation went smoothly. I created a username and password and I had to reboot the computer. Ok, now the problem is, when I started up the VM again, this time it attempted to actually go straight into Linux, but nothing happens. It's just a big black screen. Now, if I were to have chose the Default at the unetbootin, I wouldn't have had this problem. In fact, if I had just chose Default, I'd load directly into Ubuntu without having to install and I just log out and shut down with no problems. When I start up the VM, it'll bring up the unetbootin screen again and it'll give me the options. I choose Default and loads with no problems. The problem occurs when I choose to Install and leads me to the black screen.

That was the first problem. Now the second problem is, I used unetbootin and this time I chose Ubuntu 16.04_Live_x64. So it downloaded the 64-bit .iso and installed it to my flash drive. When I was done with that, I created a new VM using the PLOP Manager .iso file and chose 100 GB of hard disk space and 4 GB of RAM. Then I started it up, connected the USB flash drive, and chose USB, and unetbootin screen came up. Now I chose Install. When I finished answering all the questions like username, computer name, password, where are you, do you want to wipe out the drive, ect. I chose to wipe the hard drive by the way. So once I did that, it started doing the Copying Files. When it reached near to the end, like maybe 70%, it popped up this error. "The installer encountered an error copying files to the hard disk: [Errno 5] Input/output error This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed,  to clean the CD/DVD drive lens (cleaning kits are often available from  electronics suppliers), to check whether the hard disk is old and in  need of replacement, or to move the system to a cooler environment.". Ok, but the thing is I'm using the flash drive as the destination to install Ubuntu, just like when I was installing Ubuntu 32-bit. So what bothers me is why does this error come up?

---

### Post by joshuayip on 2016-09-22
Ok I have encountered this again and again. So this time I make sure I let every one know how I fixed this errno5. Build your live cd / usb using Rufus with the DD method. I have been getting the same problem with ubuntu-16.04.1-desktop-amd64.iso. BUT ubuntu-16.04-desktop-amd64.iso works without any problem! Dont know why. But it just works

---

### Post by ajblackx on 2017-07-30
> **joshuayip said:**
> Ok I have encountered this again and again. So this time I make sure I let every one know how I fixed this errno5. Build your live cd / usb using Rufus with the DD method. I have been getting the same problem with ubuntu-16.04.1-desktop-amd64.iso. BUT ubuntu-16.04-desktop-amd64.iso works without any problem! Dont know why. But it just works

This also worked for me while installing Kubuntu 17.04.

---

### Post by sali77 on 2018-02-23
hello every one, I just have solved this problem by downloading the ubuntu iso file again. the first iso I used was corrupted. use the instruction of page below to see if your iso file is corrupted or not:

[https://help.ubuntu.com/community/HowToMD5SUM]("http://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by coffeecat on 2018-02-23
Back to sleep, old thread.

Closed.

---

