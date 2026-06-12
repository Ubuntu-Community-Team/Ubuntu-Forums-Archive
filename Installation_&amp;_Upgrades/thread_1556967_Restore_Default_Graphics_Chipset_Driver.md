---
title: "Restore Default Graphics Chipset Driver"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by kScream on 2010-08-20
I have a problem with my graphics. When i installed ubuntu lucid lynx a few days ago it installed all the drivers and everything perfectly. Now I have gone and messed up the graphics whilst trying to get cod4 to work through wine and installing an nvidia utility suggested by someone. cod4 didn't work and all I want now is get the graphics back to how it was. Any help would be greatly appreciated.

---

### Post by davidmohammed on 2010-08-20
its a little difficult to diagnose this without knowing what you tried to install and how you did it.

Assuming you tried to install the nvidia graphics driver you could try the following

sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

then reboot

If it wasnt nvidia - 

please let us know what chip

lspci | grep VGA

---

### Post by kScream on 2010-08-20
Yep that was it! thank you so much for your help.

---

### Post by Khufucius on 2011-03-09
> **davidmohammed said:**
> 

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

then reboot



Thanks so much, this solved a similar problem I was having.  In my case, I'd just installed a proprietary graphics driver, and when I rebooted, my screen went to sleep -- as if there were no video input.

Switching to a different tty (ctrl-alt-f1 through ctrl-alt-f6) made the screen wake up and allowed me to log in (command-line only).

Then, renaming the xorg.conf file as per your instructions did the trick -- after a reboot, I was able to use TTY7/x11 again.  Thanks!

-Khufu

---

### Post by brunolopes446 on 2012-02-23
> **davidmohammed said:**
> its a little difficult to diagnose this without knowing what you tried to install and how you did it.

Assuming you tried to install the nvidia graphics driver you could try the following

sudo apt-get purge nvidia*
[B][U]sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
[/U][/B]
then reboot

If it wasnt nvidia - 

please let us know what chip

lspci | grep VGA
restoring the xorg.conf file with this command was the solution for a problem I had. you should spread this command. 
my problem was related to graphic drivers, too. I downloaded the newest and recommended drivers from nvidia's website, installed it correctly, and then I couldn't boot. After trying a lot of stuff, this is one saved me :)

---

### Post by oldos2er on 2012-02-23
Closed, necromancy.

---

