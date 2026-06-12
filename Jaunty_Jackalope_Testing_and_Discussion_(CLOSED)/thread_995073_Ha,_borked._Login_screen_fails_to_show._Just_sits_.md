---
title: "Ha, borked. Login screen fails to show. Just sits there with animated pointer going."
date: 2008-11-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-11-27
Can get to a shell with ctrl F1. Tried recovery and xfix, gdm is already running. 

Anything to try?

---

### Post by autocrosser on 2008-11-27
Good question--I just updated & have the same thing--back to my one week-backdated Jaunty install & waiting..................

---

### Post by lonniehenry on 2008-11-27
Same here. I can use jaunty because my cairo-dock work, compiz is running - have wireless, rotating cube, just no gnome panels.

---

### Post by Eclipse. on 2008-11-27
Anybody know what package is at fault?

---

### Post by plun on 2008-11-27
Nope not exactly but these packages broke

The following packages will be REMOVED:
  deskbar-applet gedit gnome-games gnome-orca libdeskbar-tracker
  python-gnome2-desktop python-gnome2-extras python-gtksourceview2

A new gnome-desktop is also coming along.

[https://lists.ubuntu.com/archives/jaunty-changes/2008-November/thread.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-November/thread.html)

Doing nothing for the moment..


ssh or putty from another PC is one solution....:)

EDIT

Or chroot

Or remove splash from boot, chris poulsson and I did some exercise on the tty error and nosplash works.

---

### Post by Knorr on 2008-11-27
Oh I just love these situations. ;)

I somehow got to "semi" login. Probably by enabling autologin in /etc/gdm/gdm.conf. But it doesn't seems like the gnome session is started. The only thing that was visible was pidgin (I have a script starting pidgin at login). I got this browser open by writing someone an url and clicking on it.

There are no menus around, and Alt+F2 doesn't work.
I have seen some lines in my auth.log file.

pam_nologin(gdm:auth): cannot determine user

Don't know if that's related to this bug or not.

---

### Post by ronacc on 2008-11-27
I updated this AM and all was ok after reboot , I just updated again and this time got breakage , haven't rebooted yet but already nautilus and terminal will not start from desktop icons , pannels are ok so far and some progs still start from destop icons , synaptic shows nothing as broken . looks like something updated that should have been held back for awhile yet .

---

### Post by plun on 2008-11-27
A new GTK version is also coming

Apps breaks for me now

```
rhythmbox: error while loading shared libraries: libgailutil.so.18: cannot open shared object file: No such file or directory

```

Just to wait for GTK and gnome-desktop and install ubuntu-desktop  :)

---

### Post by autocrosser on 2008-11-27
Waiting---I broke both my Jaunty installs :( , so waiting in my Hardy backup with both chroot scripts warm & idling........

---

### Post by marijus on 2008-11-27
a dist-upgrade made my box working again :)
good luck!

---

### Post by plun on 2008-11-27
> **autocrosser said:**
> Waiting---I broke both my Jaunty installs :( , so waiting in my Hardy backup with both chroot scripts warm & idling........

Well... kernel install was also broken.

This chroot manual works... did it last week.

[http://ubuntuforums.org/showthread.php?t=306424](http://ubuntuforums.org/showthread.php?t=306424)

I also needed the last advice about resolv.conf

> Before chrooting:

To correct this, before the chroot we have to enter:
```
sudo cp /etc/resolv.conf /media/hardy/etc/resolv.conf
``` 


hardy > jaunty...

I am not going to log out...:)

---

### Post by ShirishAg75 on 2008-11-27
> **plun said:**
> A new GTK version is also coming

Apps breaks for me now

```
rhythmbox: error while loading shared libraries: libgailutil.so.18: cannot open shared object file: No such file or directory

```Just to wait for GTK and gnome-desktop and install ubuntu-desktop  :)

Same here 

```
$ brasero
brasero: error while loading shared libraries: libgailutil.so.18: cannot open shared object file: No such file or directory

```

I am also not going to logout till electricity fails me or some disaster like that. And updates every 6 hours or so.

---

### Post by philinux on 2008-11-27
From ctrl F1 I did a update then dist-upgrade 

Then update upgrade

ctrl F7 and Login screen appeared. Ha. Dont you just love alpha testing.

Wait a minute as I type more updates!!!

---

### Post by Naddiseo on 2008-11-27
> **plun said:**
> A new GTK version is also coming

Apps breaks for me now

