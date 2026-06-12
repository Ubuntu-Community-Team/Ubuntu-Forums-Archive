---
title: "bin/sh: can't access tty; job control turned off"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by dhodg777 on 2007-02-19
First off, computer hardware,

    * Athlon 1.2 ghz thunderbird cpu
    * silurio t400 graphics card (Nvidia)
    * gigabyte GA-7DX motherboard
    * Maxtor 17.2 gigabyte hard drive
    * Hitachi DVD drive (GD-3000)

i have burned 6.10 edgy on to a cd and used the built in disk checking, and it comes out alright, it goes through the pretty colored graphic screen, and after the bar is filled, the screen goes black and a white cursor flashes for about 5 seconds, and then the screen goes black and the activity light on the dvd drive goes out, at the original window with the 5 options, i pressed the F6 key and to the end of the line, i erased "quiet splash --" and put in "break=bottom" to get to busy box after the error was found, it showed the error "bin/sh: can't access tty; job control turned off"
:confused: 
any and all help will be greatly appreciated

Devon

---

### Post by Physonius on 2007-02-19
I don't know if this helps you, but I have a Dell laptop (Inspiron 8200), single 60 GB HD and had Ubuntu 6.10 running on it, then a security update blasted my system and I got the same message you have one day.

So the solution I discovered was to boot the installation CD, remount HD5 and then I did a apt-get and did a minimal-install.  Upon rebooting the system, everything worked.

---

### Post by merlin3 on 2007-02-24
I am also having the same problem on many different PC's all of which ran Ubuntu 6.06 perfectly. Hardware tried: Sony VaioPGC 4A1M, Homemade Foxconn AMD64 512MB, Homemade AMD semipron, Old compaq PII PC. Sorry I cant remember the hardware details of all these PC's right now. In short I cant get 6.10 to boot or install at all. Very frustrating! Any help highly appreciated.

---

### Post by writeson on 2007-02-26
Hi all,

I was having this problem as well. I just bought a new Gateway machine that I installed a second HD into and wanted to install Ubuntu Edgy onto this second drive. When I booted the install CD it would get to the progress bar then fall back to the can't access tty; job control turned off thing. I thought it might be the CD Rom on the machine as it's a multi-function drive doing DVD-R, DVD-RW, CD, etc. etc. So I plugged an old CD Rom reader/writer into the IDE cable that I had used before and had the exact same problem. Then I tried booting up a Linux Rescue Disk, Puppy Linux and DSL and by looking at what they were complaining about it looked like somewhere in the boot process Ubuntu was losing track of the boot device. 

So I connected the CD-Rom to a USB chassis and booted the Ubuntu CD from there and everthing worked fine! Got the system installed, up and running. However, when I shut down and tried to reboot from the HD, same problem. After scratching my head for awhile I hit 'esc'  to get the Grub menu and edited the boot sequence. In there I noticed that it was trying to boot from sda1, however I had installed the second drive on the second port, so I edited that to sdb1 and booted. Worked fine, booted up. Then I edited the /etc/grub/grub.conf file to make the same change and voila, works every time now. 

Just thought I'd pass this along,
Doug

---

