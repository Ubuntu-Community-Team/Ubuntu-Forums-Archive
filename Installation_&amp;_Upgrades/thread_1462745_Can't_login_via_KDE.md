---
title: "Can't login via KDE"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by alaren on 2010-04-26
So, I just ran the auto-updater to try the 10.04 RC.

Everything appeared to work fine, and I rebooted and got to the login screen with no problem.

However, when I type my password, I see a white window appear briefly, then a black screen, then I get dumped back to the login screen.  Removing home/.kde does not solve the problem.  Creating new users and logging in with them results in the same symptom.

The only solution I've found is to log in via console, then run "startx."  It brings me into KDE and all is well.

I don't even know where to begin fixing this.

---

### Post by Lampi on 2010-04-26
kdm has it's own logfile in /var/log/kdm - try having a look what's going on in there

---

### Post by alaren on 2010-04-26
This is what appears in that log file:

(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 25 23:34:54 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
QFont::fromString: Invalid description 'Serif,20,5,0,50,0'
QFont::fromString: Invalid description 'Sans Serif,10,5,0,50,0'
QFont::fromString: Invalid description 'Sans Serif,10,5,0,75,0'
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /tmp/0518865195/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
QFont::fromString: Invalid description 'Serif,20,5,0,50,0'
QFont::fromString: Invalid description 'Sans Serif,10,5,0,50,0'
QFont::fromString: Invalid description 'Sans Serif,10,5,0,75,0'
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /tmp/1298455037/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
 ddxSigGiveUp: Closing log

It's all Greek to me, any help would be appreciated. d^_^b

---

### Post by Pavlo Solntsev on 2010-05-03
$ sudo apt-get install ibus 
$ibus-daemon -d

Check your log. Ibus daemon is not running. I think it is bug. I have got problem also with dragon and kaffeine players. I reported that bug.

Best.

---

### Post by Mr. Wishes on 2010-05-07
I have been getting the same problem. Installing and running ibus doesn't seem to have helped at all. I've tried logging in with a brand new user account in case some of my configuration files were wrong, but no luck. My kdm.log looks much like the one posted above.

At the moment I have more-or-less unusable system, so any help would be appreciated.

Edit: I should mention that I'm using the full release, not the RC as above.

---

### Post by Bios Element on 2010-05-07
Exact same problem here. Kubuntu is totally unusable for me now.

---

### Post by Mr. Wishes on 2010-05-07
More information:
I can't login with startx either - though there are no errors reported, it just gets killed at the same point.

According to apt-get, there is one package that is held back - kdegraphics-strigi-plugins.

I've tried installing gdm so that I can use my computer, but that's been a failure too, I can't choose a gnome session from the login manager, and choosing the kde session results in a black screen.

---

### Post by Bios Element on 2010-05-07
So has anyone filed a bug on this? Judging from a few searches, no one has actually found a solution to this problem.

---

### Post by gasdia73 on 2010-05-11
Same problem here, I think people who upgraded are all stuck with this problem...

---

### Post by Zorael on 2010-05-11
And all packages look okay otherwise?
```
$ sudo dpkg --configure -a
$ sudo aptitude update
$ sudo aptitude full-upgrade
```
The logs to check are **/var/log/kdm** (as mentioned above) as well as **/var/log/Xorg.0.log**. That Xorg.0.log file refers to the currently running session, so if you have X at the login screen you'll have to look at the last log instead; **Xorg.0.log.old** in the same directory.

---

### Post by surfingthewind on 2010-05-16
Hi, all. I have the same problem after upgrading to Kubuntu 10.04
On login (often but not always), I type my password and after some time login windows disappear and reappears again. I often have to restart X to be able to login.

Once I'm logged in, I have the same problem on screen unlocking. I can unlock only by typing passwd and clicking return button more than once.

The only error present in kdm.log is:
------------------------------------------------------------
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch 
failed: No such file or directory
QFileSystemWatcher: failed to add paths: /tmp/1500275922/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address.
IBusInputContext::createInputContext: no connection to ibus-daemon
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /tmp/1077755098/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address.
IBusInputContext::createInputContext: no connection to ibus-daemon
 ddxSigGiveUp: Closing log
-------------------------------------------------------------


Surfingthewind

---

### Post by stigman13 on 2010-05-22
I have this same problem as this post and haven't found any solutions, do the others in this post still have this problem or has a fix been found?

---

### Post by stigman13 on 2010-05-22
I got by my kde problem. I orginally loaded kubuntu 10.04 with an ATI radeon X1600 pro, had install issues with the video freezing even though my PC sounded like it was still doing something. I removed this video card and re-installed 10.04 with the on board crappy video and everything installed and displayed correctly. I then had a login looping issue which I tried several suggestions from this forum which just ended up with the problem in this post, but didnt see any logs with video errors. Without any other suggestions and seeing posts how video cards can cause this problem, I decided to put a nvidia geforce video card I had laying around and everything started working.

---

### Post by ilya.kasnacheev on 2010-06-10
I've found a solution. In my case, mysql-server-5.1 was obliterating kdebase-workspace-bin

Try sudo apt-get install kdebase-workspace-bin and there are chances that it'd work.
Spread it if it works.

---

### Post by metrofun on 2010-07-05
The same problem after fresh install of Kubuntu 10.04, can't find solution

---

### Post by metrofun on 2010-07-05
I've tried to install Kubuntu 10.10 and Kubuntu 10.04 the same thing - can't login...it may be hardware specific.I have old integrated intel graphic card.

---

### Post by metrofun on 2010-07-07
I tried to use descret video card and everything is ok.Seems it's a problem with my integrated card
VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)

---

### Post by metrofun on 2010-07-07
I found a solution on russian forum ([http://www.linux.org.ru/forum/general/5060498](http://www.linux.org.ru/forum/general/5060498))
Add to the .kde4/share/config/kwinrc (.kde/share/config/kwinrc)

[Compositing] 
Enabled=false

---

