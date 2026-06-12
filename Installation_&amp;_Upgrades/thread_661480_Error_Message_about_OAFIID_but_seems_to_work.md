---
title: "Error Message about OAFIID but seems to work"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by tmcdlive on 2008-01-07
Keep in mind I am brand new to Linux, Ubuntu, and Gnome...

Loaded above on PC devoted to Linux (no windows involved) about a week or a trifle more ago.

All seems to work ok except for this old monitor's resolution and the following error message that comes up whenever I boot up:

**[INDENT]The panel encountered a problem while loading "OAFIID:deskbar_Applet".[/INDENT]**

Then it asks what I want to do -- delete or ignore

I use the ignore and all seems to work ok but it bugs me that something is wrong.


_Questions:_

[INDENT]A)  What is OAFIID?[/INDENT]
[INDENT]B)  Is there a simple solution?  Or should I just keep ignoring the message?[/INDENT]

---

### Post by bryncoles on 2008-01-09
i'm also a rank n00b (three days and counting)

i got the same error message, after installing klamav (i share with windows machines... just trying to be a courteous neighbour). 

i would also be interested to know what the message means, and what i should do about it....

---

### Post by Acunga on 2008-03-13
The same here:confused:

---

### Post by 888mafia on 2008-03-16
Me too :(

---

### Post by mgbridges on 2008-03-20
I too am getting an error message about OAFIID:Deskbar_Applet every time I boot up. I looked in Launchpad and it seems to suggest it was a bug that has been fixed. However, it's still happening for me.

Any ideas what to do about it?

---

### Post by eugenevdm on 2008-05-14
I run Hardy 8.04 and I have just encountered this error message for the first time. The system has not crashed and Firefox is still open and working fine.

Clicking on Firefox on the shortcut on the bottom panel works and new Firefox windows open, but trying to open anything from the Applications menu (such as Text Editor, Calculator or Evolution) does not work. It just does nothing or open the program and then immediately closes it again.

Overall I am very happy with Hardy 8.04 though. Ubuntu 7.10 crashed on me almost every day but so far I have been able to run Hardy for more than 30 hours, which is a record uptime. I suspect something to do with my motherboard and / or video card caused the major instability before. I use a MSI K9AGM2 motherboard with on-board video. I notice also that when I use 1 GB RAM instead of 512 MB RAM that the system is much more unstable. I will keep you posted.

EDIT:

Just when I though Firefox was OK I closed it and then couldn't open it again at all. I tried logging off.
Then the system went into a crash loop. First it said:

"Greeter application appears to be crashing. Attempting to use another one."

and then repeated messages that I couldn't get out off:

"The display server has been shut down 6 times in the last 90 seconds. waiting for 2 minutes before trying again on display :0"

I was forced to use ALT-F1 to log into another terminal and did a sudo reboot.

---

### Post by eugenevdm on 2008-05-14
Today when I got home the caps lock and scroll lock buttons were flashing. This happens quite often on my system. Normally I just press the reboot button on the front of the PC to get everything working again.

Does anyone know if there are keyboard shortcuts to get out of this situation?

---

### Post by gerben1 on 2008-05-19
I have this problem too now and then, it just seems to be totally random. Ocasionally when i boot up the laptop I get one of those OAFIID messages, usually OAFIID:GNOME_MultiloadApplet, and then all windows do not have a titlebar. It is mostly solved after rebooting.

(and I have reinstalled gnome-applets and gnome-applets-data, but that did not solved it)

---

### Post by helpdeskdan on 2008-05-20
After the most recent security upgrade, (including gnome-panel) I now have this problem.  I can't fix it!  Hardly anybody else is having this problem - what do we do?

---

### Post by helpdeskdan on 2008-05-21
Hey! I believe I got it!  Thanks to an old post:
[http://ubuntuforums.org/archive/index.php/t-25259.html](http://ubuntuforums.org/archive/index.php/t-25259.html)

I tried the instructions on the last post:

sudo /etc/init.d/gdm stop
sudo aptitude reinstall gnome-applets

Not something you want to mess around with if you're a newbie.  Luckily, I knew enough about linux to understand the virtual consoles, so I hit ctl-alt f2 to get me to a login screen.  However, when I went to reinstall, gnome-applets wasn't installed.  How that got uninstalled, I have no idea!  (Miro might have had something to do with it)  I installed the applet and then did a sudo /etc/init.d/gdm start, and all my missing applets came back with no error messages!  I bet a simple sudo apt-get install gnome-applets combined with a reboot would have had the same effect.

---

### Post by eugenevdm on 2008-05-21
> **eugenevdm said:**
> I run Hardy 8.04 and I have just encountered this error message for the first time.

When I had this problem the system prompted me to report the issue. I did so. Since then I have never had this problem again. My system is still freezing every day but I suspect it's a different problem altogether and I will start a separate post for it.

---

### Post by MBdocotr on 2008-05-21
Original New and Used Mercedes Electronics Parts. Mercedes TV tuner, Head Unit, Comand (Command), CD changer, Passenger Mercedes rear screen, Mercedes remote control, Voice recognition, Audio Gateway, DVD player, Prologic, APS, W211, S and E class comand HU with MP3, DVD, RDS, Dolby digital, Dolby 5.1, Dolby surround, Harness, I-Pod, CarPC, Retrofit. For additional information, order or technical support call 212.660.2905 or 213.291.0192 
For the partner programm and cooperation, contact [email]partner@mbdoctor.com[/email], installers from all countrys needed. 

PHONE KIT BLUETOOTH

S H O P                G A L L E R Y

Click for 

Online shopping       Gallery     Installation

Original New and Used Mercedes Electronics Parts. Mercedes TV tuner, Head Unit, Comand (Command), CD changer, Passenger Mercedes rear screen, Mercedes remote control, Voice recognition, Audio Gateway, DVD player, Prologic, APS, W211, S and E class comand HU with MP3, DVD, RDS, Dolby digital, Dolby 5.1, Dolby surround, Harness, I-Pod, CarPC, Retrofit

for additional information, order or technical support call 212.660.2905 or 213.291.0192

 

MBdoctor is not affiliated with Mercedes Benz, Mercedes-Benz AG, Mercedes-Benz USA, or Daimler Chrysler. MBdoctor's website and it's contents, are not endorsed or affiliated with Mercedes-Benz AG, Mercedes-Benz USA, or Daimler Chrysler, Nothing in this website is endorsed or affiliated with Mercedes-Benz AG, Mercedes-Benz USA or any of it's dealerships. 

 MBdoctor  2003 (c)


[http://mbdoctor.com/](http://mbdoctor.com/)

[http://mbdoctor.com/installation.html](http://mbdoctor.com/installation.html)

[http://mbdoctor.com/shop/index.php?manufacturers_id=10](http://mbdoctor.com/shop/index.php?manufacturers_id=10)

[http://www.mbdoctor.com/gallery/main.php](http://www.mbdoctor.com/gallery/main.php)

Affordable Web Hosting

Copyright © 2003 MBdoctor Inc. All rights reserved.
212.660.2905 or 213.291.0192




Thank you for shopping with us!!

---

