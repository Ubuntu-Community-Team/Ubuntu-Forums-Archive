---
title: "Gnome session startup programs hang Gnome login"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by billstei on 2008-10-24
After having upgraded to Intrepid RC, Gnome was hanging right after the login, and the solution was to switch to a Fail Safe Gnome session, and then go to System->Preferences->Sessions->Startup Programs, and uncheck some startup programs.  I have a lot of the KDE stuff installed and ended up with several double entries, 2 Print Queue Applets, 2 Update Notifiers (Adept and the Gnome one), etc. from the upgrade.  As to what exactly caused the hang I don't know, but it might be good advice to turn off as many custom startup items as possible before doing a Hardy to Intrepid upgrade.

Bill

---

### Post by whtvr on 2008-10-25
Hi there,

I'm glad I found your thread cause I have exactly the same problem. I installed Intrepid RC a while ago on my Thinkpad X30 and after reboot when I get to GDM login screen very fist time, put in my username/password, for a while Gnome looks like it's starting and then it just stops. I can move cursor on the screen but there's no panels or icons or anything else for that matter. Ctrl+Fx, Ctrl+Alt+Backspace or any other key combinations don't work either and I can only hard reset the whole machine.

I tried to follow your solution but the same thing happens when I select Gnome failsafe. Also, I had the same behaviour on Intrepid Beta (don't remember which one... ).

Does anybody have an idea how to fix that?

---

### Post by gary_emms on 2008-10-25
> **whtvr said:**
> Hi there,

I'm glad I found your thread cause I have exactly the same problem. I installed Intrepid RC a while ago on my Thinkpad X30 and after reboot when I get to GDM login screen very fist time, put in my username/password, for a while Gnome looks like it's starting and then it just stops. I can move cursor on the screen but there's no panels or icons or anything else for that matter. Ctrl+Fx, Ctrl+Alt+Backspace or any other key combinations don't work either and I can only hard reset the whole machine.

I tried to follow your solution but the same thing happens when I select Gnome failsafe. Also, I had the same behaviour on Intrepid Beta (don't remember which one... ).

Does anybody have an idea how to fix that?


Same problem, as from the last upgrade - after the login I get a dark screen and the Gnome 'welcome sound' plays. I can kill gnome with a keypress (<ctr> + esc) which drops me to a text log-in as it can't find an image.

I can boot into xfce and KDE4 so it must be a problem with Gnome. 
Two other points:
In Xfce I get a message saying that Gnome Power manager is incorrectly configured and
Firefox won't loan in KDE (these both happened at the same time.
Gaz

I've just checked and the key press is <ctr>+<lt>+F1, sorry, and the fault also occurs in Gnome-failsafe.

---

### Post by Valeryan_24 on 2008-10-25
Hello,

I'm exactly in the same case.

I was still on Intrepid beta, all worked fine, but after the last update of yesterday, going on RC, at reboot all was normal until login, but after just a blank screen, with only the mouse cursor...

The only thing which works is Ctrl Alt F1, logging in a terminal, I can see my files with "ls" command, so I should be able to make modifications or boot on a Live CD to repair this problem if a solution is found.

I have this message written in the console : "kinit, no resume image, doing normal boot".

And I also had a bug before on Gnome Power manager update, it didn't start anymore.

On Ctrl Alt F1 console, as described here in bug report :

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/279450](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/279450)

I removed (sudo rm -rf) in /home the config folders
.gnome .gnome2 .gconf .gconfd .metacity
I restart GDM, selected "new Gnome session", then I get my own customized wallpaper, the welcome sound, a message telling that Gnome Power Manager is not correctly installed and... that's all : desktop and screen remain empty, no icon, no table board, no menu, no files, only the mouse cursor again !

:confused:

Same thing on Gnome failsafe.

Please, does someone have a solution to fix it ? I can reinstall, my /home is on a separate partition, but I'd like not to re-do some modifications again.

Thanks ! :)

---

### Post by Valeryan_24 on 2008-10-25
In console mode, it is also written "desktop tty1"

I tired a "sudo apt-get upgrade" :

Some errors occurred during execution (I translate from french)

/var/cache/apt/archives/gnome-session_2.24.1-0ubuntu1_i386.deb
/var/cache/apt/archives/gnome-applets_2.24.1-0ubuntu1_i386.deb
/var/cache/apt/archives/fast-user-switch-applet_2.24.0-0ubuntu6_i386.deb
/var/cache/apt/archives/gnome-power-manager_2.24.0-0ubuntu8_i386.deb
/var/cache/apt/archives/nautilus-data_1%3a2.24.1-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I did again sudo apt-get upgrade and got those errors :

g++-4.3 ; gcc-4.3 ; libgcc1 ; libstdc++6 ; libstdc++6-4.3-dev : Depend on gcc-4.3-base (= 4.3.2-1ubuntu10) but 4.3.2-1ubuntu11 is installed
E: Missing dependancies. Try to use option -f.

I did so and :

dpkg : error during cleaning : sub-process post-removal script returned  erreur de sortie d'etat 1
Traitement des "declenchements (triggers)" pour "man-db"...
Some errors occurred during execution
/var/cache/apt/archives/gnome-session_2.24.1-0ubuntu1_i386.deb
/var/cache/apt/archives/gnome-applets_2.24.1-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Here am I for the moment...

---

### Post by billstei on 2008-10-26
From what I can tell... the startup launchers that Gnome runs are located in ~/.config/autostart and removing a launcher from there will in fact keep it from running, however the presence of a launcher there does not mean it will run necessarily, as some of the launchers I see there are unchecked in gnome-session-properties (aka System->Preferences->Sessions->Startup Programs).  So I assume this is still being scripted from somewhere else...

No doubt there exists a Gnome User's Guide, but is there a Gnome Under-The-Hood Hot Rodders Guide (or a similar Ubuntu Under-The-Hood Hot Rodders Guide) ?

Bill

---

### Post by whtvr on 2008-10-27
> **billstei said:**
> From what I can tell... the startup launchers that Gnome runs are located in ~/.config/autostart and removing a launcher from there will in fact keep it from running, however the presence of a launcher there does not mean it will run necessarily, as some of the launchers I see there are unchecked in gnome-session-properties (aka System->Preferences->Sessions->Startup Programs).  So I assume this is still being scripted from somewhere else...
Bill

so you think that it's a service or program that Gnome's trying to run on startup that fails to launch properly and prevents the whole environment from loading... ? there must be a way around it then

---

