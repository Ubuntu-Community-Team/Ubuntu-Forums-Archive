---
title: "xubuntu on an old toshiba laptop"
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by qiemem on 2006-08-04
Hi everyone. I'm trying to make an old laptop of mine useable again and, after having such a great experience with Ubuntu, I thought I'd give Xubuntu a shot. Here's what I got:
Toshiba Satellite 1730
Pentium Celeron 700 MHz
64MB Memory
10GB HDD
([here]("http://linux.toshiba-dme.co.jp/linux/eng/spec.php3?model=PS170U-000")'s the rest of the specs if you need em)
Anyway, so whenever I try to boot from CD, everything seems to load fine, but when it tries to actually start, after taking a long time reading the disc and loading things in the background, it simply freezes. I get cursor control, but nothing else comes up. I've tried both the the normal run off disc option  as well as graphical safe mode. I'm pretty new at this stuff, and am trying to do this both because I want to use this laptop and for the learning experience. I'm running a memory test right now, but so far everything is checking out. Anyone have any ideas? Is Xubuntu even the way to go in this situation or is there another distro I should try? Any help would be much appreciated.

---

### Post by Jack W on 2006-08-05
I have xubuntu running on an old Toshiba Cel. 500 meg. laptop and working great. Only thing for me to play with was to use the vesa video driver. It's an old 2210 XCDS with 192 mb ram

---

### Post by Metacarpal on 2006-08-05
Hi qiemem,

Did you download the "Desktop" or "Alternate install" CD?

The desktop CD is a LiveCD - that is, it runs the OS from the disc.  That one needs about 256+MB of RAM to load up.

The alternate install CD is what you need to go for.

---

### Post by r4ik on 2006-08-05
If you have a computer with rather modest specifications (I'd say anywhere between 128 MB of RAM to 256 MB of RAM), you may find that Kubuntu's KDE and Ubuntu's Gnome are too slow on your computer to be functional. There's another desktop environment called XFCE that is rather lightweight, and the nickname for it is Xubuntu. If you have 64 MB of RAM or less, you should consider using Damn Small Linux.

---

### Post by qiemem on 2006-08-05
Oh, I see what the problem is... duh... I was trying to run the LiveCD (trying to decide between this and some other distros). Course, with only 64mb of ram, that's not really possible. I'll download the alternate and try that out. Thanks!

---

### Post by qiemem on 2006-08-05
r4ik,
How do you think Xubuntu will run with only 64mb? I running DSL off a cd, and it was certainly lightweight and worked fairly, but seemed too rough. I think I'm looking for useablity over lightweightiness, but I don't know if that's possible with the POS I'm working with.

---

### Post by r4ik on 2006-08-05
I dont think it will be realy useable 64mb RAM wont do the job imo.

---

### Post by r4ik on 2006-08-05
Did you concider DSL-N it is now upto RC3

[http://www.damnsmalllinux.org/dsl-n/](http://www.damnsmalllinux.org/dsl-n/)

1. Kernel 2.6.11 and modules
2. Mozilla Suite 1.7.12, browser,mail,irc,etc.
3. Mplayer 3.3.5 audio and video
4. Leafpad 0.7.9 editor/notepad
5. Abiword 2.2.7 wordprocessor
6. Gnumeric 1.4.3 spreadsheet
7. gTFP 2.0.18 ftp client
8. gaim 0.77 IM client
9. Xpdf 3.0.0 pdf viewer
10.Emelfm 0.9.2 file manager
11.Xpaint 2.7.6 paint program
12.Cups 1.1.14 printing
13.unionfs supported as an optional boot parameter
14.MyDSL system of extensions
15.Frugal Installs
16.USB Pendrive Install

---

### Post by qiemem on 2006-08-05
I got Xubuntu up and running just fine. Installation was very easy. However, while it was useable, it ran pretty slow.

I decided I may as well try some other distros just to see if anything works better. I tried Vector first, and everything installed okay (though I must admit, it was quite a bit more confusing than the Xubuntu install. All sorts of options I knew nothing about). When I tried to startup, however, I got a grub error (error 15), which is funny because Vector uses Lilo and I chose not to install it anyway because I only need the one partition. Grub left over from my Xubuntu install maybe?

Anyway, I didn't really feel like messing with it, so I decided to try out dsl-n (thanks r4ik). Everything has installed fine, though I'm a little worried because this still seems a bit above my head.

I don't have any questions, just figured posting my experience might be helpful for others wishing to do something similar. If you wish to impart any wisdom to me however, feel free. It would be appreciated.

---

### Post by r4ik on 2006-08-05
Thanks for sharing youre experience i think i would be a good thing,stating the obvious here, if you tried to get some more RAM.
That would realy help.
About the GRUB error a list of it can be found here,

[http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors)

Good luck !

---

### Post by mojoman on 2006-08-05
Jack W > I have xubuntu running on an old Toshiba Cel. 500 meg. laptop and working great. Only thing for me to play with was to use the vesa video driver. It's an old 2210 XCDS with 192 mb ram

Jack W, Could I ask what videocard your laptop have? I'm running Xubuntu on a Toshiba Satellite 1800-504, 1 GHz, 256 MB RAM which has a Trident CyberBlade Ai1. It's i supposed to be supported but it is identied as Trident CyberBlade i1. Also, video is jerky and gets out of synch and the graphic isn't as fast as I'd like it to be. My bet is that it's a driver issue but I haven't tried the vesa driver.

Best regards
/Mojoman

---

### Post by K.Mandla on 2006-08-05
> **r4ik said:**
> i think i would be a good thing,stating the obvious here, if you tried to get some more RAM.
That's the best solution. A 128Mb stick of PC100 on top of your nonremoveable 64Mb will give you more than enough to run Xubuntu. And a used stick off eBay will probably cost you $20 with shipping included. 

Go for it! :D

---

