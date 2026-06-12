---
title: "Software Updater 14.LTS: Blank page in Trusred Software Providers"
date: 2015-04-04
forum: Installation &amp; Upgrades
---

### Post by MikeMecanic on 2015-04-04
Not able to restore defaults.  That problem appear after moving from 15.04B2 alone to 14.04.2 LTS with VM Ware running on 15.04B2.  Try to change server (main, US, clone...) and still get an empty page on trusted software providers.  Is there a way to restore to default setting?  Software updater seem to work correctly and I'm able to do it in the terminal. [FONT=Ubuntu Mono]sudo apt-get update && apt-get upgrade[/FONT]

But I get this error at the end:
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by deadflowr on 2015-04-04
Well, first what are the lines in the file /etc/apt/sources.list?
and the command sudo apt-get update && apt-get upgrade, are two different commands, so you need sudo in the second command as well.

---

### Post by MikeMecanic on 2015-04-04
When I click on the file (sources.list) it open software & updates.  Plus if I do sudo apt-get upgrade I get the same message: [COLOR=#000000]E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)[/COLOR]
[COLOR=#000000]E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

[/COLOR]

---

### Post by deadflowr on 2015-04-04
you can read the file using the gedit text editor >> open file system(or Computer) > etc > apt > sources.list. 
or
```
gedit /etc/apt/sources.list
```
As far as if using sudo apt-get upgrade still returns the lock message, do you have any package management programs open, like the software updater or software center, or any other?

---

### Post by MikeMecanic on 2015-04-04
Get this result and the file sources.list.save open (the one beside sources.list). And no nothing is open.  The file that open got a long list...
gedit /etc/apt/sources.list


(gedit:3470): Gtk-WARNING **: GtkScrolledWindow 0x1443880 is mapped but visible child GtkScrollbar 0x144acc0 is not mapped
(gedit:3470): Gtk-WARNING **: GtkScrolledWindow 0x1443880 is mapped but visible child GtkScrollbar 0x144acc0 is not mapped

Also, I'M able now to do **sudo apt-get upgrade.**

---

### Post by deadflowr on 2015-04-04
Seems like you're running into this bug
[https://bugs.launchpad.net/ubuntu/+source/overlay-scrollbar/+bug/1086494](https://bugs.launchpad.net/ubuntu/+source/overlay-scrollbar/+bug/1086494)
I haven't seen it personally, so cannot comment further.

You can also look at the file using the terminal command, cat.
```
cat /etc/apt/sources.list
```
but for naught probably, when you run the sudo apt-get update command, only the update not the upgrade command,
are there any error lines?
Or does it output normally, or as normal as one would expect.

---

### Post by MikeMecanic on 2015-04-04
Both are normal now: sudo apt-get update and sudo apt-get upgrade.  For the last commandline, it is not realy helpful.  Each time I install third-party software (codecs) during installation, I get bugs like that one.  Also, I install VM Ware and the pc runs slower even when it's not open.   Planning to reinstall it...

---

### Post by MikeMecanic on 2015-04-04
Just remove software updater and replcae it by Muon Update Manager.  The missing list is in Muon : see sceenshot

---

### Post by deadflowr on 2015-04-05
My apologies.
I was hung up on the apt-get/lock problem i forgot the initial problem.

My best guess is that the gtk libraries on the system are causing you problems.
The empty window
The gtk warning trying to run gedit
Lead me to think something's amiss with them, at the very least.

(Muon uses the qt libraries, which are typical of kde apps, so that's probably why the windows render properly there.)

I was confused by the statement 
> That problem appear after moving from 15.04B2 alone to 14.04.2 LTS with VM Ware running on 15.04B2
Which is the main system.
15.04 or 14.04?
Do you mean you have 15.04 as the host with a vm of 14.04, or vice versus, or neither?

Any extra info or clarifications could be helpful to figuring out how to best solve the overall problems at hand. 
(or not, it's your system, if you feel you can live with whatever problems it has, you are totally free to do so)

---