```
rhythmbox: error while loading shared libraries: libgailutil.so.18: cannot open shared object file: No such file or directory

```

Just to wait for GTK and gnome-desktop and install ubuntu-desktop  :)

Me too, do you know if it's been bugged yet?

---

### Post by plun on 2008-11-27
> **Naddiseo said:**
> Me too, do you know if it's been bugged yet?

New GTK is out.... testing..

(32 bit at least)

---

### Post by gjoellee on 2008-11-27
first issues with Jaunty is coming!

---

### Post by plun on 2008-11-27
Breakage fixed for me....

Canberra is still broken, probably needs a rebuild.


(also took the new kernel with me but its a sound mess...)

---

### Post by Ewingo401 on 2008-11-27
> **plun said:**
> Breakage fixed for me....

Canberra is still broken, probably needs a rebuild.


(also took the new kernel with me but its a sound mess...)

How did you fix it?

---

### Post by philinux on 2008-11-27
I uninstalled, rightly or wrongly, libcanberra-gnome. Then let gnome-session-canberrra get updated.

---

### Post by gjoellee on 2008-11-27
> **philinux said:**
> I uninstalled, rightly or wrongly, libcanberra-gnome. Then let gnome-session-canberrra get updated.

I was about to tell that ! :)

---

### Post by plun on 2008-11-27
> **Ewingo401 said:**
> How did you fix it?

I was logged in all the time and saw the breakage.

It depends where you are.

Probably easiest is to change boot to nosplash  >  Ctrl-Alt-F1 at login screen

Log in within tty

```
sudo apt-get update && sudo apt-get dist-upgrade

sudo apt-get install -f

sudo apt-get install ubuntu-desktop
```

---

### Post by Ewingo401 on 2008-11-27
Weird, that didn't work for me.  Oh well, I'm just running in a virtual machine for testing purposes, no biggie if its borked lol.

---

### Post by gjoellee on 2008-11-27
For you who wonder, this "bug" dit not show on people doing a ```
update-manager -d
``` upgrade from an earlier version.

---

### Post by plun on 2008-11-27
> **philinux said:**
> I uninstalled, rightly or wrongly, libcanberra-gnome. Then let gnome-session-canberrra get updated.

```
plun@plun:~$ **sudo dpkg -i --force-overwrite /var/cache/apt/archives/gnome-session-canberra_0.10-1ubuntu2_all.deb**

(Reading database ... 175636 files and directories currently installed.)
Unpacking gnome-session-canberra (from .../gnome-session-canberra_0.10-1ubuntu2_all.deb) ...
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/gnome/autostart/libcanberra-login-sound.desktop', which is also in package libcanberra-gnome
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/gnome/shutdown/libcanberra-logout-sound.sh', which is also in package libcanberra-gnome
Setting up gnome-session-canberra (0.10-1ubuntu2) ...
```


My solution...  Ubuntu-desktop is still there...:)

---

### Post by ronacc on 2008-11-27
seeing the problems people were reporting I did not reboot after the update I did 3 hrs ago , then seeing that things seem to be better I updated and dist-upgraded  , removed splash from the bootline and rebooted , all seems ok (except the front speaker still muted after boot).

---

### Post by autocrosser on 2008-11-27
I got back in after doing a dist-upgrade thru my chroot script---My backup install is still borked---but the main is going---Hey plun--my chroot script looks like----

#!/bin/bash
sudo mount --bind /dev /mnt/JJbackup/dev
sudo mount --bind /proc /mnt/JJbackup/proc
sudo mount --bind /sys /mnt/JJbackup/sys
sudo cp /etc/resolv.conf /mnt/JJbackup/etc/resolv.conf
sudo chroot /mnt/JJbackup su

Gota run--Thanksgiving Dinner---talk in a couple of hours---

---

### Post by forumache on 2008-11-27
> **gjoellee said:**
> For you who wonder, this "bug" dit not show on people doing a ```
update-manager -d
``` upgrade from an earlier version.

I am the exception to your rule :)

I've just joined Jaunty, from up to date Intrepid, and after reboot I was not able to login. Also not able to Ctrl-Alt-F1.

I rebooted in recovery mode, root with net, plugged in the network cable (wifi didn't work in text mode), update, upgrade, solved the problem with canberra (by uninstalling libgnome-canberra and let gnome-session-canberra to be pulled in) and now I'm fired up and ready to go.

---

### Post by plun on 2008-11-27
> **autocrosser said:**
> 
Gota run--Thanksgiving Dinner---talk in a couple of hours---

Aha... its holiday in US...  have a really nice dinner !! :)

