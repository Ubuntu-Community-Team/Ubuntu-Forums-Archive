---
title: "Ubuntu 11.04 upgrade install fail on Dell Optiplex GX-620"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by markling on 2011-05-01
Attempted upgrade by two methods, both using downloaded CD ISO:
1. Upgrade over existing 10.10 installation
2. Clean install, erasing over previous install.

1. Upgrade install failed with the following errors:
----------------------------------------------------

a.
Could not updata ICEauthority file /home/[user]/.ICEauthority

b.
There is a problem with the configuration server (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

c.
Nautilus could not create the following folders:
/home/[user]/Desktop, /home/[user]/.Nautilus
Before running Nautilus please create these folders, or set permissions such that Nautilus can create them.

WHAT THEN HAPPENED: Ubuntu asked for an encryption passphrase, then went to blank purple splash screen with no other visible icons or features. Then nothing. On reset, the same happens: same errors, repeated request for encryption passphrase and repeated fail on purple splash screen.

2. Clean install failed with same errors and result as described above for the attempted upgrade install.

I reverted to Ubuntu 10.10, which works fine.

CONSEQUENCES
-------------
I've wasted another bank holiday weekend trying to upgrade the latest version of Ubuntu.

The same happened last year, when I tried to upgrade on the machine I was then using:

[http://ubuntuforums.org/showthread.php?t=1498312](http://ubuntuforums.org/showthread.php?t=1498312)

SUGGESTIONS FOR CANONICAL
--------------------------

1. Don't release it if its not ready

2. Clearly specify the makes/models of machine on which the upgrade can been attested to work

3. Clearly specify the makes/models of machine on which the upgrade can be attested to fail

4. Clearly specify the makes/models of machine on which the upgrade has not been tested 

5. Preferably automate the detection of attested hardware at start of installation and allow user to abort and preserve machine in previous state if make/model is one of instances 3. or 4. above.

6. Recruit more beta testers.

7. At the very least, get it working on Dell machines. It's not like Dell's an uncommon make, is it?

---

### Post by ktz84 on 2011-05-02
On the log on screen do you have any desktop sessions that you can choose from?

I didn't and got the same error. I had to manually install gnome through the terminal (Ctrl - Alt - F2), logged in and ran:

sudo aptitude install gnome

and said yes to everything. Lots of packages and over 100mb of downloads required but I'm now up and running.

This may or may not resolve your issue.

---

### Post by markling on 2011-05-02
Thanks. Didn't run through terminal. Ran it by booting from the CD. I'm back on 10.10 now. And that's where I'll be staying. I only have so much time to spare.

---

### Post by frysianDjohn on 2011-05-08
I have solved this problem through the following steps.

step 1.
```
sudo chmod 775 /etc/gconf/gconf.xml.system
```

step 2.
```
sudo chmod 775 /tmp/
```

as found [here]("https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215").

With this the problem wasn't solved, yet. So, after this I've tried to update my system trough the terminal by hitting ctrl+alt+t when you login though the GUI (instead of using the command line interface before you login by hitting ctrl+alt-F2 this would not happen in my case. But in both cases you should enter the following lines:

```
sudo apt-get update
```
this will let you know that there is a problem with the package manager which will be fixed by entering the line of code, it will give back something like this.
```
sudo dpkg --configure -a
```

reboot the system by enter
```
sudo reboot
```

this should solve the errors.

---

### Post by Quackers on 2011-05-08
I'm sorry that you are having problems (and that you did last year too), but really the possible causes are myriad. And in fairness this

"SUGGESTIONS FOR CANONICAL
--------------------------

1. Don't release it if its not ready

2. Clearly specify the makes/models of machine on which the upgrade can been attested to work

3. Clearly specify the makes/models of machine on which the upgrade can be attested to fail

4. Clearly specify the makes/models of machine on which the upgrade has not been tested

5. Preferably automate the detection of attested hardware at start of installation and allow user to abort and preserve machine in previous state if make/model is one of instances 3. or 4. above.

6. Recruit more beta testers.

7. At the very least, get it working on Dell machines. It's not like Dell's an uncommon make, is it?"

is just so completely ridiculous that it's funny.

I hope you solve your problems.

---

### Post by markling on 2011-05-14
Thanks frysianDjohn. I will surely use your advice if I get another opportunity to try the upgrade before the next release. But it is unfortunate that one cannot spare the time for these things often.

Quackers, the possible causes are indeed myriad. And thanks for your good wishes, but I solved my problem by abandoning my attempt to upgrade to 11.04.

I can have a good laugh about it now as well, but my suggestions are not at all ridiculous. They are a perfectly good idea because the of the myriad problems one can imagine a non-MS operating system has with underlying hardware.

A similar problem occured again recently when trying to install Ubuntu on the computer of someone I know who was getting fed up with XP. The install didn't work. I wasted a lot of time, gave up and put XP back on it.

You can read all about it here: [http://ubuntuforums.org/showthread.php?t=1737815](http://ubuntuforums.org/showthread.php?t=1737815)

Now please note I'm still here. And consider what an enourmous service Canonical would do by providing a little information about those machines on which it has tested before release, presuming that is indeed what it does.

---

### Post by MickG01 on 2011-05-18
I'm running on an Optiplex GX-620 But having burnt CDs and DVD with Natty and so far none of them will run from CD/DVD so I'm very doubtful about doing the Upgrade.

When booting from CD and selecting the 'Try' option it goes to BusyBox and shows "cannot mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem/squashfs

But something has happened as now whenever Update Manager appears it immediately asks for the Ubuntu 11:04 CD if I select to install the updates.

---

