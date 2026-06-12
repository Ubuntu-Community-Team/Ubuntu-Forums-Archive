---
title: "Firefox not updating - what is the best way to update it using GUI method"
date: 2019-06-28
forum: Installation &amp; Upgrades
---

### Post by sunrise718 on 2019-06-28
Auto updates is selected in my settings but nothing seems to be updating.  I know that Firefox is not updating because I get a notification when I log in that I do not have the latest version.

I posted for help in this thread but never resolved the issue:  
[https://ubuntuforums.org/showthread.php?t=2411584&p=13834748#post13834748](https://ubuntuforums.org/showthread.php?t=2411584&p=13834748#post13834748)

What is the best way for me to update Firefox?  I prefer to use the GUI (graphical user interface) method if possible.

Thanks in advance.

---

### Post by uRock on 2019-06-28
Firefox would normally get updated when running system updates. Have you been able to get your system to update? If not, then could you run the following command in a terminal, then copy and paste it here?
```
sudo apt update && sudo apt dist-upgrade
```

---

### Post by sunrise718 on 2019-06-28
I get:
 
```
(Regular Username) is not in the sudoers file. This incident will be reported.
```

I always log in with my regular account for security purposes with the intention of entering the sudo password to access permission for this kind of thing.  

So, obviously, this is messed up.  

How do I fix this and get my updates straightened out?  

Thanks in advance.

---

### Post by uRock on 2019-06-29
You have to log in as admin to run updates. Even while logged in as admin, you'll get a prompt for a password before completing a root task.

---

### Post by sunrise718 on 2019-06-29
I never used to have to log in as an admin to get updates with a different (older) computer.  It would do it automatically from the regular user account after entering the admin password.  Has that changed?

That said, I logged in as the admin to check things out and discovered that my WiFi password was not in the system for that account.  Strange.  So, I entered that.

I was unable to enter the admin password in the terminal; it froze at that point.  

Then I tried to download the updates through settings and received the following failure notifications:

```
Unable to download updates from "extensions.gnome.org": [*/*/*/source/shell-extensions/*]failed to download https://extensions.gome.org//static/extensions.json: Cannot resolve hostname
```

And this:

```
Low disk on "var" The volume "var" has only 220.1 MB disk space memory
```

Clicking "Examine' produced the following:

```
Error opening directory /var/log/gdm3': Permission denied. Could not open some of the folders contained in "/var"
```

Perhaps the permission error was due to not having the network password in the system but that part was resolved.

Perhaps if these problems are resolved, I can properly download updates from the regular account using the admin password.

---

### Post by uRock on 2019-06-29
To run commands you have to be in the Admin user account. You do have the option to elevate to admin user for GUI applications from the Standard account.

The first line of code makes it appear the network connection is working properly.

The low disk space can be fixed by running a few commands from the admin account to clean up logs, temp, cache, and old packaging.```
sudo  apt clean
sudo apt autoclean
sudo apt autoremove
```After this and figuring out your network issue, if that's still happening, we should be able to get updates to run.

I usually run Bleachbit to keep the cache and temp files to a minimum.


[https://www.omgubuntu.co.uk/2016/08/5-ways-free-up-space-on-ubuntu](https://www.omgubuntu.co.uk/2016/08/5-ways-free-up-space-on-ubuntu)

---

### Post by sunrise718 on 2019-07-09
I need someone to help me figure out why Firefox is still not updating for me and neither are other updates.  I tried the advice above from uRock but that did not resolve the issues. 

When I try to update from my regular account via the GUI, I am getting:
[COLOR=#000000]
```
Unable to download updates from "extensions.gnome.org": [*/*/*/source/shell-extensions/*]failed to download [https://extensions.gome.org//static/extensions.json:](https://extensions.gome.org//static/extensions.json:) Cannot resolve hostname
```[/COLOR]
[COLOR=#000000]
And this:[/COLOR]

[COLOR=#000000]```
Low disk on "var" The volume "var" has only 241.6 MB disk space remaining.
```

[/COLOR]

---

### Post by TheFu on 2019-07-09
Packages are stored in /var/, so if /var is almost full, there isn't any room for the packages/updates to go.

I don't use the GUI, so cannot suggest any GUI solutions. Sorry.

---

### Post by uRock on 2019-07-09
> **sunrise718 said:**
> I need someone to help me figure out why Firefox is still not updating for me and neither are other updates.  I tried the advice above from uRock but that did not resolve the issues. 

When I try to update from my regular account via the GUI, I am getting:
[COLOR=#000000]
```
Unable to download updates from "extensions.gnome.org": [*/*/*/source/shell-extensions/*]failed to download [https://extensions.gome.org//static/extensions.json:](https://extensions.gome.org//static/extensions.json:) Cannot resolve hostname
```[/COLOR]
[COLOR=#000000]
And this:[/COLOR]

[COLOR=#000000]```
Low disk on "var" The volume "var" has only 241.6 MB disk space remaining.
```

[/COLOR]
What's your partitioning scheme? Can you open Disks and take a screenshot of the partition table or share the output of the following command,
```
sudo fdisk -l 
```

---

### Post by sunrise718 on 2019-08-17
> **uRock said:**
> What's your partitioning scheme? Can you open Disks and take a screenshot of the partition table or share the output of the following command,
```
sudo fdisk -l 
```

I was going to reply to you, uRock, but then the system crashed, no doubt due to a memory issue.  So, I reinstalled Ubuntu and so far all is well.  

This time I did not partition it like I did originally.  I went with the default installation.  

Onward and upward!  :D

---