---

### Post by Ewingo401 on 2008-11-27
> **plun said:**
> ```
plun@plun:~$ **sudo dpkg -i --force-overwrite /var/cache/apt/archives/gnome-session-canberra_0.10-1ubuntu2_all.deb**

(Reading database ... 175636 files and directories currently installed.)
Unpacking gnome-session-canberra (from .../gnome-session-canberra_0.10-1ubuntu2_all.deb) ...
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/gnome/autostart/libcanberra-login-sound.desktop', which is also in package libcanberra-gnome
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/gnome/shutdown/libcanberra-logout-sound.sh', which is also in package libcanberra-gnome
Setting up gnome-session-canberra (0.10-1ubuntu2) ...
```


My solution...  Ubuntu-desktop is still there...:)

This worked for me thanks.

---

### Post by philinux on 2008-11-27
So did i make a boo boo uninstalling libcanberra-gnome

---

### Post by cariboo on 2008-11-27
Yes you did. I did the same thing this morning and ended up with the so called brown screen of death.

This afternoon I purged libcanberra, which also removed the ubuntu desktop, then did the updates  and reinstalled Ubuntu desktop and now everything that worked before works again. This was all done at the new netprompt selected from the recovery menu.

edit: oops misread the previous post, you did good. :)

Jim

---

### Post by dinxter on 2008-11-27
was this gtk? xfce4 went down with gnome so i thought thats what it was. seemed to be the upgrade to 2.14.5-1ubuntu1 that fixed this for me. always nice to see a proper breakage anyway and made me try out kde for the first time in a while, looked good!

---

### Post by autocrosser on 2008-11-27
Thank you my friend!!! had a good one w/wife & parents--had to "fix" my step-fathers Windozs XP unit--very nice to get back to Linux!!!!

I had manually removed the libcanberra-gnome     info from /var/lib/dpkg to get things "unstuck"--didn't un-install it, but apt thought it was ;) --I'll -force-overwrite the backup jaunty install to get it fixed--nice easy breakage to keep us on our toes:lolflag:

I've got til Monday to go back to work, so I might muck around with EXT4 this weekend......should keep life "interesting"

Cheers!!!!

> **plun said:**
> Aha... its holiday in US...  have a really nice dinner !! :)

---

### Post by ronacc on 2008-11-27
probably did have something to do with gtk , nautilus and gnome terminal wouldn't run for me but yakuake would .thats how I was able to wait for things to get sorted before I rebooted.

---

### Post by namd3r on 2008-11-28
So, Jaunty has been my first effort at installing an ubuntu alpha, and I have this happening to me when I start up, with no clue as to how to fix it.

A couple of things that are keeping me from fixing it are a) I upgraded from the update manager, so I have no copy of the cd, and b) the network that I am connected to has a login to monitor internet traffic, so if I am not already logged in through a browser, the updates to my system always fail because the packages get hit with a 302 redirect to the login page.

Would I have to download a cd version to fix the problem?

---

### Post by Starks on 2008-11-28
This happens to me when resuming from standby.

---

### Post by klim8 on 2008-11-28
> **ronacc said:**
> probably did have something to do with gtk , nautilus and gnome terminal wouldn't run for me but yakuake would .thats how I was able to wait for things to get sorted before I rebooted.

The problem was libgtk2 not depending on libgail so libgailutil.so.18 was missing. The latest libgtk2 upload fixes this.

---

### Post by ShirishAg75 on 2008-11-28
> **autocrosser said:**
> Thank you my friend!!! had a good one w/wife & parents--had to &quot;fix&quot; my step-fathers Windozs XP unit--very nice to get back to Linux!!!!

I had manually removed the libcanberra-gnome     info from /var/lib/dpkg to get things &quot;unstuck&quot;--didn't un-install it, but apt thought it was ;) --I'll -force-overwrite the backup jaunty install to get it fixed--nice easy breakage to keep us on our toes:lolflag:

I've got til Monday to go back to work, so I might muck around with EXT4 this weekend......should keep life &quot;interesting&quot;

Cheers!!!!

Right. This seems to be the only way forward. I hope they do fix libcanberra. We need system sounds back again :)

---

### Post by autocrosser on 2008-11-28
YES--not fun without system sounds--I had setup a custom soundset from stuff off of gnomelook.org & really liked the my login/out/action sounds--but a working Jaunty is better than no Jaunty at all :)

---

