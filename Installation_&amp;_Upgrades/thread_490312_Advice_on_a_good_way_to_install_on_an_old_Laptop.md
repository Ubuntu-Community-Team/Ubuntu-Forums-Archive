---
title: "Advice on a good way to install on an old Laptop"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by jtpryan on 2007-07-02
I was given an older Vaio Laptop.  It has a USB floppy drive, no CD drive, no network connection. A 6 Gb hardrive with 2 partitions, 2 Gb and 4 Gb.  Windows 98 is on the 2 Gb partition. 64 Mb of memory that could only be increased to 128.

I would like to wipe the drive, have one 6 Gb partion, and get Ubuntu running.  It does have one PCMCIA slot.  The best method would be to create a bootable Ubuntu CD, figure out how to boot from a USB CD drive and install from there.  But I see this as frought with problems, not the least of which is I don't have a USB CD drive.  I have a USB HDD I could employ to perhapse get the Ubuntu installation on to the one of the partions, but can I install from a HDD to the same HDD?

Anyway, thoughts would be apprecitated.

-Jim

---

### Post by Beaucephus on 2007-07-02
Can your BIOS even boot from USB?  Thats the first thing to check. If not check into a floppy install.  Have you considered Debian?   It has a network install that uses floppies and then installs the rest over the network.

If you do get a CD method working you should use the **alternate install cd**.  The live CDs tend to not work on older hardware.  Also try xUbuntu as you will probably get a more usable experience.

---

### Post by into_311 on 2007-07-02
I would probably look at a slimmer Linux distro anyways myself.  I'm told all the time that Gnome only runs well on 256 Mb of ram or higher. Also, with a 6 gb partition. That leaves you barely enough room to install the base operating system (around 2GB or so) then 4GB of room for files.

Xubuntu would not be a bad way to go at all. if you are going to go with ubuntu on an older system like that. It uses XFCE for the desktop environment instead of Gnome or KDE. Its a little bit lighter on your resources and slimmed down. It doesn't have as much configuration tools and applications, but its smaller and quicker.

Have you tried looking at damn small linux, slackware, gentoo, or debian w/ the minimal install? Those are better distributions for giving you a more minimal install with just what you need to have a working system. They will run faster and boot quicker on an older system like that.

ubuntu 7.04 has this listed for their system requirements:

System Requirements
The minimum memory requirement for Ubuntu 7.04 is 256MB of memory. With only the minimum amount of memory available, the installation process will take longer than normal, but will complete successfully, and the system will perform adequately once installed.

---

### Post by jtpryan on 2007-07-02
Thanks for the replies.  Maybe I should state what I would like to do with this.  

Browse the web
Use it for a remote portal to my XP Pro media server.

I'm assuming there exists a Linux remote desktop client out there somewhere.  That's it , it's just that it's a nice small system I could use as essentially a remote control for my music.

-Jim

---

### Post by Beaucephus on 2007-07-02
Debian starts off real light but can be easily tailored to those specific purposes.  It uses apt and synaptec for package management which is a real plus.  

I would also check into Mythtv [http://www.mythtv.org/](http://www.mythtv.org/).  When you see it you will want to drop your XP server.

---

