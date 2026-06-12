---
title: "Hotkey-Setup issue (Jaunty)"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Aye Up on 2009-04-06
I have an Advent 4211, moreover I came to install some distro upgrades for the beta and all seemed to go fine except for the above titled package,  I have ran all varying modes of commands to remove the package such as autoclean/autoremove and also the deb orphan commands.

It seems the package is broken however when I try to remove it I get the following...

```
sudo apt-get autoremove
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up hotkey-setup (0.1-23ubuntu10) ...
/etc/init.d/hotkey-setup: 47: Syntax error: ";;" unexpected (expecting "fi")
invoke-rc.d: initscript hotkey-setup, action "start" failed.
dpkg: error processing hotkey-setup (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 hotkey-setup
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Likewise if I was to use deborphan:

```
sudo apt-get --purge remove `deborphan` && sudo apt-get autoremove
deborphan: The status file is in an improper state.
One or more packages are marked as half-installed, half-configured,
unpacked, triggers-awaited or triggers-pending. Exiting.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up hotkey-setup (0.1-23ubuntu10) ...
/etc/init.d/hotkey-setup: 47: Syntax error: ";;" unexpected (expecting "fi")
invoke-rc.d: initscript hotkey-setup, action "start" failed.
dpkg: error processing hotkey-setup (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 hotkey-setup
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Please forgive me if I am not being clear, I am not an advanced linux user, so most things like this don't come natural to me.

All I really want to know is how to remove the package forcibly is possible.

Any suggestions?

TIA

---

### Post by sephiroth_4 on 2009-04-06
dbl post:guitar:

---

### Post by sephiroth_4 on 2009-04-06
I'm getting the same after today updates.  The "Community" will fix it later.
or

dalinuxlova wrote on 2007-04-15: (permalink)

@grendelkhan :

this helped, thanks

DON'T REBOOT!:
sudo chmod 444 /etc/init.d/hotkey-setup
then sudo /etc/init.d/hotkey-setup stop

(if you can't open up another gnome-terminal / have closed gnome-terminal & gnome-panel crashed, just switch to tty2:
ctrl + alt + f2, then login and do the above steps)

for restarting / reviving gnome-panel:
killall gnome-panel

then switch back to X:
ctrl + alt + f7

open up a new gnome-panel (alt + f2 -> gnome-panel)
sudo apt-get dist-upgrade

now update should continue

---

### Post by balaknair on 2009-04-06
The hotkey bug has been fixed

Try this:
Press Alt+F2 ----> gksudo gedit /etc/init.d/hotkey-setup
Enter password when asked
This opens the file in a text editor
Find the part which says
```
# This entire block does nothing on desktops right now
     if laptop-detect; then

    do_video

    ;;
     restart|force-reload)
     $0 stop || true
     $0 start
```

Replace it with
```
# This entire block does nothing on desktops right now
     if laptop-detect; then
	    do_video;
    fi;
 

	;;
     restart|force-reload)
     $0 stop || true
     $0 start
```

Save and close the document.
Now run the update manager

---

