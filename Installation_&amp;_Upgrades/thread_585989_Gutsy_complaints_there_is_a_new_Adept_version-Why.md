---
title: "Gutsy complaints there is a new Adept version-Why?"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2007-10-21
Hi,
I'm on a fresh installed Kubuntu Gutsy (7.1/ 386), which, among others, contains Adept ver 2.1 (over KDE 3.5.8). Every day, the system notifies me about new updates which I download and install via Adept. (these updates do NOT include a new Adept version). At the end of the process, I get (every time) a message notifying me that there is a "new distribution version" and offers me to install it-which I decline (I just installed the new distribution, didn't I?).

Can somebody explain what's going on and how to get rid of that message?


Thanks


Michael Badt

---

### Post by ezak on 2007-10-21
Try running:

sudo update-manager -c -d 
 
If anything shows up then install the latest packages. 

If u still have problems, then run:

sudo apt-get update

sudo apt-get upgrade

sudo apt-get dist-upgrade

*If you still have the same message then finally follow these steps:

   1.   Open the Adept Manager by going to KMenu -> System -> Adept  Manager (Manage Packages)
   2. In Adept, go to Adept -> Manage Repositories
   3. Enable the "Recommended updates" and "Pre release updates" repository, close and reload
   4. If your system is up to date, the upgrade wizard will be offered after you click "Fetch Updates" via the "Version Upgrade" button.
         
1. Press the Full Upgrade button
2. Press the Apply Changes button
3. Once the packages are installed, exit the Adept Manager (Adept -> Quit)
4. Repeat the initial steps (1 - 3)

---

### Post by PacketCollision on 2007-10-21
Unless I'm mistaken, Adept calls things like a new kernel, or other major upgrades a "new distrobution version".  This is the same as doing "apt-get dist-upgrade" on the commandline, and it generally a good idea.  I would not follow ezak's instructions to enable "Pre Release Updates" though, unless you *like* having potentially broken packages installed.

---

### Post by opm8 on 2007-10-22
> **PacketCollision said:**
> Unless I'm mistaken, Adept calls things like a new kernel, or other major upgrades a "new distrobution version".  This is the same as doing "apt-get dist-upgrade" on the commandline, and it generally a good idea.  I would not follow ezak's instructions to enable "Pre Release Updates" though, unless you *like* having potentially broken packages installed.

Uhh, Step 3 of the "official" upgrade method is to enable the "Recommended updates" and "Pre release updates."  What that means is anyone's guess since it also leaves behind this line in /etc/apt/sources.list: deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe

Adept is very broken, basically and I wish the "official" method didn't rely on it.

opm8

---

### Post by mibadt on 2007-10-23
Thanks all!
I'll follow your recommendations.

Michael Badt

---

