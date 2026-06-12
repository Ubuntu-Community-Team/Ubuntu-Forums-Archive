---
title: "[SOLVED] Install ubuntu-desktop on server without Internet connection"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by dazed001 on 2007-07-30
I have just installed Ubuntu server 7.04 on a PC without internet connection. The install was done using a Ubuntu Server 7.04 CD. I also have a Ubuntu desktop CD.

After I have installed the server edition, I tried to install the ubuntu-desktop package onto the PC using the desktop CD. However I only receive the message that the ubuntu-desktop package could not be found.

Here are the steps I have taken to install the ubuntu-desktop

1. After logging onto the server, I inserted the ubuntu desktop CD into the CD ROM
2. I entered sudo apt-cdrom add.
3. I wrote down the the source list entry displayed (cdrom:[Ubuntu 7.04 _Feisty ...)
4. I edited the sources.list text file in /etc/apt.
5. I commented out all deb line entries except the line for the ubuntu desktop CD
6. Leaving the desktop cd in the CD ROM, I entered mount /dev/cdrom
7. I entered sudo apt-get update. I received messages indicating that certain tree lists were successfully loaded
8. I entered sudp apt-get install ubuntu-desktop. I received the message, "Couldn'd find the package ubuntu-desktop"

Is it possible to install the desktop software on a Ubuntu server PC without connecting to the Internet?

---

### Post by talby on 2007-07-30
well you could do a "sudo apt-cache show ubuntu-desktop" to show all the dependencies and manually install them all...  Let's see:

```
sudo apt-cache show ubuntu-desktop > /tmp/ubuntu-desktop-meta
grep -i depends: /tmp/ubuntu-desktop-meta|tail -1|sed -e "s/Depends:/sudo apt-get install/g" -e "s/,//g"
```

that should get you the correct command to install all of them manually.

cheers!

---

### Post by aysiu on 2007-07-30
You can't add *ubuntu-desktop* from the Ubuntu Desktop CD, ironically enough. You can either add *ubuntu-desktop* from the Ubuntu Alternate CD **or** install the Ubuntu Desktop CD _over_ your current server installation.

I'll tell you right now, though--server, desktop, whatever... Ubuntu isn't very fun to use without an internet connection, unless you're planning to play hours of tetris.

---

### Post by dazed001 on 2007-08-06
Thanks to aysiu, I was able to install Ubuntu desktop on top of Ubuntu server.
I followed the advice posted and downloaded the iso image for the Ubuntu alternate install CD (7.04)

Here is a list of steps I have taken to install Ubuntu Desktop on top of Ubuntu Server
1. After writing the iso image to a CD, I powered on the PC that ran Ubuntu Server.
2. Once Ubuntu Server is loaded, I logged on with the administrative password.
3. I inserted the alternate install CD into the CD-ROM. At the command prompt I entered
sudo apt-cdrom add
4. I wrote down the deb name of the CD, which is Ubuntu 7.05 _Feisty Fawn ...
5. I checked if this deb entry is listed in the text file, sources.list (found in /etc/apt)
6. To open this text file, I entered "sudo vi /etc/apt/sources.list"
7. After verifying that this deb entry is in the text file, I exited vi
8. I mounted the CD by typing "mount /dev/cdrom"
9. Next, I entered "sudo apt-get update"
10. Then I entered "sudo apt-get install ubuntu-desktop"
11. What follows is the installation of numerous files for the ubuntu desktop.
12. After the desktop is installed (takes about 30 min on Intel P4 with 1 Gb RAM) I entered "startx"
13. I was presented with the Ubuntu desktop, I then configured the network card to connect to the a DHCP router and was subsequently connected to the Internet.
14. I then logged onto the Ubuntu forums and posted this reply
I

---

### Post by piniped on 2007-08-19
Hallelujah! I spent half a day trying to figure out how to install ubuntu-desktop on my server following various forum threads that did not work. I followed the "14 steps" and everything works perfectly. Thank you

---

### Post by shinigami16 on 2008-06-12
> **dazed001 said:**
> Thanks to aysiu, I was able to install Ubuntu desktop on top of Ubuntu server.
I followed the advice posted and downloaded the iso image for the Ubuntu alternate install CD (7.04)

Here is a list of steps I have taken to install Ubuntu Desktop on top of Ubuntu Server
1. After writing the iso image to a CD, I powered on the PC that ran Ubuntu Server.
2. Once Ubuntu Server is loaded, I logged on with the administrative password.
3. I inserted the alternate install CD into the CD-ROM. At the command prompt I entered
sudo apt-cdrom add
4. I wrote down the deb name of the CD, which is Ubuntu 7.05 _Feisty Fawn ...
5. I checked if this deb entry is listed in the text file, sources.list (found in /etc/apt)
6. To open this text file, I entered "sudo vi /etc/apt/sources.list"
7. After verifying that this deb entry is in the text file, I exited vi
8. I mounted the CD by typing "mount /dev/cdrom"
9. Next, I entered "sudo apt-get update"
10. Then I entered "sudo apt-get install ubuntu-desktop"
11. What follows is the installation of numerous files for the ubuntu desktop.
12. After the desktop is installed (takes about 30 min on Intel P4 with 1 Gb RAM) I entered "startx"
13. I was presented with the Ubuntu desktop, I then configured the network card to connect to the a DHCP router and was subsequently connected to the Internet.
14. I then logged onto the Ubuntu forums and posted this reply
I






I can't do that!:( can you tell me that more details. please! or you have a articel to make that!

---

### Post by aysiu on 2008-06-12
> **shinigami16 said:**
> I can't do that!:( can you tell me that more details. please! or you have a articel to make that!
That whole process is too convoluted. All you have to do is log in and then type these commands: ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by shinigami16 on 2008-06-18
> **aysiu said:**
> That whole process is too convoluted. All you have to do is log in and then type these commands: ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```







Thank aysiu,
I know that code can work!
but I don't have internet now!
please....
could you tell me how I can install ubuntu desktop in ubuntu server without internet?

---

### Post by aysiu on 2008-06-18
You need the Ubuntu Alternate CD (*not* the Desktop CD).

Then type ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by shinigami16 on 2008-06-19
> **aysiu said:**
> You need the Ubuntu Alternate CD (*not* the Desktop CD).

Then type ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```




thank aysiu

could you tell me link for ubuntu alternate cd?

---

### Post by aysiu on 2008-06-19
> **shinigami16 said:**
> thank aysiu

could you tell me link for ubuntu alternate cd?
[This](http://ubuntuforums.org/showthread.php?p=5188844#post5188844) should help you.

---

