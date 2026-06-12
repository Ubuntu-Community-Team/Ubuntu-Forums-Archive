---
title: "Greeter crash"
date: 2008-07-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2008-07-03
I've just dist-upgraded from hardy to alpha1 this morning and no my system boots normally but after briefly showing the egg timer equivilent circle thingie (does it have a name??) it displays 'the greeter application has crashed, attemting to use another' and after clicking ok it loops.

I've done a little research and it appears this fault normally occurs after logging in, not before. So I'm assuming the cause this time is different to the one most have encountered and their fixes don't work.

So it's either re-install time or I'm running on a live disc until it's fixed! I did see on here someone post a method of installing updates to your system whilst running off cd, anyone care to jog my memory?

Thanks

---

### Post by plun on 2008-07-03
Use a tty terminal and check if everything is installed.

Swith over to a tty from the login screen

Ctrl-Alt-F1

Login to tty

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Maybe repairing command is needed, read messages.

Ctrl-Alt-Del for PC restart or Ctrl-Alt-F7 for returning to login.

:)

---

### Post by macroshaft on 2008-07-03
Running the command resulted in an error

> Could not open lock file /var/lib/dpkg/lock - open (13 permission denied)

Unable to lock the administration directory (/var/lib/dpkg/), are you root?


Very intriguing....

---

### Post by PmDematagoda on 2008-07-03
You might need to remove that lock file with:-
```
sudo rm /var/lib/dpkg/lock
```
and then try plun's commands again.

---

### Post by meborc on 2008-07-03
> **plun said:**
> Use a tty terminal and check if everything is installed.

Swith over to a tty from the login screen

Ctrl-Alt-F1

Login to tty

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Maybe repairing command is needed, read messages.

Ctrl-Alt-Del for PC restart or Ctrl-Alt-F7 for returning to login.

:)

yeah, you might need to run either **sudo apt-get -f install** or **sudo dpkg --configure -a** to correct any problems with updates...

the only thing i would do differently from plun's advice is that i would stop gdm before upgrading... i guess it does not matter, but it feels a bit better :) if you know what i mean

so CTRL+ALT+F2, log in, then stop gdm **sudo /etc/init.d/gdm stop**, then dist-upgrade and repare if needed, then exit, then ALT+F7 (no need to use CTRL+ALT+F7 as you move just by ALT+FX)

EDIT: stupid me :) i forgot that you need to start gdm again before exiting F2... so just **sudo /etc/init.d/gdm start**

---

### Post by macroshaft on 2008-07-03
when removing the lock as advised apt-get update results in tons of the following errors

> W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'


as does attempting to install updates from a live cd.

I'm now going to try the -f install and dpkg configure commands.

---

### Post by macroshaft on 2008-07-03
apt-get -f install removed several packages
libakonadiprivate0
libqimageblitz4
kdepimlibs5
libqca2-pluginossl
kdepimlibs-data

dpkg --configure -a gave no output
no change in the symptoms

---

### Post by MacUntu on 2008-07-03
I installed xdm but no success. I can't read all the output because my Virtual PC install only shows crap on the terminals. :(

---

### Post by plun on 2008-07-03
> **macroshaft said:**
> apt-get -f install removed several packages
libakonadiprivate0
libqimageblitz4
kdepimlibs5
libqca2-pluginossl
kdepimlibs-data

dpkg --configure -a gave no output
no change in the symptoms

check a dist-upgrade again followed with a

```
sudo apt-get install ubuntu-desktop
```

But... are you running Kubuntu :confused:

---

### Post by macroshaft on 2008-07-03
No, I'm not running kubuntu and I'm fairly certain the system does not connect to wireless whilst at the command line (I can't use a wired connection)

I've had to re-install to get something done so this will bug me indefinately now!!

---

### Post by psyke83 on 2008-07-03
> **macroshaft said:**
> No, I'm not running kubuntu and I'm fairly certain the system does not connect to wireless whilst at the command line (I can't use a wired connection)

I've had to re-install to get something done so this will bug me indefinately now!!

Too bad you didn't see this guide before reinstalling: [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

NetworkManager isn't vital to get wireless working.

---

### Post by PmDematagoda on 2008-07-03
> **macroshaft said:**
> No, I'm not running kubuntu and I'm fairly certain the system does not connect to wireless whilst at the command line (I can't use a wired connection)

I've had to re-install to get something done so this will bug me indefinately now!!

But you do realise that you were trying to upgrade to a Development version of Ubuntu didn't you? And that crashes/problems are to be expected due to Intrepid still being in Alpha 1.

---

### Post by supenguin on 2008-07-06
> **PmDematagoda said:**
> But you do realise that you were trying to upgrade to a Development version of Ubuntu didn't you? And that crashes/problems are to be expected due to Intrepid still being in Alpha 1.

I'm having the exact same problem as the original poster. I do expect there to be problems with an Alpha release, I didn't expect them to keep me from even logging into my desktop!

I tried a clean install of Intrepid and got the greeter crashed error.  Then I tried a fresh install of Hardy and an upgrade and got the same results.  I've tried all the work-arounds mentioned in this thread and it all gets me the same place: no error messages, no packages added, updated, or removed.

The only thing I haven't been able to figure out: I'm running the Alpha inside Parallels so I'm not sure if this is a Ubuntu bug or just some bad interaction with Parallels.

My work-around for now: switch over to the other terminal as you have described and do chmod 444 on /etc/init.d/gdm  This keeps it from starting up when the system boots.  If I want to try to start it up to see if the issue is fixed I can run

sudo bash /etc/init.d/gdm start

---

### Post by Raptor45 on 2008-07-06
> **supenguin said:**
> I'm having the exact same problem as the original poster. I do expect there to be problems with an Alpha release, I didn't expect them to keep me from even logging into my desktop!

That shouldn't be unexpected. Anything goes in an alpha.

---

### Post by macroshaft on 2008-07-07
psyke83, thanks for that. I knew it would be possible, I just didn't know if it worked by default or how to set it.

PmDematagoda, yes I do realise it's an alpha release but knowing that doesn't make the faults go away! I use it to learn more about the system and don't worry because in a worst case scenario a re-install is a walk in the park.

supenguin, running a test release is like living in a house that hasn't been built yet. You do expect to get wet and cold as they lay the bricks around you. You will get locked out of your system, the trashcan will stop working, openoffice will go mental and just about any other feature, however routine can and will break. If you want to test it use a second system which does not contain any valuable data.

---

