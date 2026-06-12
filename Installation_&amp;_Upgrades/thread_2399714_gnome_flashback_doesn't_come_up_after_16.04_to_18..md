---
title: "gnome flashback doesn't come up after 16.04 to 18.04 upgrade"
date: 2018-08-29
forum: Installation &amp; Upgrades
---

### Post by edwardsah3-3 on 2018-08-29
I just upgraded to 18.04. At the login screen I can select gnome flashback (compiz), and synaptic says that gnome-sessions-flashback is installed, but when I login, I just get the new gnome interface. Can someone demystify me?

Art Edwards

---

### Post by Claus7 on 2018-08-29
Hello,

this sounds as a display manager problem: gdm3, lightdm. Could you please check which of the two is installed from synaptic? If gdm3 is installed, purged it completely, install lightdm and reboot your system. Are you able to login as normal?

In case both are installed issue the command:
sudo dpkg-reconfigure gdm

and select lightdm.

Also, could you mention which are the packages in synaptic that are installed in your system with the name flashback?

Regards!

---

### Post by edwardsah3-3 on 2018-08-29
Thanks very much for the reply

Apparently, I don't have gdm installed:

root@theory:~# dpkg-reconfigure gdm
dpkg-query: package 'gdm' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: gdm is not installed

Packages with flashback in  the name:

theory/home/edwardsa>dpkg -l | grep flashback
ii  gnome-flashback                                             3.28.0-1ubuntu1                             amd64        helper application for the GNOME Flashback session
ii  gnome-flashback-common                                      3.28.0-1ubuntu1                             all          GNOME Flashback helper application - common data files
ii  gnome-session-flashback                                     1:3.28.0-1ubuntu1                           all          GNOME Session Manager - GNOME Flashback session

Art Edwards

---

### Post by edwardsah3-3 on 2018-08-29
A little bit more: I looked at synaptic, and gdm3 is installed. I invoked

root@theory:~# dpkg-reconfigure gdm3
gdm.service is not active, cannot reload.
invoke-rc.d: initscript gdm3, action "reload" failed.

Thanks,

Art Edwards

---

### Post by edwardsah3-3 on 2018-08-30
So, yours was the only response. I thought I gave all the information you requested. Do you have any ideas? If not, I think I'll be re-installing 16.04?

Thanks

---

### Post by Claus7 on 2018-08-31
Hello,

the packages you have installed are the ones they should. Please do follow the directions posted above (purging gdm3 and installing lightdm instead). It seems that in some boxes gdm3 and flashback do not work very well: [https://ubuntuforums.org/showthread.php?t=2399463&highlight=flashback](https://ubuntuforums.org/showthread.php?t=2399463&highlight=flashback)

Regards!

---

### Post by edwardsah3-3 on 2018-09-01
Sorry to take so long to get back to you. Between my last question and your response (only 42 minutes) I had decided to simply do a clean install of 18.04, to  see if that helped. It did. I had not purged gdm3. I do have another 16.04 box that I may upgrade now to 18.04, in which case your input could be very useful. Here is the thing. I now have a pretty fast internet connection, and a solid state drive for the system. I didn't time it, but the clean install, including installing all of the special tools I use seemed to be faster than the upgrade. The upgrade path left me asking people like you for help because it's impossible to debug every upgrade path. 

Thanks very much for responding to the query.

---

### Post by Claus7 on 2018-09-02
Hello,

> **edwardsah3-3 said:**
> Sorry to take so long to get back to you. Between my last question and your response (only 42 minutes) I had decided to simply do a clean install of 18.04, to  see if that helped. It did. I had not purged gdm3. I do have another 16.04 box that I may upgrade now to 18.04, in which case your input could be very useful. Here is the thing. I now have a pretty fast internet connection, and a solid state drive for the system. I didn't time it, but the clean install, including installing all of the special tools I use seemed to be faster than the upgrade. The upgrade path left me asking people like you for help because it's impossible to debug every upgrade path. 

Thanks very much for responding to the query.

it's normal not to be every single instance in front of a pc. Clean install indeed is a better solution as far as creating a more bug free system, yet, the issue is that some of your configurations have to take place once again, as you did already. The new upgrade you are planning might not show the same problem that you faced in the previous one. Yet, if it shows up, you have a solution that you could try. 
Happy ubuntu-ing!

Regards!

---

### Post by edwardsah3-3 on 2019-02-05
I'm back:

gnome-flashback worked for weeks. Then, out of the blue, it went away, and was replaced by what looks like a gnome-3 interface. I have done two clean installs since the first time it happened, and each time, flashback works for a while, and then goes away. I'm sitting in the Ubuntu desktop right now, not so ahppily. By the way, when I go to purge gdm3, it wants to remove ubuntu-desktop. I really don't want to do another fresh install, as it requires loading a lot of software I use for work. I did look at syslog, and there are a lot of errors.

Examples:
Failed to get current display configuration state: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Name "org.gnome.Mutter.DisplayConfig" does not exist
Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit gnome-user-share-webdav.service not loaded.

and others. I could include the sylog file if that would help.

Art Edwards

---

### Post by Claus7 on 2019-02-06
Hello again,

I do not face the issues you are facing, yet I would advice you to wait till tomorrow, max the day after tomorrow: ubuntu 18.04.2 will be released, so this might solve many of the issues you are facing. From a quick search I was able to see that at least some of the messages you are getting are some kind of gnome bugs.
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1752083](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1752083)

