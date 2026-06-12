---
title: "HELP! Installation stuck totally!"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by PooingCavy on 2007-10-21
Um, the installation totally stuck, and I don't know what to do.

---

### Post by gregbzh on 2007-10-21
You need to tell us a little more about what you get on your screen while trying to install.  At what stage do you get stuck and what do you see?

---

### Post by ede1005 on 2007-10-21
i came to a similar situation. i was using tomboy notes while the update manager was downloading the files. i tried to print my notes to a .pdf and everything froze with the exception of the  download manager. after all the downloading finished, it started installing some of the updates but stopped completely when a dialog box popped up prompting me to click "next" to start a part of the installation. (i can't remember what it was installing when it stopped. SORRY) i couldn't force anything to quit since everything was frozen at this point so i had to restart manually. hoping that the installation would pick up where it left off, i booted to ubuntu again and got a message saying that my GUI would not start and would i like to diagnose the problem. i selected no since im kinda new at this and my computer eventually restarted.

im starting to panic a bit since i really hate windows and now im being forced to use it.

any help would be appreciated. im trying not to have to delete the linux partition and reset the MBR but it looked like i might end up doing just that. 

HELP!!!!!

---

### Post by bapoumba on 2007-10-21
Can you boot in recovery mode from the grub menu?

If you do, login with your regular user, and run
```
apt-get update
apt-get dist-upgrade
```
To finish up the upgrade.
In recovery mode, you'll be root with a # prompt. No need to enter sudo.

If everything goes okay:
```
reboot
```

---

### Post by ede1005 on 2007-10-21
i'll try it

---

### Post by tmcginn5 on 2007-10-21
I am having the same problem.  I know how to boot in recovery mode from the grub menu.

But how do you login with your regular user?

---

### Post by bapoumba on 2007-10-21
> **tmcginn5 said:**
> I am having the same problem.  I know how to boot in recovery mode from the grub menu.

But how do you login with your regular user?
You'll be prompted for your login, then your password.

---

### Post by ede1005 on 2007-10-21
thanks a lot. it worked for the most part. now i have to figure out why my drives will not mount. i'll be doing some forum surfing for the next hour or so

---

