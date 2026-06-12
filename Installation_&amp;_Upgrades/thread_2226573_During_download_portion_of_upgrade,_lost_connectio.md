---
title: "During download portion of upgrade, lost connection"
date: 2014-05-28
forum: Installation &amp; Upgrades
---

### Post by Samuel_Vivian on 2014-05-28
I lost my internet connection during the download portion of a do-release-upgrade from Saucy to Trusty. Now, I can't restart the upgrade because my system "thinks" it's already running trusty. So far as I know, no actual upgrades happened, as there was still about 20% left in the download phase. I'm assuming this is just a case of editing the right file so the system "realizes" it still needs to finish the download and can then kick off the actual install process, but I don't know what file or files need to be fixed.

---

### Post by Bucky Ball on 2014-05-28
Welcome. Could you open a terminal and post the result of:

```
uname -a
```

Also, what happens when you issue these three commands, one at a time:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Please post ANY errors it spits out.

---

### Post by Samuel_Vivian on 2014-05-28
uname -a gives this:

> Linux svivian 3.11.0-20-generic #34-Ubuntu SMP Tue Apr 1 20:40:25 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux



Well, burn my biscuits.

I did an update, and a dist-upgrade prior to posting this, and it updated just a couple of files but no errors. It honestly never occurred to me to try just apt-get upgrade.

That resulted in listing a whole bunch of files (the new version, I guess) being listed as "held back", and it seems to be processing it. Let me see what happens, and I'll update shortly.

---

### Post by Samuel_Vivian on 2014-05-28
Well, fingers crossed. I ran the apt-get upgrade, and it first killed lightdm and left the whole thing hanging. I logged in to another tty session, launched x to try to see if I could see where things were, and ended up re-running apt-get upgrade. That seemed to complete the upgrade process, and I was able to reboot (apparently) successfully. I'm going to knock it around for a bit and see if everything ended up where it is supposed to be.

---

### Post by Samuel_Vivian on 2014-05-28
Oookay. So, the upgrade ran. And there was still a big wadge of files "held back", so I run apt-get dist-upgrade and the system tries to install. However, the install fails, and here's why:

I removed Unity on the "saucy" version of my system. Now it looks like the system is trying to get Unity back in. I put in Gnome-shell, which uses version 3.10 of the gnome-settings-daemon, and Unity doesn't want that version. Guess I get to see how good Canonical's software repair utilities work

Edited to add: The upgrade is trying to put in the new package unity-settings-daemon, which wants gnome-settings-daemon to be a version greater than or equal to 3.8, but less than 3.10. Since I don't have Unity installed, I'd assume that I don't need this daemon. Is there a way to run the dist-upgrade so it excludes that file? That's all that seems to be holding up the works at the moment.

---

### Post by Samuel_Vivian on 2014-05-29
Update: 
I purged the files causing the problem, then did an autoclean to remove all the previously downloaded packages. I set unity-settings-daemon and gnome-settings-daemon-schemas to held with dpkg, but apt is still trying to install them, and I am now right back in dependency hell as unity-settings-daemon can't accept the newer version of gnome-settings-daemon-schemas that's already installed. Is there any way to salvage this at this point? Or am I just going to have to do a fresh install because apt doesn't bother to check with dpkg before going Leeroy Jenkins on the upgrade?

---

### Post by Samuel_Vivian on 2014-05-29
Well, since I can't have this machine down (or half-hosed in this case), I'm gonna "solve" this by wiping and doing a fresh install. Ugh.

---

### Post by Samuel_Vivian on 2014-05-29
Well, since I can't have this machine down (or half-hosed in this case), I'm gonna "solve" this by wiping and doing a fresh install. Ugh.

---

