---
title: "Administrative programs hang after partial upgrage to 8.04"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by batyi on 2008-06-03
I have upgraded from 7.04 to 8.04. Upgrade went well until conflict with manually installed python setuptools occurred and installer was unable install python-setuptools package. After that upgrade has aborted with message "Partial upgrade. System may be in unusable state."

I have removed manually installed setuptools and installed python-setuptools package. However: system works well except that almost all GUI applications that require administrative (root) rights hang indefinitely or aborting in a while doing nothing. Applications that hang are:

[LIST]
[*]Applications / Add/Remove (hangs when I lcick "apply changes")
[*]System / Administration / Software sources (does not show any window, aborts after a while)
[*]System / Administration / Hardware Drivers (does not show any window, aborts after a while)
[*]System / Administration / Update Manager (hangs when I click "check for updates")
[/LIST]

However sudo and gksu seem to be working properly.

How do I fix this?
Are there any means to retry installation(upgrade)?

---

### Post by caseyjones on 2008-06-03
It all works like a charm here without any complaints or problems whatsoever. Albeit I use a clean install and not an upgrade.

---

### Post by Purple Sheep on 2008-06-03
I have exactly the same problem, except supposedly the upgrade went perfectly (but I have experienced many other problems). Running "sudo update-manager" or "sudo synaptic" in the terminal allows you to run them so that they will work, as you enter the password in the terminal. What doesn't seem to be working is the screen that asks you for your password when you don't run them as root.

---

### Post by batyi on 2008-06-03
What I have also found from menu shortcuts some of administrative tools use gksu as GUI equivalent of sudo. If I run gksu explicitly it seems to be working. 

"Device drivers" launcher uses gksu, but "add/remove" and "update manager" launchers - do not (maybe it is invoked somewhere inside them).

What I also found that /usr/bin/gnome-app-install, /usr/bin/jockey-gtk (without gksu), /usr/bin/update-manager work if started from gnome console but hang if started from gnome menu. :-/

---

### Post by batyi on 2008-06-03
Seems that is authentication caching might be a problem. Reproduction:
1. Start gksu and run command ls
2. Enter credentials
3. For a while authentication will be cached and administrative applications work.

---

### Post by batyi on 2008-06-04
It looks like problem with gksu. Besides usual prompt, sudo also outputs message that "host my_local_host_name can not be resolved". Seems that this message confuses gksu. 
After I have added my_local_host_name to /etc/hosts, gksu seems to work as expected.

---

### Post by gregorys on 2008-06-04
> **caseyjones said:**
> It all works like a charm here without any complaints or problems whatsoever. Albeit I use a clean install and not an upgrade.

You're lucky, I did a clean install also. I also downloaded all of their updates and now I seem to have a problem with gksu. By the way, I'm using the 64-bit version. Are you running the 32-bit one? 


> **batyi said:**
> What I have also found from menu shortcuts some of administrative tools use gksu as GUI equivalent of sudo. If I run gksu explicitly it seems to be working. 

"Device drivers" launcher uses gksu, but "add/remove" and "update manager" launchers - do not (maybe it is invoked somewhere inside them).

What I also found that /usr/bin/gnome-app-install, /usr/bin/jockey-gtk (without gksu), /usr/bin/update-manager work if started from gnome console but hang if started from gnome menu. :-/

Yup, I'm also forced to use the terminal to get the job done.


> **batyi said:**
> It looks like problem with gksu. Besides usual prompt, sudo also outputs message that "host my_local_host_name can not be resolved". Seems that this message confuses gksu. 
After I have added my_local_host_name to /etc/hosts, gksu seems to work as expected.

Holy shrapnel, Rather than "mylocalhostname", Ubuntu alter it to "mylocalhostname.Ubuntu". After deleting the "Ubuntu" suffix after "mylocalhostname" the gui for administrative programs worked as normal.

The only question is: why did Ubuntu suddenly add the ".Ubuntu" suffix after 2 weeks of sound operation? ????

Well looks like everything is back to normal for now...


Edit: Batyi, Thank you very much for your input!

---

### Post by aiden83 on 2008-06-26
Purple Sheep, I have the same problem (which I have fixed, read on) and gksu was not the problem, instead the problem lies with the sudo configuration, because afterall I believe that gksu is a GUI to sudo.

I have installed Ubuntu manually to allow booting from RAID5 volume.

After installing the ubuntu-desktop package and booting into Gnome/Hardy, I was unable to run any root tasks, such as System -> Preferences -> Appearance  or System -> Administration -> Update manager.  
I could, however, run root tasks via terminal and the command su.  I had had trouble using the sudo command before this.
I fixed the problem so that now I can do all GUI based administrative tasks.  THe solution was posted previously here:
[http://ubuntuforums.org/archive/index.php/t-180206.html](http://ubuntuforums.org/archive/index.php/t-180206.html)

In short, the problem was:
An error when I run anything under 'System ---> Administration ---> Whatever'. I am the only user setup on this computer. Here is the error message.
Failed to run /usr/sbin/synaptic
The underlying authorization mechanism (sudo) does not allow you to run this program.

In short, the solution was:

To gain root privileges, either boot with recovery mode or append '1' as a kernel parameter on grub menu.

When logged as root in terminal, create group called admin
sudo groupadd admin

add your useraccount (e.g. aiden83) on the group
adduser aiden83 admin

Then change the /etc/sudoers file using visudo command:
visudo /etc/sudoers

Add the line:
%admin ALL=(ALL) ALL

 using visudo script 
After, your /etc/sudoers should look like:

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

I then rebooted and all was fixed I could use sudo graphically when prompted, thus I could change my Preferences --> Appearance from my user account to allow Extra Visual effects.

---

### Post by mac178 on 2008-07-07
I had the same problem.
I fixed it doing as batyi and gregorys, updating my /etc/hosts file.
Still wondering why it happened.
:)

---

