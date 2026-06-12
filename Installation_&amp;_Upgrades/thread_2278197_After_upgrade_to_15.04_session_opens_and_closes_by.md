---
title: "After upgrade to 15.04 session opens and closes by itself after some seconds"
date: 2015-05-14
forum: Installation &amp; Upgrades
---

### Post by jpegubuntu on 2015-05-14
Hi all,

I have a Sony Vaio laptop that runs Ubuntu for a long time but after upgrading to 14.10 I could not open any session.
I could see the desktop background and the mouse but nothing else (same with live boot on a USB drive with 14.10).
I tried many things but finally I reinstalled 14.04 from a USB drive and everything worked fine again.

I then tried to run 15.04 from a USB drive and it worked fine. So I decided to run the 2 upgrades one after the other, first from 14.04 to 14.10 and then to 15.04.
At the first reboot after the upgrade to 15.04, I see the 3 sessions as before but when I try to login on any of the sessions, I see the background, the mouse, sometimes some apport pop ups and then the session closes by itself, I see a black screen with some messages like:
```

ACPI PCC probe failed
starting version 219
started tool to automatically collect and submit kernel crash signature
failed to start lsb: start jetty

```
Then it comes back to the logging screen.

I have tried many things with tty1 (see below).

I think it might be related to my Video card so here is the output:
```
:~$ lspci -vnn | egrep 'VGA|3D'
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Park [Mobility Radeon HD 5430/5450/5470] [1002:68e0] (prog-if 00 [VGA controller])
```


Some things I have tried:

```
sudo apt-get purge jetty
```
It worked (1 package removed) but my problem is still present.

```
:~$ sudo service lightdm start
:~$ sudo service lightdm stop
:~$ dconf reset -f /org/compiz/
error: Cannot autolaunch D-Bus without X11 $DISPLAY
```

```
:~$ sudo apt-get install gnome-panel
:~$ sudo mv ~/.Xauthority ~/.Xauthority.backup
:~$ sudo reboot
```

```
:~$ sudo apt-get install compizconfig-settings-manager
:~$ export DISPLAY=:0
:~$ dconf reset -f /org/compiz/
error: Erreur lors de la génération de la ligne de commande " dbus-launch --autolaunch=d6df58f931a1d5be8781949754ce639c --binary-syntax --close-stderr " : le processus fils s'est terminé avec le code 1
:~$ sudo ccsm
Invalid MIT-MAGIC-COOKIE-1 KEY/...
```
(It goes on here with a lot of stuff that I did not copy)

```
:~$ setsid unity
WARNING: no display variable set, setting it to :0
stop: Name "com.ubuntu.Upstart" does not exist
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: starting plugin: core
start: Name "com.ubuntu.Upstart" does not exist
compiz (core) - Fatal: Couldn't open display :0
compiz (core) - Info: Stopping plugin: core
compiz (core) - Info: Unloading plugin: core
```
(I manually stopped with CTRL+C since it was not ending after a long time)

After all these trials and since I understand less and less what I am doing and what I am reading in the forums I need your help. I do not want to reinstall 14.04 forever on this laptop.


Thanks a lot!

---

### Post by jpegubuntu on 2015-05-14
News: I installed Kubuntu
```
sudo apt-get install kubuntu-desktop
```
I selected "sddm" as default display manager.

After a reboot I now have a different logging screen (kubuntu).
I also have several choices on the logging screen:
[LIST=1]
[*]            Gnome Flashback (Metacity)
[LIST=1]
[*]                It works ! But with a KDE desktop ! But at least my session can open and I can launch applications.
[/LIST]

[*]            Gnome Flashback (Compiz)
[LIST=1]
[*]                brings me quickly back to the logging screen
[/LIST]
[/LIST]

I am still trying to get ubuntu work properly so any help is appreciated.

---

### Post by jhecn on 2015-05-29
Today I tried this
```
sudo apt-get remove kubuntu-desktop
```

---

### Post by jhecn on 2015-06-12
By the way, I had a merge of my 2 forum accounts so in fact I am the OP.

Here is the complete list of actions I did so that I remember and also even if some actions did not work, maybe it's a combination of several changes that made my system work again.

install gdm
default dm : lightdm
first start: mouse and black screen : CTRL+ALT+F1 does not answer => hard reboot
second start: mouse and black screen (after a short display of the kubuntu logo) : CTRL+ALT+F1 does not answer => hard reboot
third start (in recovery mode) switch to root console / dpkg-reconfigure sddm => DM by default is sddm
sudo reboot
- login screen is displayed
-- metacity : login OK but with an "internal error occured window" / 
-- compiz : login loop
dpkg-reconfigure gdm => DM by default is gdm
- the login screen seems to be displayed but pixels are messed up so that I can not read anything, the pixels change when I move the mouse on some of them or when I hight up and down arrows
-- I tried to enter my password but then no answer and even CTRL+ALT+F1 does not answer => hard reboot
- boot in recovery mode, switch to root console
--dpkg-reconfigure gdm => DM by default is sddm
--- impossible to delete /etc/X11/default-display-manager : it is read only
-- dpkg-reconfigure gdm => DM by default is sddm
--- impossible to move /etc/X11/default-display-manager to /etc/X11/default-display-manager.dpkg-tmp: it is read only
-- sudo reboot
--- the reboot succeeded but I saw shortly the message "impossible to get authority"
- the login screen seems to be displayed but pixels are messed up so that I can not read anything, the pixels change when I move the mouse on some of them or when I hight up and down arrows
-- I tried to enter my password but then no answer and even CTRL+ALT+F1 does not answer => hard reboot
- reboot on 3.19 upstart
-- login screen properly displayed (seems to be gdm since I never saw this login screen)
-- I can login but then I see an empty desktop with only the mouse
-- in tty1: ls -lah 
--- 2 files where displaying "root root" (.gvfs and another) but neither /.Xauthority nor /.ICEauthority
-- sudo reboot
-- dpkg-reconfigure sddm => DM by default is sddm
-- move /home/<username> to /home/<username>_2015.06.12 (still login loop with compiz but metacity is working)
-- in tty1: ls -lah 
--- no files displays "root root" except "..", all other show <username> <username>
-- dpkg-reconfigure lightdm => DM by default is lightdm

Removing KDE
- sudo apt-get install aptitude
- sudo apt-get autoremove
-- problem was found in /sda4
-- I was asked to choose between gdm and lightdm so DM by default is now lightdm
-- dpkg-reconfigure lightdm => DM by default is lightdm

Clean
- sudo apt-get purge lightdm (removes lightdm and ubuntu-desktop)
- sudo apt-get purge compiz (removes compiz and unity)
- sudo apt-get install ubuntu-desktop (implies lightdm + compiz + unity)
- sudo apt-get install compizconfig-settings-manager (and enable the unity plugin)
- DISPLAY=:0 ccsm
- sudo reboot
- sudo killall unity-panel-service 
- remove GDM

- sudo reboot in Gnome (from the "ubuntu" icon next to my username I found that I can change from "Ubuntu (default)" to "GNOME")
In Software updater tab "additional drivers":
1) I switched the ATI driver from Server X X.Org (free) to fglrx-updates
2) I switched the "Unknown:Unknown" driver from "Do not use the device" to "Use intel-microcode"

After a reboot, now the GNOME desktop brings me to the login loop.
But the Ubuntu (default) desktop, with unity, the one that I prefer, is now working properly !
I will try to mark the topic as solved. :-) !

---