Just for clarification: you select gnome-flashback from login screen, and then what? It boots to another desktop environment?

Please do also check that your system is up to date with the following commands:
sudo apt update
sudo apt upgrade

check if you are getting any errors from these...

EDIT: it seems that the upgrade to 18.04.2 will take place next week...

Regards!

---

### Post by edwardsah3-3 on 2019-02-08
Hi:

I only saw your reply now. I have found an interesting thread on the gnome site. Here is the  link

[https://gitlab.gnome.org/GNOME/gnome-session/issues/6](https://gitlab.gnome.org/GNOME/gnome-session/issues/6)

It seems that the files

~/.local/share/applications/gnome-flashback-init.desktop
~/.local/share/applications/gnome-flashback.desktop

Eventually get a 

Hidden=True

prepended to them. In my now fourth clean install these files do not appear in my .local/share/applications, even with gnome-flashback working. The do appear in 
/usr/share/applications/, and, currently, there is no Hidden=True. My guess is that on an update a new gnome install has written that line in.
II have to get some work done this weekend, so I am avoiding reboots, although I have done the 

apt-get update
apt-get dist-upgrade

and gnome-flashback still abides. After I have passed the deadline this Monday, I will be a little more courageous.

Thanks for your replies.

---

### Post by oldfred on 2019-02-08
I only do clean installs, now.
And my flashback install command changed to gnome-panel, but installed flashback.
In checking some of the paths posted in your links, I do have some mention of flashback, but the hidden  .local/share only has nautilus-classic.desktop.

fred@Bionic-Z170N:~$ echo $DESKTOP_SESSION
gnome-flashback-metacity
fred@Bionic-Z170N:~$ gnome-shell --version
GNOME Shell 3.28.3
fred@Bionic-Z170N:~$ env | grep XDG_CURRENT_DESKTOP
XDG_CURRENT_DESKTOP=GNOME-Flashback:GNOME

---

### Post by Claus7 on 2019-02-10
Hello,

> **edwardsah3-3 said:**
> Hi:

It seems that the files

~/.local/share/applications/gnome-flashback-init.desktop
~/.local/share/applications/gnome-flashback.desktop

Eventually get a 

Hidden=True

prepended to them. In my now fourth clean install these files do not appear in my .local/share/applications, even with gnome-flashback working. The do appear in 
/usr/share/applications/, and, currently, there is no Hidden=True. 

I have made an upgrade and not a clean install. Still now, at 18.04.1, the files in question are found under /usr/share/applications and they are not found as hidden ones under the HOME folder.

I do not see any Hidden string in their content as well. 

Regards!

---

### Post by Claus7 on 2019-02-14
Hello,

ditto for 18.04.2.

Regards!

---

