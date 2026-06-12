---
title: "Unable to Install Ubuntu on Sony Vaio"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by pwn on 2007-09-25
I have a Sony Vaio VGN-AR590E
2GHz Core2 Duo
2GB RAM
1GB GeForce
Blu-Ray Writer
320GB (160GB X 2 RAID0)

When I booted with the Live CD, first I got an error saying "Unable to allocate memory resource", and then 2 seconds later, it showed the Ubuntu loading screen. After that, it said "/bin/sh: can't access tty; job control turned off" and waits for me to type something.

What do I need to do? I have Ubuntu working perfeclty fine on my desktop. But in this case, I'm completely clueless.

---

### Post by Pumalite on 2007-09-25
If using Live CD do try this:

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

Report back with results.

---

### Post by kerry_s on 2007-09-25
i heard it works with the alternate cd

---

### Post by pwn on 2007-09-25
It took me to the command promot. While loading, it said several times that there was an I/O error on sda2

It also couldn't start the graphical X manager. Took me to the command prompt

---

### Post by Pumalite on 2007-09-25
Was this at the end of the install?. If so, then:
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx.

---

### Post by pwn on 2007-09-25
Pumalite, you're a life saver. I've been trying this from the past 15 hours lol.

I'll try installing it and let you know how it went. I hope there won't be any problem with installing cause of the RAID0

---

### Post by Pumalite on 2007-09-25
Ahhh...now you tell me.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by pwn on 2007-09-25
It shows my drives separtely.. What do I do about that? Its a RAID0

---

### Post by pwn on 2007-09-25
Will this destroy my existing Windows Installation?

---

### Post by Pumalite on 2007-09-25
Read my post # 7

---

### Post by pwn on 2007-09-25
I got this after runnning dmraid

ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "isw_dcdfbjhaaa_Volume0" already active
RAID set "isw_dcdfbjhaaa_Volume01" already active
RAID set "isw_dcdfbjhaaa_Volume02" already active
ubuntu@ubuntu:~$ 

Am I all set?

---

### Post by pwn on 2007-09-25
Still shows two drives :|

---

### Post by pwn on 2007-09-25
Okay, just resized the drive from C and left 25GB of unalloted space. Lets see how it goes now.

---

### Post by pwn on 2007-09-26
It said unable to create the ext3 file system

---

### Post by pwn on 2007-09-30
Still haven't been able to install ;[

---

### Post by Pumalite on 2007-09-30
Get rid of your Raid, work with independent drives and install anything you want.

---

### Post by pwn on 2007-10-08
Yeah, I did that as a last resort. I'll try again when Gutsy is out. Hopefully it can install on RAID0.

---

