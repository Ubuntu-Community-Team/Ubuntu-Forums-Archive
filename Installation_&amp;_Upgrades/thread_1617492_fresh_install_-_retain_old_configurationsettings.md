---
title: "fresh install - retain old configuration/settings"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by newboyo on 2010-11-09
Hi all,
 
I use karmic 64 bit (dual boot with win 7 - rarely used though :)) with separate / and ~ partitions. 
 
I've set up this box just perfectly for my needs and am scared of losing my customisations. I would like to reinstall 10.04 LTS with an encrypted ~ partition. 
 
If I were to 
1. backup ~ and /etc
2. install 10.04 with encrypted ~
3. copy files/folders from backupped ~ and /etc into the new system
 
would I be able to retain the configurations and settings? 
 
I don't have the energy to redo the box, if I lose the customisations, so seek assistance/guidance from the knowledgeable folk in the forum.

---

### Post by dino99 on 2010-11-09
if your actual installation have /home partition (you should), all your tweaks are safe when upgrading/reinstalling because only / (root) is affected

---

### Post by newboyo on 2010-11-09
> **dino99 said:**
> if your actual installation have /home partition (you should), all your tweaks are safe when upgrading/reinstalling because only / (root) is affected
 
Thanks for looking at my post. 
 
I'd need to format existing ~ while upgrading to 10.04 , to be able to encrypt it using LUKS. After which I plan on copying files/folders from the backed up ~ to the new encrypted ~.
 
What should I do to retain my configurations/packages/tweaks etc.

---

### Post by dino99 on 2010-11-09
you'd better to start from scratch then recreate the config/settings you want.

Anyway each time you change distro, packages changes, default settings often change, new dependencies are created, other are removed, applets are often hugely modified.

That mean your old/previous settings might conflicts, brings errors and so on; i suppose that recreating a custom config is easier than fighting bugs around.

---

### Post by newboyo on 2010-11-09
Thanks vm, Dino
 
From the debian reference manual -
 
**_Quote_**
6.4.9 Record/copy system configuration
To make a local copy of the package selection states: 
# dpkg --get-selections "*" >myselections # or use \* 
# debconf-get-selections > debconfsel.txt"*" makes myselections include package entries for "purge" too. 
 
You can transfer this file to another computer, and install it there with: 
# dselect update # debconf-set-selections < debconfsel.txt 
# dpkg --set-selections <myselections 
# apt-get -u dselect-upgrade # or dselect install
**_Unquote_**
 
In your opinion, could I reinstall the new distro, run the above files and then copy files/folders from the backup ~ into the new ~.
 
Rgds
 
New

---

