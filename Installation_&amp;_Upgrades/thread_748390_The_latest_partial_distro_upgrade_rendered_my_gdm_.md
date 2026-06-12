---
title: "The latest partial distro upgrade rendered my gdm useless - blank desktop!"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by cr0atian on 2008-04-07
I am not a total novice when it comes to Linux, but I am not very good at it either. I'm some place in between leaning towards a novice. What I am, however, is a Microsoft Windows support professional who uses Linux as a learning platform striving to achieve nirvana of a sort. :)

No, enough about me (it's my first post on this forum, so forgive me). What I just experienced a few minutes ago after my darling Hardy told me that I have some partial distro upgrades available is somewhat puzzling to me because I now find myself with the blank desktop and Compiz Fusion that won't run. No icons, no toolbars, no gdm, no menus... nothing... zero... zilch... nada.... nicht.... ništa!

Can someone tell me what I can do to get my desktop back? Is something wrong with the default display manager libraries or someone's monkeying around with partially finished code that is intended to cause harm to people's desktops because they don't agree with the color choice or something? :mad:

Please help me, whoever you are... I love my Linux Ubuntu and I show it off to all my coworkers proudly every day. I love the expression on their faces when I show them all the eye candy in Compiz Fusion running on a system that supposedly "can't run Vista" because "Microsoft said so". ;-)

Yours truly,

Croatian

---

### Post by warp99 on 2008-04-07
Can you boot into recovery mode without any problems? If so we can downgrade the packages that are causing the problems.

---

### Post by cr0atian on 2008-04-07
If I select recovery I can get to the # prompt as root no problem. I also tried running just the terminal screen by selecting that at the logon prompt from the session chooser. So, I do have graphics, just nothing on it. The terminal shows in the lower right corner surrounded by nothing but the nice uniformly colored "Human" color. I can type anything I want, I can launch compiz --replace and it then invokes emerald, which makes my terminal window nicer looking allowing me to move it, the cube rotates (although blank) and all compiz plugins seem to run just fine. If I try running gdm it tells me that it's already running, so fair enough, that at least seems to be loading. I can run thunar, evolution and other useful things, firefox included. Everything seems to run except that the whole screen is blank, no icons, no toolbars, no panels... nothing. Please tell me what you think I should do to uninstall what screwed me up? How do I get a boot log file of a sort to examine what is the error that causes it to do that? I ran apt-get update, apt-get dist-upgrade, apt-get autoclean... you name it i ran it... but no candy.

Grateful Croat

---

### Post by warp99 on 2008-04-07
Can you run Synaptic in the desktop? Because if you can it would be easier.

---

### Post by cr0atian on 2008-04-07
Yes, I can. What should I look for to remove? Is there a filter of a sort based on the time period when I did those updates so I can remove them or you got something more specific in mind?

---

### Post by warp99 on 2008-04-07
Yes go into synaptic under 'File' > 'History'. You can get a list of updated packages from the date and time you did this. Find the first package in the scrolling list, highlight then right mouse click and choose 'Properties'. When the dialog box pops up click on versions and see if there are multiple version available. If there are multiple versions read the instructions at the bottom of the dialog box and repeat this for each of the updated files in the history list. If there are not multiple versions then you're going to have to do this from the command line.

Now before you do this how many packages are in the history list that you updated? Because if the number is very large your best bet is to wait a few days for another update to see if that smooths out the problem. Anyway here is the way to downgrade the packages using an example with the packages 'tasks', 'bar' and 'foo': 

```
sudo apt-cache policy tasks
```
you'll get an output similar to this:
```
 sudo apt-cache policy tasks
tasks:
  Installed: (none)
  Candidate: 0.12-1ubuntu1~gutsy1
  Version table:
     0.12-1ubuntu1~gutsy1 0
        500 http://archive.ubuntu.com gutsy-backports/universe Packages
     0.11-1ubuntu1 0
        500 http://archive.ubuntu.com gutsy/universe Packages

```
then the following:
```
sudo apt-get install tasks=0.11-1ubuntu1
```
this is going to downgrade the package to the previous version. Now you may have dependency problems by doing this with a single package, so the best thing is to string all of your packages with one command:
```
sudo apt-get install tasks=0.11-1ubuntu1 bar=0.113.1ubuntu1 foo=0.3.451ubuntu1
```
or you can put all of the packages with versions in a text file:
```
tasks=0.11-1ubuntu1 
bar=0.113.1ubuntu1 
foo=0.3.451ubuntu1
```
and in the same directory as the text file enter the following:
```
sudo apt-get install $(cat my_text_file)
```
and the variable will pass the contents of the text file to apt-get. Once Hardy is released out of beta you can most likely update the packages. Hope this helps.

