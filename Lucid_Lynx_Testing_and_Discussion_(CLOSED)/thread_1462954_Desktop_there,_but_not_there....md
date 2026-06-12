---
title: "Desktop there, but not there..."
date: 2010-04-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mrpinchy on 2010-04-26
Hi All,

   I downloaded and installed Beta 2 about 2 weeks ago.  about a week ago I said, "self, update manager hasn't come up on its own so I guess I should run it".  I did, and there was about 250 packages to install or update, so I installed them to see what would happen.  Nothing happened other than normal operation.
   I installed Bootchart so I could see my performance.  Everything was going swimmingly, until I rebooted and posted my chart here on the forums.  Right after that I ran the update manager again and blindly installed what was there.  Then I changed things so I would not have to manually login, to increase boot speed.

   Then I tried to reboot...

   I chose the OS to boot up 2.6.32-21 Lucid.
   
   I got to the screen where I choose my profile to log in as, press enter, and off it goes.  I get UBUNTU with the five dots for a few seconds, then my desktop background comes up and I get a few error messages.

#1. Could not update ICEauthority file /home/Joseph/.ICEauthority

#2. /usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256

#3. Nautilis could not create the following required folders /home/Joseph/Desktop,/home/Joseph.nautilis.

   Afterwards my desktop background comes up but there are no menues or Icons.  I can still bring up a terminal from the keyboard.

   I can still get into the Lucid partition from Jaunty, so I don't know if I can repair from Jaunty or the live disk or if I should just wait a few days and re-install.

 [http://img214.imageshack.us/img214/8270/josephlaptoplucid201004.png](http://img214.imageshack.us/img214/8270/josephlaptoplucid201004.png)
   This is the chart that came up.  I don't know if it says anything useful.

Thanks
Joe.

---

### Post by dino99 on 2010-04-26
as i understand your problem, you can boot with lucid and open a console: so from there you can try to clean the system and view logs.

is it a fresh install or a dist-upgrade ? it's better if we know about harware and desktop (gnome ?)

---

### Post by renkinjutsu on 2010-04-26
From the terminal (as user), try ```
chmod 600 .ICEauthority
```
then log back in to see if it fixed your problem

---

### Post by mrpinchy on 2010-04-26
It's a compaq laptop
lucid 64 bit gnome, downloaded from Ubuntu.com as beta 2.  Installed on fresh partition.
amd athlon x2 64
nvidia geforce 8400 I think
250g hdd Jaunty 32bit (working), Lucid 64bit (OS in question)& Vista H.P. 32bit (haven't tried it since)
integrated sound
atheros wireless.

I'm on the road helping the GF look at cars so I won't be able to try any fixes until tonight.

Thanks,
Joe.

---

### Post by dino99 on 2010-04-26
so you might have those packages installed:

- nvidia-current
- nvidia-settings
- nvidia-common
- nvidia-current-modaliases
- nvidia-173
- jockey-gtk

into console: sudo apt-get install "each of them"

then : sudo dpkg --configure -a

after reboot, see if nvidia-current is activated (system admin hardware driver)

if troubles are still there, as lucid dont need xorg.conf by default, you can erase it, sometimes it bring problem ( sudo rm -f /etc/X11/xorg.conf)

---

### Post by sdowney717 on 2010-04-26
[http://forums.fedoraforum.org/showthread.php?t=205035](http://forums.fedoraforum.org/showthread.php?t=205035)

this ought to fix it.
login with a new user that you will need to create from the console window
then follow what he did about changing ownership etc...
or perhaps you can just run this at recovery console window
chown username -R /home/username

gconf sanity check is something in you gnome user configuration is so messed up it is insane
[http://forums.fedoraforum.org/showthread.php?t=208427](http://forums.fedoraforum.org/showthread.php?t=208427)

---

