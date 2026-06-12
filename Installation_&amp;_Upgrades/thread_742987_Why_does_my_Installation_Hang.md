---
title: "Why does my Installation Hang?"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by jonbo in Ark on 2008-04-02
--------------------------------------------------------------------------------

Hi folks,

I hope my problem isn't too feeble or obvious. My installation of 7.1 turns to an apparant error message almost right away. I'll start with background info: I was given an Athlon 1024 Mhz or so desktop with a 62 MB HD, wiped. An IT guy I know gave it to me, a very stock looking older machine. So, I said, "I'll try installing Ubuntu on it!" I ordered a set of CD's from someone on Ebay for about $5 + postage, several flavors of Linux. I put the one that said "Ubuntu 7.01" in the DVD spinner after making sure in CMOS that it would check the DVD and booted. I got to the point where I was given several choices. I chose "Install". After a minute I started getting this message:

ta 4096 in
[188.814366] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[188.814366] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 da

ta 4096 in

Those first 3 lines will repeat several times, each time with the first 3 digits inside the square brackets incremented by about 30. After a little while, though, it will just hang with that last line.

Can anyone tell me what's going on? Do I have a 64 bit version, or something, that I'm trying to install on a 32 bit machine? I ran the memory checker on the installer. After about an hour of checking memory, while I was distracted, the screen went back to those strings above.

Any advice will be much appreciated.

JS

---

### Post by housam on 2008-04-02
> **jonbo in Ark said:**
>   I was given an Athlon 1024 Mhz or so desktop with a 62 MB HD, wiped.


ubuntu need at least 4 GB of space and 256 MB of RAM.

---

### Post by jonbo in Ark on 2008-04-02
Sorry, I've communicated carelessly and stupidly.

HD - 60GB
DRam - 504 MB according to the memory tester on the Ubuntu 7.10 CD.

---

### Post by jonbo in Ark on 2008-04-02
Okay, let me amend that with a little more information.

There is one 512 MB stick of Dram 133 Mhz.
In BIOS the DRAM frequency is 100 MHZ.
The processor is a 1100 MHz AMD K7 Athlon. The multiplier in BIOS is set at 11.

thanks much.

JS

---

### Post by frogeyes on 2008-04-03
Have you tried another distro ? if so what happens:)

---

### Post by jonbo in Ark on 2008-04-03
Funny you should ask. I installed Mandriva last night. It didn't complain. However, being a rookie with Linux distros, I have no idea what to do next, or even how to control an installation. For example, Mandriva installed completely by asking me a few simple questions using a graphical interface. At no point that I could tell did I have any options to decide how to partition the hard drive. Now when it boots the graphical desktop shows 2 hard disks, an about 40 G one and an about 8 G one. I presume that's how it partitioned. That's just an example of my Linux naivete, but Mandriva did install just fine.

I'd still like to install Ubunta. I understand one can do a lot with it. I'm gonna try and use a cell phone interface to access the 'net. My cell phone company provides the service. They provide software -for Windows, of course. I found a forum where someone had written lines of text to set it up. -on a Ubunta installation. I'm going to try to do something like that. However, I first have to get it to install. The goal I've mentioned here may seem ridiculous for someone like me who couldn't even figure out how to "mount" the 2nd CD player on the system when I booted to Knoppix, but I have time, patience, I want to learn, and I'm in no big hurry.

Oh, a little more info. As you can gather above, the system will boot to Knoppix, and also to a Mandriva installation.

When it hangs displaying that arcane-looking text, right before it displays those strings it displays a string:
(initramfs)
Is it attempting to create a ramdrive for the install, and failing?

Again, any help is much appreciated.

JS

PS I might not be able to reply until noon CST, or this evening, but thanks for any help.
J

---

### Post by jonbo in Ark on 2008-04-03
Is it considered bad form to bump this back up?

---

### Post by jonbo in Ark on 2008-04-03
Buu-uummp.  help... me!  Help... me!

---

### Post by jonbo in Ark on 2008-04-04
I tried switching out the CDRom drive and making the DVD drive master and booting from that and vice versa. Nothing.

---

### Post by jonbo in Ark on 2008-04-04
I don't know what I'm doing here. I tried entering the command "root = /dev/cdrom prior to installation. Nada. At the (initramfs) prompt I found in / the directory cdrom. It's empty. I don't know enough.

---

### Post by jonbo in Ark on 2008-04-04
Bump.

---

### Post by makhand on 2008-04-22
same problem here. however, my machine is no old machine. It's a dell vostro 200. Just bought it. does anyone know how to approach this?

---

### Post by tenub on 2008-04-25
I have the same problem...brand new computer too.

---

### Post by welshmike on 2008-04-25
I’ve read a lot of positive things about Ubuntu so I decide to try it out.
I had previously installed Fedora 8 and my desktop currently can dual boot and run XP or Fedora 8. The latter installed without problems and runs trouble free.
When I went through the install process of xubuntu-7.10-desktop-i386.iso it first produced a message:
8139cp …  this (id 10ec:8139rev10) is not a 8139cr compatible chip
8139cp   trying the “8139t00” driver instead
Some 20 or so seconds later the install hung.
I then attempted to install ubuntu-8.04-rc-desktop-i386.iso .
The same two messages appeared and shortly after a message stating “starting Gnome” a message “… deferred execution …” appeared very briefly. The monitor screen went blank and the install hung

Can the team help please and what info about my desktop do you need?

---

