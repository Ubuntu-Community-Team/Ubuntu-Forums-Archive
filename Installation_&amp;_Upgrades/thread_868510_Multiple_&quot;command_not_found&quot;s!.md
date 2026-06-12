---
title: "Multiple &quot;command not found&quot;s!"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by NekoXandu on 2008-07-23
Hi! *Newbie to the boards!*
Ok, I was probably doing something I wasn't supposed to do, I was trying to install a .rpm file, and I used "alien" via "sudo apt-get install alien" to convert it to .deb and then install it, but afterwards, I noticed that I cant use "sudo", "aptitude", or "apt-get" anymore! They all say "command not found". On top of that, My "Synaptics Package Manager", and "Add/Remove" are gone. I was Googling up some other posts, and saw that some people reinstalled these things, but I have no clue as to how to do this! I also noticed in other posts that some information was posted, so here is mine, besides the fact that I am on Gutsy Gibbon 7.10...

stefan@stefan-laptop:~$ which sudo
/usr/bin/sudo

stefan@stefan-laptop:~$ which apt-get 
(no response)

stefan@stefan-laptop:~$ which aptitude
(no response)

stefan@stefan-laptop:~$ dir
CMakeCache.txt  Examples  location                Pictures  RemoteJoy     wep
CMakeFiles      file:     Music                   PSPDEV    start-compiz
Desktop         foo       nautilus-debug-log.txt  Public    Templates
Documents       LimeWire  palomino                random    Videos

stefan@stefan-laptop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

stefan@stefan-laptop:~$ id
uid=1000(stefan) gid=1000(stefan) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev),1000(stefan)

Also, if you want to know the exact steps I used, here is where I got them from: [http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/]("http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/")

I would really like to avoid having to reinstall the whole OS considering I've had this system dual-booting Vista and Ubuntu since Jan. and I just yesterday figured out how to put CompizFusion/Emerald on it, and play videos...lol

Hopefully this helps, and according to how much you guys have helped me out without me asking a question, I know you guys will come through for me! So thanks in advance!

---

### Post by mikewhatever on 2008-07-24
Try <sudo apt-get install ubuntu-desktop>.

---

### Post by NekoXandu on 2008-07-24
> **mikewhatever said:**
> Try <sudo apt-get install ubuntu-desktop>.

Negative
stefan@stefan-laptop:~$ sudo apt-get install ubuntu-desktop
sudo: apt-get: command not found

---

### Post by zvacet on 2008-07-24
```
gksudo gedit /etc/hosts
```

Look if first two lines look like this

127.0.0.1 localhost
127.0.1.1 hostname

**hostname **= your hostname 

So if these lines doesn´t look that way correct that ans save and close file.Try to use administrative commands ( sudo...).

---

### Post by NekoXandu on 2008-07-24
> **zvacet said:**
> ```
gksudo gedit /etc/hosts
```

Look if first two lines look like this

127.0.0.1 localhost
127.0.1.1 hostname

**hostname **= your hostname 

So if these lines doesn´t look that way correct that ans save and close file.Try to use administrative commands ( sudo...).


Ok, heres what came up in Terminal:
** (gksudo:5914): WARNING **: Invalid borders specified for theme pixmap:
        /home/stefan/.themes/OSX-theme/gtk-2.0/Buttons/button-default.png,
borders don't fit within the image

And Heres what opened at the same time:
127.0.0.1	localhost
127.0.1.1	stefan-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by NekoXandu on 2008-07-28
*Self-Bump* I need help guys!

---

