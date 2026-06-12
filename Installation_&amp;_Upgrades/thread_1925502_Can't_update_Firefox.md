---
title: "Can't update Firefox"
date: 2012-02-14
forum: Installation &amp; Upgrades
---

### Post by Ddeeff on 2012-02-14
Hi all!

A while ago I tried to update Firefox and failed. I ended up with two shortcuts in the xfce's menus both pointing to 5.0.1

So I've finally gotten up the willpower to try again. I searched online and found the following code somewhere:

```

sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get upgrade

```After trying this. the terminal appeared to be downloading and installing firefox as I was running it, which I thought was odd. So I tried quitting and restarting firefox, then rebooting then starting firefox, but to no avail: the 'About Firefox' window still says 5.0.1.

My theory is that Firefox has been downloaded and installed elsewhere on the system. So how do I (1) locate the updated firefox, (2) refer all my shortcuts to the new version and (3) delete an item from XFCE's menu?

(by the way, I'm a Linux newbie, so I originally installed Ubuntu, got annoyed with Unity and Gnome 3 and installed xfce. It is adequate enough for me. I don't know whether the thread should be [xubuntu] prefixed instead)

---

### Post by winh8r on 2012-02-14
You would be best to take a look here:

[http://ubuntuforums.org/showthread.php?t=1712247&highlight=firefox+mega+thread]("http://ubuntuforums.org/showthread.php?t=1712247&highlight=firefox+mega+thread")

this should help you out


EDIT**** please read through it all before doing anything!

---

### Post by Ddeeff on 2012-02-14
I have already tried there; the two options for me are manual and automatic installation

**[SIZE=2]Automatic installation[/SIZE]**
> You just need to do a regular update/upgrade to get the latest stable version
Yes, this hasn't worked for me for a while. I've tried using Ubunntu Software Centre, but there is no button to upgrade. I've tried Update Manager, but it's not in there - I've tried looking for a repository in there that might be unchecked but I can't find one.

**[SIZE=2]Manual installation[/SIZE]**
I hold reservations about doing this because I'm scared of deleting personal data such as preferences (I've changed a few about:config preferences)

---

### Post by ajgreeny on 2012-02-14
That firefox ppa repository is now not needed as the standard repos for all supported versions of ubuntu and othet *ubuntu family of OSs now contain firefox 10.01, so firstly I suggest you disable that ppa.

I think you then need to make sure you update the repos with ```
sudo apt-get update
```and finally try again to look for the version of firefox available to you.  Just to be sure everything is as it should be can you please run the commands ```
which firefox
whereis firefox
``` in terminal and report the output back here.  That may tell us if you have an unusual installation of the package due to a manual install at some time in the past.

PS:  Try using synaptic instead of software-centre.  It is a much better package manager, which you may need to install first.  I have never used the software-centre to update or install anything, as I find it too dumbed down for me.

---

### Post by Ddeeff on 2012-02-14
I have disabled that ppa already. Update Manager couldn't connect to it and, when that happens, Update Manager has a hissy fit and refuses to update anything.

'**which firefox**' reports:
> [FONT=Courier New]/usr/bin/firefox[/FONT]'**whereis firefox**' reports:
> [FONT=Courier New]firefox: /usr/bin/firefox /usr/bin/firefox.ubuntu /etc/firefox /usr/lib/firefox /usr/share/man/man1/firefox.1.gz[/FONT]As for Synaptic Package Manager, I believe that was removed from the Ubuntu by default because it can do scary things. I still have it though, I'm not extremely familiar with it.
I used the filter, for 'firefox' and found 8 packages installed, 2 of which are unsupported by Ubuntu. The key one of these is this one:

[LIST]
[*]firefox-mozilla-build, current version: 5.0.1, Latest version: 5.0.1
[/LIST]
As for the remaining 6 packages, they all refer to version 10.0.1, apart from a Totem related one (3.0.1) and xul-ext-ubufox (1.0.2)

---

### Post by ajgreeny on 2012-02-14
> **Ddeeff said:**
> I used the filter, for 'firefox' and found 8 packages installed, 2 of which are unsupported by Ubuntu:..... edit in progress
What were those?  Does 10.0.1 show at all?

By the way, synaptic does not "do scary things" in my opinion.  It gives you much more control over packages than other gui applications, and often shows packages that are not shown at all in USC.

---

### Post by Ddeeff on 2012-02-14
er... my apologies, I edited the message whilst you were replying

on scariness: I was voicing the opinion of Canonical, who removed Synaptic Package Manager from new installations of Ubuntu because a user could seriously damage their system using it. I think I read that somewhere; I could be wrong entirely.

---

### Post by Ddeeff on 2012-02-15
Bump
In Synaptic Package Manager...
> 
I used the filter, for 'firefox' and found 8 packages installed, 2 of  which are unsupported by Ubuntu. The key one of these is this one:

[LIST]
[*]firefox-mozilla-build, current version: 5.0.1, Latest version: 5.0.1
[/LIST]
As for the remaining 6 packages, they all refer to version 10.0.1,  apart from a Totem related one (3.0.1) and xul-ext-ubufox (1.0.2) 	

---

### Post by ajgreeny on 2012-02-15
I think that if synaptic is showing firefox-mozilla-build, it means that at some point you, or maybe someone else has installed a version 5.0.1 manually, not from the repos, though I could be wrong.

Anyway, if you have version 10.0.1 showing as well as 5.0.1 in synaptic, I suggest you mark version 5.0.1 for complete removal, and then mark version 10.0.1 for installation, assuming you actually have version 10.0.1 of firefox itself showing as available.

I am still baffled as to why you have had this problem at all, as it should not happen in a normal *ubuntu family OS installation, whichever DE you are using.

**EDIT:**
Can you check if you are using now, or have used in the past the **ubuntuzilla** repositories, as that wopuld account for the firefox-mozilla-build being installed on your system.  If ubuntuzilla is enabled, disable it and remove your current firefox 5.0.1, as I suggest above, then use the standard ubuntu repos to install 10.0.1.

---

### Post by Ddeeff on 2012-02-15
Won't user related files, preferences, history, etc be deleted if I uninstall 5.0.1?

---

### Post by ajgreeny on 2012-02-15
They are all in your /home/user folder or partition, so they are left exactly as they were, totally untouched in any way.

---

