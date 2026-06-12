---
title: "Install OK, but reboot fails"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by jamisonaw on 2006-06-02
Hi everyone,
This is my first post. 

I am installing EduBuntu server, and the install process worked fine. I got no errors. I've verified the disk, even used it to set up workstations.

When I reboot a very strange thing happens. It goes to Grub, then into the Graphical loader, but when it gets to "Kernel Log" the output to the screen shuts off. My monitor indicator just starts to blink. Hence, I think it is a Video driver. The Vid card is a SiS (I think).

I've tried using the CD to go into rescue mode and editing the xorg.conf file. "sudo gedit /etc/X11/xorg.conf" but it can't open the file (null). I am an admitted novice in the shell.

Thanks for the forum, and ubuntu is wonderfull.

---

### Post by John.Michael.Kane on 2006-06-02
Most likely you will have to use something like sudo nano /etc/X11/xorg.conf

---

### Post by jamisonaw on 2006-06-03
Thanks for your suggestion. I gave it a try, but it gives me an error:

> sudo nano /etc/X11/xorg.conf
sudo: unable to lookup ubuntu via gethostname()

I did another full install, and have the same problem. I've tried logging (without visual) and the hard drive works. Probably loading Nautilus etc. So my guess is that it really is the video card.

How can I get more information about this problem? Is there as wiki?
How can I determine the video card?

---

### Post by mengd2002 on 2006-06-03
I have exactly the same problem with my ATI 9600 Radeon video card.  At this point I'm going back to Breezy and staying there until these issues are resolved.  The old release works much better than the new one.

Don

---

### Post by jamisonaw on 2006-06-04
At this point I'm thinking about doing the same thing, but the new features in Dapper are so tempting. 

Does anyone have any suggestions???

---

### Post by ubuntu_demon on 2006-06-04
the hostname problem :
[http://www.ubuntuforums.org/showpost.php?p=992332&postcount=14](http://www.ubuntuforums.org/showpost.php?p=992332&postcount=14)

in recovery mode also do :
$sudo visudo

and add a line so the end of the file becomes like this :

```

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
*yourusername* ALL=(ALL) ALL

```

---

### Post by ubuntu_demon on 2006-06-06
Did my post help you ?

Did you solve it ? If not try following this guide :
[http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672)
and post any errors you get.

---

