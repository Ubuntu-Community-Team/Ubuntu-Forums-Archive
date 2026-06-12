---
title: "After 6.06 upgrade, most system admin functions missing"
date: 2006-09-24
forum: Installation &amp; Upgrades
---

### Post by Murwiz on 2006-09-24
I installed version 5 from a distribution CD yesterday, and all the system administration functions were available in my "System" menu. This morning I upgraded to 6.06, and the System menu is a lot smaller. For instance, there's no "Synaptic package manager" option. I can still run it by invoking from the command line, but where did all the menu options go?

---

### Post by danielph on 2006-09-24
Have you got Alacarte menu editor -  Applications, Accessories. Check out if the options for the System Admin programs are in the menu and not enabled.

---

### Post by Murwiz on 2006-09-24
Yes, in fact they are in the menu there and enabled. They don't show up, though.

---

### Post by danielph on 2006-09-24
You could try update-menus

---

### Post by Murwiz on 2006-09-24
Sorry, I didn't understand your suggestion.

---

### Post by danielph on 2006-09-24
Sorry, I'll be clearer.

You need to run the command update-menus from a terminal window. Not sure if you have it in your menus so we can use alt-f2 to run an applcation like this:

Press Alt and F2 together and type ```
gnome-terminal
``` and click on run.

This should open a terminal window. In the terminal type ```
update-menus
``` and press Enter

---

### Post by Murwiz on 2006-09-24
No dice:

$ update-menus
bash: update-menus: command not found
$ locate update-menus
$

---

### Post by danielph on 2006-09-24
Strange, I have that command. How did you upgrade? Have you updated all your packages since the upgrade? The command for synaptic is ```
gksu /usr/sbin/synaptic
``` Try a reload and see if there are required updates perhaps you are missing something?

Another suggestion is to create another user and see if you have the menus in the other account.

---

### Post by danielph on 2006-09-24
Try opening a terminal again and run 2 commands
sudo apt-get install menu
update-menus

---

### Post by Murwiz on 2006-09-24
I upgraded from 5.10 for 64-bit, to 6.06, via the Synaptic package manager. I just let it do its thing when it prompted me about the new version.

I just tried adding a new user from the command line using "adduser". That user has the same menus, with no sysadmin functions.

---

### Post by Murwiz on 2006-09-24
> **danielph said:**
> 
sudo apt-get install menu
update-menus

Tried that, still nothing.

---

### Post by danielph on 2006-09-24
Well I have menu and menu-xdg on this system, you could try installing that also

```
sudo apt-get install menu-xdg
update-menus
```

---

### Post by Murwiz on 2006-09-24
Still nothing ... even logged out and back in, just in case the menus were loaded only at login.

---

### Post by danielph on 2006-09-24
Well that is me out of ideas. Anyone else?

---

### Post by danielph on 2006-09-24
Until you find a solution you can run ```
gnome-control-center
``` to give you some access.

---

### Post by Murwiz on 2006-09-24
gnome-control-center gives me the menu items that are in the "Preferences" menu I already have. I'm looking for the system administration functions like "Shared Folders", "Add Applications", etc.

---

### Post by danielph on 2006-09-25
Well I guess we have 3 options:

1.You say it is a new installation, so you can reinstall 6.06 from scratch
2. We can cut and paste the information into the menu through alacarte
3. Find the name of the menu item file and paste the info from that
The config is normally in 
[LIST=1]
[*]~/.config/menus/applications.menu
[*]~/.local/share/desktop-directories
[*]~/.local/share/application[/LIST]I do not know the structure well enough to work from here though so I here is the information from Alacarte. The format is 
Name
Comment
Command
Icon

You may have to change the icon files to suit

```
Device Manager
View hardware information
hal-device-manager
/usr/share/icons/gnome/48x48/apps/hwbrowser.png

Discs
Configure the system discs
gksu disks-admin
/usr/share/icons/gnome/48x48/filesystems/gnome-fs-blockdev.png

Language Support
Configure multiple and native language support on your system
gksu /usr/bin/gnome-language-selector
/usr/share/icons/gnome/24x24/apps/config-language.png

Login Window
Configure the login window (GNOME Display Manager)
gksu gdmsetup
/usr/share/pixmaps/gdm-setup.png

Networking
Configure network devices and connections
gksu network-admin
/usr/share/icons/gnome/24x24/filesystems/gnome-fs-network.png

Printing
Configure your printers
gnome-cups-manager
/usr/share/icons/gnome/24x24/devices/gnome-dev-printer.png

Services
Configure which services will be run when the system starts
gksu services-admin
/usr/share/icons/gnome/24x24/filesystems/gnome-fs-server.png

Shared Folders
Configure which folders will be shared with others
gksu shares-admin
/usr/share/icons/gnome/24x24/filesystems/gnome-fs-share.png

Synaptic Package Manager
Install, remove and upgrade software packages
gksu /usr/sbin/synaptic
/usr/share/pixmaps/synaptic.png

System Log
View the system log file
gnome-system-log
/usr/share/icons/gnome/48x48/apps/logviewer.png

System Monitor
View current processes and monitor system state
gnome-system-monitor
/usr/share/icons/gnome/24x24/apps/gnome-monitor.png

Time and Date
Change system time, date, and timezone
gksu time-admin
/usr/share/icons/gnome/48x48/apps/config-date.png

Update Manager
Show and install available updates
gksu /usr/bin/update-manager
/usr/share/icons/hicolor/24x24/apps/update-manager.png

Users and Groups
Add or remove users and groups
gksu users-admin
/usr/share/icons/gnome/24x24/apps/config-users.png
```

---

### Post by Murwiz on 2006-09-25
My problem was the clobbering of my account so that it was no longer a member of the "admin" group. I booted into recovery mode, did this:

```
$ adduser {myname} admin
```

and everything went back to normal.

---

### Post by danielph on 2006-09-25
Most excellent, glad you found the answer!

---

