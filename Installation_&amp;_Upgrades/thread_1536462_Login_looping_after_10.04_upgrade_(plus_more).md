---
title: "Login looping after 10.04 upgrade (plus more)"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by Penny N. Nickels on 2010-07-22
A couple weeks back, I upgraded to **9.10**. Shortly afterwards, I started having trouble with [COLOR=Red]logging in[/COLOR], rarely sending me to my desktop after one try. I tried changing my setting to bypass logging in. It rarely works. For whatever the reason, it sometimes helps when I reset the setting on the bottom of the login page (language, keyboard, etc.) to what they already are.

Then, there have been several times, after I do reach the desktop, I get the following error box: > An error occurred while loading or saving configuration info for evolution-alarm-notify. Some of your configuration setting may not work properly.Inside the box read: > *Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for info. (Details: Failed to get connection to session: Failed to connect to socket /tmp/dbus-[*this varies each time*]. Connection refused.* This message is repeated inside the box as many times as I attempted to login due to the looping.

It happened again this morning. The following is from the user.log from this morning's multiple tries:

> [I]Jul 22 05:51:39 marilyn-desktop pulseaudio[1635]: pid.c: Stale PID file, overwriting.
Jul 22 05:51:58 marilyn-desktop pulseaudio[1545]: ratelimit.c: 3 events suppressed
Jul 22 05:52:10 marilyn-desktop pulseaudio[1897]: pid.c: Stale PID file, overwriting.
Jul 22 05:52:26 marilyn-desktop pulseaudio[1545]: ratelimit.c: 3 events suppressed
Jul 22 05:52:34 marilyn-desktop pulseaudio[2111]: pid.c: Stale PID file, overwriting.
Jul 22 05:52:41 marilyn-desktop pulseaudio[2111]: ratelimit.c: 4 events suppressed
Jul 22 05:53:20 marilyn-desktop pulseaudio[2369]: pid.c: Stale PID file, overwriting.
Jul 22 05:53:28 marilyn-desktop pulseaudio[2369]: ratelimit.c: 5 events suppressed
Jul 22 05:53:29 marilyn-desktop pulseaudio[2484]: pid.c: Stale PID file, overwriting.
Jul 22 05:53:30 marilyn-desktop pulseaudio[2484]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-w46dPIYnuK: Connection refused
Jul 22 05:53:34 marilyn-desktop pulseaudio[1545]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul 22 05:53:34 marilyn-desktop pulseaudio[1545]: sink-input.c: Failed to create sink input: sink is suspended.
Jul 22 05:53:48 marilyn-desktop pulseaudio[2632]: pid.c: Daemon already running.
Jul 22 05:53:57 marilyn-desktop pulseaudio[2744]: pid.c: Stale PID file, overwriting.
Jul 22 05:53:58 marilyn-desktop pulseaudio[2744]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-rEHSeGerEV: Connection refused
Jul 22 05:54:02 marilyn-desktop pulseaudio[1545]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
Jul 22 05:54:02 marilyn-desktop pulseaudio[1545]: sink-input.c: Failed to create sink input: sink is suspended.
Jul 22 05:54:29 marilyn-desktop pulseaudio[2893]: pid.c: Daemon already running.
Jul 22 05:54:35 marilyn-desktop pulseaudio[2744]: ratelimit.c: 2 events suppressed
Jul 22 05:55:01 marilyn-desktop pulseaudio[3146]: pid.c: Stale PID file, overwriting.
Jul 22 05:55:06 marilyn-desktop bonobo-activation-server (marilyn-3203): could not associate with desktop session: Failed to connect to socket /tmp/dbus-vksaqtiMdg: Connection refused
Jul 22 05:55:07 marilyn-desktop pulseaudio[3146]: ratelimit.c: 1 events suppressed
Jul 22 05:55:33 marilyn-desktop pulseaudio[3408]: pid.c: Stale PID file, overwriting.
Jul 22 05:55:41 marilyn-desktop bonobo-activation-server (marilyn-3498 ): could not associate with desktop session: Failed to connect to socket /tmp/dbus-a97EUEjz1n: Connection refused
Jul 22 05:56:09 marilyn-desktop pulseaudio[3671]: pid.c: Stale PID file, overwriting.
Jul 22 05:56:11 marilyn-desktop bonobo-activation-server (marilyn-3680): could not associate with desktop session: Failed to connect to socket /tmp/dbus-CBB8evsFBl: Connection refused
Jul 22 05:56:55 marilyn-desktop pulseaudio[3934]: pid.c: Stale PID file, overwriting.
Jul 22 05:57:48 marilyn-desktop pulseaudio[4190]: pid.c: Stale PID file, overwriting[/I].This noob would really appreciate any help that someone may give me. Thank you.

**NOTE: It's the version I'm currently on, 9.10 that I'm having trouble with & NOT 10.04 Sorry!**

---

### Post by kansasnoob on 2010-07-22
I'm curious about a few things so please post the output of the following commands:

```
uname -a
```

```
df -H
```

```
sudo apt-get -f install
```

That latter command might suggest removing stuff but wait until I see the results please. I'd also like to see your sources.list:

```
cat /etc/apt/sources.list
```

Maybe that'll give us some ideas.

---

### Post by Penny N. Nickels on 2010-07-22
> **kansasnoob said:**
> I'm curious about a few things so please post the output of the following commands:

```
uname -a
``````
df -H
``````
sudo apt-get -f install
```That latter command might suggest removing stuff but wait until I see the results please. I'd also like to see your sources.list:

```
cat /etc/apt/sources.list
```Maybe that'll give us some ideas.

I'm a real noob, so please explain how do I do those things.

**NOTE: It's the version I'm currently on, 9.10 that I'm having trouble with & NOT 10.04 Sorry!**

---

### Post by Nick_Jinn on 2010-07-22
There might be problems with upgrading from a now unsupported distro. Try downloading a new version and burn it to CD.


He is telling you commands for the terminal. Go to the start menu, find the terminal and open it....its like an app. Copy and paste those commands one by one. However, you cant use control V (They should change that I think). Use right click to paste.

---

### Post by kansasnoob on 2010-07-22
> **Penny N. Nickels said:**
> I'm a real noob, so please explain how do I do those things.

**NOTE: It's the version I'm currently on, 9.10 that I'm having trouble with & NOT 10.04 Sorry!**

It sounds like you can occasionally get booted into Ubuntu. If so just go to Applications > Accessories > Terminal, then just copy-n-paste the aforementioned commands.

---

### Post by Penny N. Nickels on 2010-07-22
> **kansasnoob said:**
> I'm curious about a few things so please post the output of the following commands:

```
uname -a
``````
df -H
``````
sudo apt-get -f install
```That latter command might suggest removing stuff but wait until I see the results please. I'd also like to see your sources.list:

```
cat /etc/apt/sources.list
```Maybe that'll give us some ideas.

The first command came back with this:

> Linux marilyn-desktop 2.6.31-22-generic #60-Ubuntu SMP Thu May 27 00:22:23 UTC 2010 i686 GNU/LinuxThe second command came up with :

> Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1               78G   9.6G    64G  14% /
udev                   261M   234k   261M   1% /dev
none                   261M   1.3M   260M   1% /dev/shm
none                   261M   287k   261M   1% /var/run
none                   261M      0   261M   0% /var/lock
none                   261M      0   261M   0% /lib/init/rwThe third command came back with:

> [sudo] password for marilyn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgsf-gnome-1-114 libavutil-unstripped-49 xchat-common
  linux-headers-2.6.28-11 xchat ttf-kannada-fonts libnotify-bin
  gnustep-back0.14 libass1 libgnustep-gui0.14 libmysqlclient15off libx264-65
  libgoffice-0-6-common linux-headers-2.6.28-11-generic libgnustep-base1.16
  ttf-telugu-fonts libffado0 tcl libgoffice-0-6 libphonon4 imagemagick-doc
  libffcall1 ttf-oriya-fonts libgmyth0 liblrdf0 gnustep-back0.14-art
  ttf-bengali-fonts qt4-qtconfig
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.The last command came back with:

> marilyn@marilyn-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverseAm I back to Jaunty? Or am I still Karmic? 

I am learning a lot today! MY HEAD HURTS! LOL! 

Let me know my next step, if any. Thank you for all your help!

---

### Post by Penny N. Nickels on 2010-07-22
I did a reboot to see if the login looped. It didn't loop. I've shut down the computer for a few minutes & turned it back on to see if the login looped. It didn't loop. 

I also decided to check the **Update Manager** since changes had been made. It did come up with a list but also a box popped up (not the dreaded one from before), suggesting that I should do only a partial install of the list. Should I install the partial list of updates suggested, or should I wait? (I did say that I was a noob!)

Once again, thank you for your help & guidance in this!

---

### Post by Penny N. Nickels on 2010-07-22
I might have started my celebration a little too soon because the login is back to looping. I didn't remove anything or added any updates. I'm back to clicking all of those things on the bottom again of the login screen to "help" login.

---

### Post by Penny N. Nickels on 2010-07-24
My login is back to always looping, but I'm no longer getting that one message box. 

> I also decided to check the **Update Manager** since changes had been made. It did come up with a list but also a box popped up (not the dreaded one from before), suggesting that I should do only a partial install of the list. Should I install the partial list of updates suggested, or should I wait? (I did say that I was a noob!)

It's a partial re-install. If I do, is that going to stop the looping? As always, thank you for any & all help I am given.

---

### Post by Penny N. Nickels on 2010-08-07
I'm not sure if one has anything do with the other, but there has been some updates recently &, since then, the looping no longer exists. As long as I'm not looping, I'm happy.

---

### Post by Nick_Jinn on 2010-08-08
Do you have problems with Wubi or with using linux in live CD mode?

If not, have you considered a clean install?

---

### Post by Penny N. Nickels on 2010-11-08
> **Nick_Jinn said:**
> Do you have problems with Wubi or with using linux in live CD mode?

If not, have you considered a clean install?

I'm not sure what you mean?

I have discovered something that has been keeping me from looping now. As odd as it may seem, it has to do something with the cursor. When I'm at the log in screen, after logging in, I move the cursor off of the screen. It then goes though the rest of the splash & then right to the desktop. I've done this repeatedly & it has worked every time. I have it set that I'm suppose to bypass the log in screen in the first place. I decided to try to move the mouse while the computer is booting up, hopefully not having the cursor on the screen. It has worked, too, taking me right to the desktop. I'm just curious if anyone can figure why that works. Is there something maybe wrong with my mouse or with cursor? I would love to hear thoughts about it. Thanks!

---