Edit:

You can also get a history list of the packages you installed from the command line:
```
sudo gedit /var/log/apt/term.log
```

---

### Post by cr0atian on 2008-04-07
Beautiful, I'll give that a try. Thank you very much and I'll get back to you some time tomorrow morning (Nashville, TN) when I go back to work. I agree that sometime it's best to wait for a day or two until better packages become available. That's the way I once managed to get a halted logon screen (7 minutes wait time) to finally show up immediately so I can log in. One of those updates fixed it.

BTW, I even managed to get one of my best friends who's a plumber and knows very little about computers to actually try and enjoy installing various Linux distributions. He got so much into it that he calls me almost every other day just to tell me about his latest achievements. Man, if even he can do Linux... I'm out of my job pretty soon! :lolflag:

---

### Post by cr0atian on 2008-04-08
Oh boy, this is not going to be fun. The list of things i updated that day is impressive as in:

Commit Log for Mon Apr  7 09:31:05 2008


Upgraded the following packages:
apport (0.106) to 0.107
apport-gtk (0.106) to 0.107
bluez-audio (3.26-0ubuntu4) to 3.26-0ubuntu5
bluez-cups (3.26-0ubuntu4) to 3.26-0ubuntu5
bluez-utils (3.26-0ubuntu4) to 3.26-0ubuntu5
capplets-data (1:2.22.0-0ubuntu3) to 1:2.22.0-0ubuntu5
cryptsetup (2:1.0.5-2ubuntu10) to 2:1.0.5-2ubuntu11
cupsys (1.3.7-1ubuntu1) to 1.3.7-1ubuntu2
cupsys-bsd (1.3.7-1ubuntu1) to 1.3.7-1ubuntu2
cupsys-client (1.3.7-1ubuntu1) to 1.3.7-1ubuntu2
cupsys-common (1.3.7-1ubuntu1) to 1.3.7-1ubuntu2
egroupware (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-addressbook (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-bookmarks (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-calendar (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-core (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-developer-tools (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-emailadmin (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-etemplate (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-felamimail (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-filemanager (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-infolog (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-ldap (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-manual (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-mydms (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-news-admin (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-phpbrain (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-phpsysinfo (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-polls (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-projectmanager (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-registration (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-resources (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-sambaadmin (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-sitemgr (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-timesheet (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-wiki (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
egroupware-workflow (1.2.107-2.dfsg-2) to 1.2.107-2.dfsg-2ubuntu1
firefox (3.0~b4+nobinonly-0ubuntu1) to 3.0~b5+nobinonly-0ubuntu1
firefox-3.0 (3.0~b4+nobinonly-0ubuntu1) to 3.0~b5+nobinonly-0ubuntu1
firefox-3.0-gnome-support (3.0~b4+nobinonly-0ubuntu1) to 3.0~b5+nobinonly-0ubuntu1
firefox-gnome-support (3.0~b4+nobinonly-0ubuntu1) to 3.0~b5+nobinonly-0ubuntu1
gfxboot-theme-ubuntu (0.5.15) to 0.5.16
gksu (2.0.0-5ubuntu1) to 2.0.0-5ubuntu2
gnome-control-center (1:2.22.0-0ubuntu3) to 1:2.22.0-0ubuntu5
gnome-keyring (2.22.0-2) to 2.22.1-1
gnome-volume-manager (2.22.1-1ubuntu4) to 2.22.1-1ubuntu5
gscan2pdf (0.9.21-1ubuntu3) to 0.9.21-1ubuntu4
guidance-backends (0.8.0svn20080103-0ubuntu10) to 0.8.0svn20080103-0ubuntu11
jockey-common (0.3.3-0ubuntu5) to 0.3.3-0ubuntu6
jockey-gtk (0.3.3-0ubuntu5) to 0.3.3-0ubuntu6
klibc-utils (1.5.7-4ubuntu2) to 1.5.7-4ubuntu3
libc6 (2.7-10ubuntu2) to 2.7-10ubuntu3
libc6-dev (2.7-10ubuntu2) to 2.7-10ubuntu3
libc6-i686 (2.7-10ubuntu2) to 2.7-10ubuntu3
libcupsimage2 (1.3.7-1ubuntu1) to 1.3.7-1ubuntu2
libcupsys2 (1.3.7-1ubuntu1) to 1.3.7-1ubuntu2
libcupsys2-dev (1.3.7-1ubuntu1) to 1.3.7-1ubuntu2
libdb4.3 (4.3.29-11) to 4.3.29-11ubuntu1
libgl1-mesa-dev (7.0.3~rc2-1ubuntu2) to 7.0.3~rc2-1ubuntu3
libgl1-mesa-dri (7.0.3~rc2-1ubuntu2) to 7.0.3~rc2-1ubuntu3
libgl1-mesa-glx (7.0.3~rc2-1ubuntu2) to 7.0.3~rc2-1ubuntu3
libglu1-mesa (7.0.3~rc2-1ubuntu2) to 7.0.3~rc2-1ubuntu3
libglu1-mesa-dev (7.0.3~rc2-1ubuntu2) to 7.0.3~rc2-1ubuntu3
libgnome-keyring-dev (2.22.0-2) to 2.22.1-1
libgnome-keyring0 (2.22.0-2) to 2.22.1-1
libgnome-window-settings1 (1:2.22.0-0ubuntu3) to 1:2.22.0-0ubuntu5
libklibc (1.5.7-4ubuntu2) to 1.5.7-4ubuntu3
libnspr4-0d (4.7.0~1.9b4-0ubuntu1) to 4.7.1~beta2-0ubuntu1
libnspr4-dev (4.7.0~1.9b4-0ubuntu1) to 4.7.1~beta2-0ubuntu1
libnss3-0d (3.12.0~1.9b4-0ubuntu1) to 3.12.0~beta3-0ubuntu1
libnss3-1d (3.12.0~1.9b4-0ubuntu1) to 3.12.0~beta3-0ubuntu1
libpam-gnome-keyring (2.22.0-2) to 2.22.1-1
libpulse-browse0 (0.9.9-1ubuntu4) to 0.9.10-1ubuntu1
libpulse0 (0.9.9-1ubuntu4) to 0.9.10-1ubuntu1
libpulsecore5 (0.9.9-1ubuntu4) to 0.9.10-1ubuntu1
libscim8c2a (1.4.7-3ubuntu6) to 1.4.7-3ubuntu7
mesa-common-dev (7.0.3~rc2-1ubuntu2) to 7.0.3~rc2-1ubuntu3
mesa-utils (7.0.3~rc2-1ubuntu2) to 7.0.3~rc2-1ubuntu3
mousetweaks (2.22.0-0ubuntu2) to 2.22.1-0ubuntu1
mozilla-imagezoom (0.3-1ubuntu1) to 0.3.1-0ubuntu1
mplayer (2:1.0~rc2-0ubuntu12) to 2:1.0~rc2-0ubuntu13
openssh-client (1:4.7p1-7ubuntu1) to 1:4.7p1-8ubuntu1
pulseaudio (0.9.9-1ubuntu4) to 0.9.10-1ubuntu1
pulseaudio-esound-compat (0.9.9-1ubuntu4) to 0.9.10-1ubuntu1
pulseaudio-module-gconf (0.9.9-1ubuntu4) to 0.9.10-1ubuntu1
pulseaudio-module-hal (0.9.9-1ubuntu4) to 0.9.10-1ubuntu1
pulseaudio-module-x11 (0.9.9-1ubuntu4) to 0.9.10-1ubuntu1
pulseaudio-utils (0.9.9-1ubuntu4) to 0.9.10-1ubuntu1
python-apport (0.106) to 0.107
python-problem-report (0.106) to 0.107
scim (1.4.7-3ubuntu6) to 1.4.7-3ubuntu7
scim-gtk2-immodule (1.4.7-3ubuntu6) to 1.4.7-3ubuntu7
scim-modules-socket (1.4.7-3ubuntu6) to 1.4.7-3ubuntu7
seahorse (2.22.0-0ubuntu2) to 2.22.1-0ubuntu1
ssh-askpass-gnome (1:4.7p1-7ubuntu1) to 1:4.7p1-8ubuntu1
system-config-printer-common (0.7.81+svn1976-0ubuntu5) to 0.7.81+svn1976-0ubuntu6
system-config-printer-gnome (0.7.81+svn1976-0ubuntu5) to 0.7.81+svn1976-0ubuntu6
ubufox (0.5~beta2.1-0ubuntu1) to 0.5~rc1-0ubuntu1
update-notifier (0.70.6) to 0.70.7
update-notifier-common (0.70.6) to 0.70.7
wine (0.9.58-0ubuntu2) to 0.9.58-0ubuntu3
xserver-xorg-video-intel (2:2.2.1-1ubuntu6) to 2:2.2.1-1ubuntu10
xulrunner-1.9 (1.9~b4+nobinonly-0ubuntu1) to 1.9~b5+nobinonly-0ubuntu1
xulrunner-1.9-gnome-support (1.9~b4+nobinonly-0ubuntu1) to 1.9~b5+nobinonly-0ubuntu1

---

### Post by warp99 on 2008-04-08
That's a lot of updates and I don't see anything that stands out as a problem. Can you make a new user and login as the new user? It's possible that one of your local configuration files is messed up. Without seeing your desktop it's impossible to tell. You can do if from the command line pretty easy if you can't access the GUI tools. First you need to get a list of your current user groups:
```
groups <$your_user>
```
output similar to this:
```
<$your_user> : <$your_user> adm dialout cdrom floppy audio dip video plugdev scanner fuse admin powerdev mythtv lpadmin
```
then add a new user:
```
sudo adduser <$newuser>
```
and then add the same groups:
```
sudo usermod -G adm,dialout,cdrom,floppy,audio,dip,video,plugdev,scanner,fuse admin,powerdev,mythtv,lpadmin <$newuser>
```

Now the new user should have sudo access since he/she is under the admin group.

Edit:

if that doesn't work I've modified your list to downgrade the updates  you made and attached the list to this post. You would then run the following:

```
sudo apt-get install $(cat my_file.txt)
```

Just make sure the my_file.txt is in the same directory when you issue the command.

---

### Post by cr0atian on 2008-04-08
Wow, that is more help than I've ever hoped for. Thanks a million! I was busy all day long, usual IT stuff (i.e. fix my mouse, move my computer etc.) so I wasn't able to do much troubleshooting today. However, a very few new updates came in this morning and I applied them in hopes that it would help, but they didn't help. I thought of using the root to login and I did that yesterday (yes, I enabled root to be allowed login), but that gave me the same result as with my user name. I will try your suggestion to see if creating another account will work, but if it doesn't - off I go doing the suggested downgrade.

Grateful Croat

---

### Post by cr0atian on 2008-04-08
If i launch Nautilus then my desktop icons show up, but i still can't get the panel and the pull-down menus back. Also when I right click anywhere on the desktop and select the option to create a launcher nothing happens at all except for a "click" sound. I tried to run x-session-manager by double clicking it and it told me that there was an error with GNOME Settings Daemon that caused it to crash and it will try to load it again on the next run. Right now I'm downloading more updates. I created a new user, but the logon screen doesn't let me use that user name to log in with. I know I'd have to add it somehow, but I'll think about that tomorrow. For some odd reason, when my desktop finally came back after launching Nautilus I noticed two generic looking executable icons on my desktop, one is kstart and the other one is konsole. I don't recall ever pacing them on my desktop. Could it be that one of those updates assumed I'm using KDE and it simply messed up my preference for the GUI? I'm using GNOME, not KDE.

---

### Post by Peter09 on 2008-04-08
This has hit a few people over the last couple of days, there is a lot of help in the Hardy forums (development). I think you need to re-install your video driver, is it Nvidia?

PC

---

### Post by warp99 on 2008-04-08
> **cr0atian said:**
> If i launch Nautilus then my desktop icons show up, but i still can't get the panel and the pull-down menus back. Also when I right click anywhere on the desktop and select the option to create a launcher nothing happens at all except for a "click" sound. I tried to run x-session-manager by double clicking it and it told me that there was an error with GNOME Settings Daemon that caused it to crash and it will try to load it again on the next run. Right now I'm downloading more updates. I created a new user, but the logon screen doesn't let me use that user name to log in with. I know I'd have to add it somehow, but I'll think about that tomorrow. For some odd reason, when my desktop finally came back after launching Nautilus I noticed two generic looking executable icons on my desktop, one is kstart and the other one is konsole. I don't recall ever pacing them on my desktop. Could it be that one of those updates assumed I'm using KDE and it simply messed up my preference for the GUI? I'm using GNOME, not KDE.

That error looks like when you were updating it was interrupted during the process and somehow wasn't completed. I've had an error occur before very similar to this. The repair was to reinstall the packages that I updated. You can do this with the list I posted  and remove the '=<version_number>" from each file in the list then running this command:

```
sudo apt-get install --reinstall $(cat my_file.txt)
```

That will re-install all of the packages with the latest versions Hope this helps.

Edit:

The new user you made should be available immediately, but you have to reload xserver, i.e ctrl-alt-backspace.

---

### Post by cr0atian on 2008-04-09
To answer Peter's question first; no, I don't have nVidia card. Mine is a built-in Dell flavor of Intel video chipset (taken from my xorg.conf):

```
Section "Device"
        Identifier      "Intel Corporation 82945G/GZ Integrated Graphics Controller"
        Boardname       "Intel 945"
        Busid           "PCI:0:2:0"
        Driver          "i810"
        Screen  0
        Vendorname      "Intel"
EndSection
```

Right now I'm doing the re-installation of that entire list of things I "upgraded" or "Updated" that faithful day. I erased all the version info starting with the = symbol from each line in the text file and it's happy. We'll see how it goes (my Internet speed at work is 3 times slower than the one at my home).

---

### Post by cr0atian on 2008-04-09
After re-install of all those things I'm still back to the same problem, nothing changed... I'm still screwed. I did create another account like you suggested I do, but bu using the GUI interface to add new user. I gave it the Administrative profile and not the Desktop User profile. The graphical logon screen still won't let me log in as that user. How can I get that done? I doubt that this new user will help because I'm having the same missing panels and menus issue with the root login, which i can use to log in from the GUI logon prompt.

Peter, can you give me the link to that message board or forum thread where you saw people talking about the same issue I have? Thanks!

---

### Post by cr0atian on 2008-04-09
Okay, how about this for strange? I just launched the user-admin (GUI tool) to see what's wrong with that new user name I created and to my surprise it wasn't even in there any more! :confused:

I tried to create one again, it didn't toss any complaints or errors (once I clicked the "unlock" button), but after i closed the tool and launched it again the account was gone yet again! :confused:

What in the world....?????? I'll try the command line instructions now to see if that works.

---

### Post by cr0atian on 2008-04-09
You know what guys? My thinking is that if it wants KDE I'll give it one and then I'll select GNOME again once it has satisfied its cravings.

Also, here's what happens when I do compiz --replace:

```
Checking for Xgl: not present.
Detected PCI ID for VGA: 00:02.0 0300: 8086:2772 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (core) - Warn: Unable to parse XML metadata from file "ccp.xml"
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Failed to execute dbus-launch to autolaunch D-Bus session
/usr/bin/compiz.real (dbus) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Couldn't find a perfect decorator match; trying all decorators
Starting emerald

```

So, it starts fine with emerald. That's good, I guess. I'm just wondering why it doesn't find a working gtk first. Maybe the compiz wrapper uses emerald as the default decorator or I left it that way the last time everything worked fine so it remembers. But, what about the dbus plugin error and the ccp.xml parsing error? That doesn't look normal either.

---

### Post by cr0atian on 2008-04-09
Finally added a new user manually using the command prompt tools. It still doesn't work. Sorry, but it's time to try some new approaches. Next thing I'll try is to use synaptic to install kubuntu (or just KDE).

---

### Post by warp99 on 2008-04-09
That could the problem. Let's purge the Compiz and see if the desktop comes back. You can always add it in later no problem:

```
sudo apt-get remove --purge compiz
```

---

### Post by warp99 on 2008-04-09
Here's the problem:
```
/usr/bin/compiz.real (core) - Warn: Unable to parse XML metadata from file "ccp.xml"
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Failed to execute dbus-launch to autolaunch D-Bus session
/usr/bin/compiz.real (dbus) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

Compiz is missing the dbus-plugin plus there's a failure with reading the some of the xml data. So your best bet is to purge Compiz like I stated before and just wait until Hardy comes out of beta and then just re-install Compiz.

---

### Post by cr0atian on 2008-04-09
When I run the command you gave me all I get back is a statement that compiz is already the latest version. That purge isn't purging anything it seems like. Is that the right command? Here's the output I get:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
compiz is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by warp99 on 2008-04-09
Oh .. I made a mistake that should be 'remove' instead of 'install'. I changed my original post to reflect this.

---

### Post by cr0atian on 2008-04-09
Thanks, but in the mean time I removed anything and everything dealing with compiz through synaptic by doing a simple search for compiz and compiz-fusion. Then I right clicked each item and selected complete removal option. That took everything out (I think), but.... there's that 'but' again.... still no change. I did 'locate compiz' command and it comes back with tone of stuff still present on my system dealing with compiz. maybe i should have waited for you to reply and use the 'remove --purge' options... but, some old Windows GUI habits are hard to kick. :(

What now?

---

### Post by cr0atian on 2008-04-09
In my hand I'm holding the latest 8.04 LTS Desktop Edition Ubuntu Beta ... AND I"M NOT AFRAID TO USE IT! :) At this point I'm looking at my computer with squinting eyes saying "Now, you've got to ask yourself one question; "Do I feel lucky?"... now do you, punk?" :popcorn:

Silliness aside, I think I just about had enough of this and I'm ready to reinstall this thing from scratch. What do you say? Do you have any other aces up your sleeve that we can try? What about that developer forum link Peter talked about? Where the heck is it? I'd like to browse through it and see what other folks are experiencing.

---

### Post by warp99 on 2008-04-09
Well the last thing you can do is to re-install the ubuntu-desktop or install the kubuntu-desktop if you like. Here's a good method to do this:

First boot into recovery mode and make sure you have a good internet connection. Then issue the following commands:

```
apt-get install ubuntu-desktop
```
Yes that's install the desktop, it may install some missing items. Go ahead and let that happen, then:
```
apt-get clean && apt-get remove --purge ubuntu-desktop

```
that's going to remove the Gnome desktop completely, Now there may be a problem with your local directory, so we're going to create a newuser with the method I stated earlier in the thread with the same groups. So create a new user account, then issue the following:

```
apt-get install ubuntu-desktop
```

Now if you want KDE you would substitute 'kubuntu' for 'ubuntu'. Now go get a Coke and when you come back depending on your internet connection you should be all ready to go. Just issue the reboot command and login under the new user name. If everything is fine try to login under the old user name to see if that works.

---

### Post by warp99 on 2008-04-09
To answer your other questions the Development forum is [here]("http://ubuntuforums.org/forumdisplay.php?f=305"). As for re-installing the entire OS you don't have to do that. Linux is a module operating system and any components that are giving you a hassle can be purged, re-installed, re-configured, and so on. I haven't re-installed any of my Ubuntu installs for at least the last three years. 

I once had to do a base install and restore from a backup because I was in a root bash session trying to remove some cruft and I did a 'rm -rf / opt' by accident. Opps! That taught me a lesson, don't enable the root account. :lolflag:

---

### Post by cr0atian on 2008-04-09
Guess what? I"M BACK IN BUSINESS!!!! YEAAAAHHHHHHHHH!!!!! :popcorn:

I've got all my stuff back, but not by what you said I should do (I know, I'm being naughty again), but by simply going to synaptic and searching for ubuntu-desktop. to my surprise the whole bloody thing wasn't even installed! None of the desktop flavors were installed! So, what is a nice Microsoft support person to do? He reaches for the almighty mouse, right clicks it ever so bravely and selects to install it. WOW!

:guitar:

I thank you from the bottom of my heart, this has been a very good learning experience for me. I now learned that Linux is so segmented into modules that just like the Lego Blocks, it too has to fit each piece perfectly - otherwise the pieces don't 'stick' and the outcome is less than desirable. The 'customization' mantra that is prevalent among Linux developers I think has some drawbacks regardless of the fact that it has far more advantages. The major drawback is that SOMETIME :mad: there is no uniformity to people's attempts to fit these Lego Blocks into something that does work - it's like the right hand doesn't know what the left hand is doing and vise versa. It leaves people like myself very well entertained while searching for the answers. After all I do belong to human species and us humans, as you know, are very curious creatures. Others who are not as "into it" as I am would just give up right away and simply say "Forget it! Linux is just a pile of %$#@$!" (<-- utter your own explicit here) and I think that's why the majority of ordinary folks don't get it and don't care much for it. Until someone wise comes and saves us all from the 'contributors' that don't pay attention to the detail there will be no success. I understand that this is just a BETA release, fair enough, I shouldn't expect much from it, but the fact remains that in a single instance thousands and maybe hundreds of thousands of "to be" supporters of Linux got denied the right to enjoy it by a simple mistake on someone's part who decides which updates are to be given to the public. I hope someone will recognize the amount of damage one such action can have on potential future Linux users and weigh the pros and cons of not testing what is to be released prior to releasing it. We are all volunteers for the BETA and in my opinion we should be entitled to a reasonable expectation that at least some testing is done before letting it out for us to test it further - especially since... how many years has it been since the first Linux was created?

I think it's Miller time for me now... too bad I'm at work and can't drink until I come home :)

You, Warp99, are a :KS in my opinion and again I can't thank you enough for all this.

THANK YOU!

Grateful Croat

---

