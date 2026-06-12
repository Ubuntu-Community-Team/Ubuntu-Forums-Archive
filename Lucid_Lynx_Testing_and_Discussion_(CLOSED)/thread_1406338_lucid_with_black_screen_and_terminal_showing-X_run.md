---
title: "lucid with black screen and terminal showing-X running"
date: 2010-02-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lonniehenry on 2010-02-13
I installed karmic 386 on a p4 desktop machine and updated it. This is on a different machine than my sig machine.  When I got it running with no problem, I changed the sources to Lucid and did an update and upgrade.  It booted ok and did changes to get it. The next day I did the updates that came down.  I am running the original xorg.conf that came with the system.  Has Nvidia card but have done nothing to enable it. After the latest updates and with autologin, it boots and goes to a black screen with a terminal window in the top left corner.  When I try to do a startx in the terminal, it says x is already running.  I can't figure out how to make it actually show the desktop.  It appears to be running, but can't see it.
Any ideas on how to proceed.

---

### Post by ranch hand on 2010-02-13
If (a big if) you can boot through recover (text login then type "startx" at the next prompt) you should try to get rid of the auto login (if the gui will work).

Check this thread and join the bug what ever happens;

[http://ubuntuforums.org/showthread.php?t=1405340](http://ubuntuforums.org/showthread.php?t=1405340)

---

### Post by lonniehenry on 2010-02-13
Thanks ranchhand.  I can't get to a usable gui.  I am not running plymouth.  I would like to change autologin to password login, but can't get to the x that I know is running.

---

### Post by VMC on 2010-02-13
> **lonniehenry said:**
> Thanks ranchhand.  I can't get to a usable gui.  I am not running plymouth.  I would like to change autologin to password login, but can't get to the x that I know is running.

What I've done is chroot to the injured partition, then remove Plymouth, like so:

```
sudo aptitude purge plymouth
```

Then you should be able to boot again so you can remove autologin.
BTW-its 'gdmsetup', but it doesn't work witout gui for some reason. And the logical reason is gdm.

---

### Post by lonniehenry on 2010-02-14
I don't have plymouth installed as I purged it during one of the sessions that I got the terminal in the upper left hand corner.  X runs, but I can not see it.  I have tried booting in recovery, but arrive at a blank screen X running in background.  
I can't get any farther in trying to solve this.
Thanks for the suggestions.  I am thinking of reinstalling as I don't have anything on the machine.  I will not use autologin as that seems to be part of the problem. Any ideas about what else to do to avoid the problem.  I didn't even get to the part about using drivers for Nvidia.

---

### Post by VMC on 2010-02-14
> **lonniehenry said:**
> I don't have plymouth installed as I purged it during one of the sessions that I got the terminal in the upper left hand corner.  X runs, but I can not see it.  I have tried booting in recovery, but arrive at a blank screen X running in background.  
I can't get any farther in trying to solve this.
Thanks for the suggestions.  I am thinking of reinstalling as I don't have anything on the machine.  I will not use autologin as that seems to be part of the problem. Any ideas about what else to do to avoid the problem.  I didn't even get to the part about using drivers for Nvidia.

I think your main issues is with nVida. If you get the right driver installed that's half your battle.

---

### Post by dino99 on 2010-02-14
try to remove xorg.conf, don't need it now, then try to add "sevenmachine ppa" to synaptic repo, update and install 195 driver.
last step: system --> admin --> choose driver (or like), activate 195 then reboot.

note:
don't know how lucid run on p4, hope you have at least 1 mo ram on it. As it is an dist-upgrade with old things left behind (settings, broken links, ...), "bleachbit" might do some room and bring some breath to your p4.

---

