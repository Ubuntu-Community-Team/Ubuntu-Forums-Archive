---
title: "Unable to Install or Update Software Due to Frozen Dropbox Update"
date: 2014-10-26
forum: Installation &amp; Upgrades
---

### Post by Terence_Cordner on 2014-10-26
Hi, I've seen some similar issues to this in the past, but I'm a bit new to Ubuntu and wasn't able to figure out how to resolve it.  I had an automatic update for dropbox that keeps freezing at 100%. I'm not able to update or upgrade anything else because I believe it is stuck with the Dropbox update.  The error I get is: 

"Software index is broken. It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."  

I don't have Synaptic and can't install it. When I run the command in terminal I get:

"E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"


Is there an easy way that I can terminate this update? At this point I'm perfectly fine getting rid of Dropbox all together too.

Thanks for your help.

---

### Post by bapoumba on 2014-10-28
The message about the lock means there is another package manager open, the Software Center for ex. Please close it and run **sudo apt-get install -f** again and post the full output here, thanks.

---

### Post by Evan_B._Howard on 2014-11-03
Hi. I am *quite* new to Ubuntu and I have encountered precisely the same problem. I tried to install Dropbox (not noticing that it was meant for GNOME desktop while I have Unity preinstalled in my Dell xps 13). The installation froze. Likewise with my attempt to remove. My computer just kept running. Later, when using Update Manager I saw the "it is impossible to install or remove software message." When doing the "apt-get install -f" thing I received the message: "could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)    Unable to lock the administration directory 9/var/lib/dpkg/), is another process using it?"

Thanks to Bapouma's advice I tried "closing" the Software Manager and found no button to do this. I unlocked it from the launcher, but I am not sure that accomplished anything. After doing a little homework on "closing" programs, I went to the terminal and typed "sudo killall dropbox" and that stopped  the constant running of my computer. I received a message that I needed to take further steps now  in order to install dropbox. 

From that point, again, after a bit of homework (see "[Three Ways to Uninstall Ubuntu Software]("http://ww.wikihow.com/Uninstall-Ubuntu-Software")") I used "sudo apt-get --purge remove dropbox" to uninstall dropbox and the configurations related to the software. When complete, I received the message "Reading package lists . . . Done." Then "Building dependency tree" Then "Reading state information. . .  Done"  Then  "E: Unable to locate package dropbox"    I think this means I did something right, yes?  

First time I've done anything like this from the terminal. Now I'll try and install Synaptic.

---

### Post by bapoumba on 2014-11-03
@ Evan_B._Howard, if you want to check if you have removed dropbox (not sure this is what you intended), you can run :
```
apt-cache policy nautilus-dropbox
```
It will tell you if the package is installed or not. Here is for me, as an example, I do have it installed and working properly :
```
bapoumba@bapoumba-utopic:~$ apt-cache policy nautilus-dropbox
nautilus-dropbox:
  Installed: 1.6.2-1
  Candidate: 1.6.2-1
  Version table:
 *** 1.6.2-1 0
        500 http://archive.ubuntu.com/ubuntu/ utopic/multiverse i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Evan_B._Howard on 2014-11-03
Thanks, Bapoumba for the help.
      I ran your script and this is what I received:

> evan@evan-XPS13-9333:~$ apt-cache policy nautilus-dropbox
nautilus-dropbox:
  Installed: 0.7.1-2
  Candidate: 0.7.1-2
  Version table:
 *** 0.7.1-2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/multiverse amd64 Packages
        100 /var/lib/dpkg/status

So I tried the same command with a program I know is not installed (Geany). In this case I received:

> evan@evan-XPS13-9333:~$ apt-cache policy geany
geany:
  Installed: (none)
  Candidate: 0.21.dfsg-1ubuntu4
  Version table:
     0.21.dfsg-1ubuntu4 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe amd64 Packages

I think this means I still have not removed it yet, correct? I actually was trying to remove Dropbox after improperly installing it. I was thinking that I needed to (1) remove it, (2) learn how to configure it for Unity, and then (3) Install it again properly.

Comments? Thanks again.

---

### Post by m3ATmeX on 2014-11-04
Perhaps [this]("http://ubuntuforums.org/showthread.php?t=2248189&highlight=remove+dropbox") post will help you

---

### Post by bapoumba on 2014-11-05
Please also try **sudo apt-get purge nautilus-dropbox** and post the output if you get any error.

---

### Post by Evan_B._Howard on 2014-11-08
Here is my output:

> evan@evan-XPS13-9333:~$ sudo apt-get purge nautilus-dropbox
[sudo] password for evan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nautilus-dropbox*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 375 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 233643 files and directories currently installed.)
Removing nautilus-dropbox ...
Dropbox isn't running!
dropbox: no process found
Purging configuration files for nautilus-dropbox ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...

I checked through s/w center and found that Dropbox had been removed. Ten minutes earlier s/w center said it was installed.
Thank you for clarifying the NAUTILUS piece.

Now I will go to work on learning how to configure Dropbox for Unity before I try to install it again.

---

### Post by bapoumba on 2014-11-09
As far as I know, the nautilus-dropbox package is the one to install for all ubuntu flavors.

---

