---
title: "lightdm won't start please see errors listed"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by petermg on 2012-04-26
Just upgraded from 11.10 to 12.04.  Machine is a netbook LT4004u, made by Gateway.  11.10 was working great, no problems.  After upgrading here is my issue, seems lightdm won't start correct, so basically I have no X session.  Here is what I've tried.

When going to tty1 I type ```
sudo lightdm
``` and an xsession tries to start, or so it seems, but when I go back to tty1 I see ```
** (lightdm:1313): WARNING **: Could not get accounts proxy: Error calling StartServiceByName for org.freedesktop.Accounts: GDBus.Error:org.freedesktop.DBus.Error.Spawn.PermissionsInvalid: The permission of the setuid helper is not correct

 ** (lightdm:1313): WARNING **: Could not get accounts proxy: Error calling StartServiceByName for org.freedesktop.Accounts: GDBus.Error:org.freedesktop.DBus.Error.Spawn.PermissionsInvalid: The permission of the setuid helper is not correct
```

Yes it shows twice for some reason.

Oh and even though at tty1 is says I'm using 12.04, on the tty7 where the Xsession usually runs, it says Ubuntu 11.10!?  Is it possible my upgrade didn't fully take??????  It said it was ready to reboot, it didn't give me any errors during the update/upgrade...?

Oh and when I do a ```
lightdm --test-mode
``` I get ```
Failed to get D-Bus connection
```

---

### Post by Toz on 2012-04-26
The command should be:
```
sudo service lightdm restart
```

And lightdm log files can be found at /var/log/lightdm. There might be some clues there as to why its not starting.

---

### Post by petermg on 2012-04-26
Ok well I ran dpkg --configure -a and now I'm able to get into lightdm no problem but seems like none of my programs come up when I click on the search and start typing.... nice.  I have a feeling this is going to be a learning experience.  I have my shortcuts on my launcher, but if I type oh say "term" in the search area, it says "Sorry, there is nothing that matches your search."  What gives?

---

### Post by Toz on 2012-04-26
Does:
```
unity --reset &
```
...fix that issue? If you don't have a terminal on the dash, you can start one with Ctrl+Alt+T.

---

### Post by chrb on 2012-04-27
Maybe your upgrade didn't complete?

Try 'apt-get install -f'

---

### Post by jdthood on 2012-04-27
Thanks for the suggestion.  I had the same problem --- lightdm wouldn't start --- and on trying "apt-get -f install" I discovered that scores of packages had yet to be upgraded.  The upgrade process had aborted early because /var/lib/dpkg/status had become corrupted by a badly formatted Description field in a third-party package.

---

### Post by rgm3 on 2012-04-29
> **jdthood said:**
> Thanks for the suggestion.  I had the same problem --- lightdm wouldn't start --- and on trying "apt-get -f install" I discovered that scores of packages had yet to be upgraded.  The upgrade process had aborted early because /var/lib/dpkg/status had become corrupted by a badly formatted Description field in a third-party package.

Thanks for sharing.  Same thing happened to me.  My lexmark printer driver had a malformed description line in two files, /var/lib/dpkg/status and /var/lib/dpkg/available.  When i fixed those, i was able to continue installation.

---

### Post by afrodeity on 2012-05-05
me too, a few packages including lexmark printer had malformed description lines for some reason.

---

### Post by shahverdy on 2012-09-11
same problem here :(

---

### Post by molhokwai on 2012-10-27
Hello all,

Just wanted to say Thank you: Issues solved: Sound cards, external drives mounts, and display back... (all systems nominal)
It was all because of an interrupted update.

Here is the fix process:

```
    >sudo apt-get -f install

```
    ...asked for:

```
    >sudo dpkg --configure -a

```
    ...completed. Then:

```
    >sudo apt-get -f install

```
    ...optionally asked for:

```
    >sudo apt-get autoremove

```
    .And finally:

```
    >sudo /etc/init.d/lightdm restart

```
    Fixed the issues...

Thanks again, all.

---

### Post by yujiangang1025 on 2013-09-07
I did the same thing as you suggested, but the problem is still there

---

### Post by mingiwu on 2013-11-10
I have the same problem. I checked out log files:  [FONT=courier new]/var/log/lightdm/lightdm.log[/FONT] and [FONT=courier new]/var/log/lightdm/x-0.log[/FONT]
then I knew the problem comes from [FONT=courier new]/var/lib/lightdm/.Xauthority [/FONT]
I solved this problem by removing [FONT=courier new]/var/lib/lightdm[/FONT] and reinstall [FONT=courier new]lightdm[/FONT]. (It will create a new [FONT=courier new]/var/lib/lightdm[/FONT] directory.)
I also have to delete the ~/.Xauthority or I can't login from greeter.

---

