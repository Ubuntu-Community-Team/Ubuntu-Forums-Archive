---
title: "The fun of making things work"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by Muskiet on 2010-02-10
This week has been interesting, I have finally thrown Windows XP out the door and installed Ubuntu.
I have no previous knowledge of Linux therefore over the past three days I have figured a lot out through "googeling" while alienating the family, and still some stuff baffles me:

1. The password.
I understand that in an office environment or any other place where other people can get access there is a need for a password, but it drives me insane that I have to constantly use my password to install and/or modify anything on a computer that only I use.
Of course there is a need for security, but I'd like to have unlimited access to my own computer, which brings me to why I can't get the same sort of access the root user can.
I have followed many tips and tricks on how to eliminate the password thing using "sudo visudo" in the terminal, but none of them seem to work so far.

2. Getting my harddisk to work.
When my backup harddisk was still NTFS I've copied all my backup files to my main ext4 harddisk, and then I've formatted it to ext4 as well.
I managed to get the harddisk a label and mount it, but it wouldn't let me do anything to it.
It wouldn't let me make directories for instance and I really wanted it to be simply part of the system in stead of a separate part which I had to mount manually every time.
I followed some directions here: [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) and now I can't even get the thing mounted.
It tells me that "only root can mount /dev/sdb1 on /media/downloads".

Could somebody please let me know what I'm doing wrong?

---

### Post by pastalavista on 2010-02-10
An easy way to set your drives to mount the way you want is pysdm storage device manager. ```
sudo apt-get install pysdm
``` open "Storage Device Manager" in System--> Administration menu

To understand password security / superuser methods check here:

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Muskiet on 2010-02-10
Thank you very much, that helped me getting my harddisk to work like it should.
Don't get me wrong, I love Ubuntu so far, but simple things like getting access to my own harddisk should have been made easier.
I also need to be in the terminal a lot to change settings or install thing making me feel like I'm working from DOS to make my Windows work.

---

### Post by arpanaut on 2010-02-10
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Maybe you need to rethink your approach to Linux...

---

### Post by pastalavista on 2010-02-10
> **Muskiet said:**
> Thank you very much, that helped me getting my harddisk to work like it should.
Don't get me wrong, I love Ubuntu so far, but simple things like getting access to my own harddisk should have been made easier.
I also need to be in the terminal a lot to change settings or install thing making me feel like I'm working from DOS to make my Windows work.
As you learn more about how Linux works, you'll see that you have much more freedom to change and perfect your system. It will get easier when you know what to do. You can decide for yourself which things to do automatically on the user level. If a user application is granted administrative powers, security is gone. With Ubuntu, a "root user" isn't even allowed.

---

