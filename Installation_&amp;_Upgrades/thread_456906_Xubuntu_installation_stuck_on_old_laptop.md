---
title: "Xubuntu installation stuck on old laptop"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by Znupi on 2007-05-28
I have a really old laptop which used to run Win95. All I know about it is that it has 32 megs of ram and 3GB harddisk. I'm trying now to install Xubuntu on it, using the alternate cd of course, but it's stuck. It said that my system has not enough memory, and that it needs at least 36mb of RAM. I thought "hey, I'm missing 4 megs, shouldn't be a problem"... so it asked me what packages to install, because I couldn't install all, so I selected what seemed more important, like networking, partitioning, etc. It got to the next step where it started loading drivers (I think) but now it's stuck to a black screen with a cursor blinking at the bottom of the screen. Should I reboot and choose less packages? What should I do? Maybe it couldn't detect my CDRom right?

The *beast* is a Compaq Armada 1592DT.

Also I got an ACPI error - Could not locate RDSP right after I selected "Install in text mode".

---

### Post by Znupi on 2007-05-28
What are the minimum packages I need to select for a minimal installation? If I select none, it starts installing, but goes back to ask me again what packages to install. Please help :|.

---

### Post by kerry_s on 2007-05-28
For something like that, you need to go totaly custom.
You need to create your swap first, so it can be used as extra memory during the install. So grab gparted and setup swap(at least 1gig) & the partions for the install-> [http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.4-7.iso?modtime=1179575456&big_mirror=0](http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.4-7.iso?modtime=1179575456&big_mirror=0)

After that grab the net install-> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso)

Your going to need to install a little at a time, first do the server install.
pop the disk in and type> server <this will install the base system.

after that's installed, login and type> sudo su < this will make you root.
type> apt-get install xorg gdm synaptic xfce4
(personally i would go for something lighter)
after all that installs, reboot, login, open synaptic and install what ever else you need.
Good luck.

---

### Post by kerry_s on 2007-05-28
I just now looked the specs for your system, you should just use-> [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/) instead

---

### Post by Znupi on 2007-05-28
Thanks! :)... Well, my hard drive has only 3GB so I can't really setup the swap partition of 1GB... I'm going to try damnsmalllinux...

---

### Post by kerry_s on 2007-05-28
Yeah, i missed that part in your post. Maybe later if you upgrade it. I just spent a week upgradeing a vaio PCG-F430 (450mhz, 64mb ram, 6gig hd) I put in a 20gig hd & upgraded the ram to 256mb which is the max. The hd was the hardest to put in, this thing don't have a hd access panel, i had to disassemable it to get to the hd under the keyboard. But once i got everything in it's working great. I did a custom debian+xfce4 install.

I think DSL will be the best for your system though, but DSL takes a bit of learning to get the most out of it. Make sure you use the forum, there are alot of people there who can help you with any problems you run into. DSL can be very good, i ran that sucker for months in ram on a old laptop with no hd i think i had 128mb and used a usb drive for the swap.

---

