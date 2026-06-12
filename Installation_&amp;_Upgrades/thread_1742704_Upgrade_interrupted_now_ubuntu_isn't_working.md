---
title: "Upgrade interrupted now ubuntu isn't working"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by tank.tmt on 2011-04-29
Hello,

I was updating to the latest version of Ubuntu (i think 11.04) and the computer was restarted with 7 mins to go; my windows is still working on the same machine which means the booter is, but I cannot get into ubuntu.

Is there a way to recover functionality to ubuntu with doing a complete reinstall: aka keep my data?

Thames

---

### Post by dino99 on 2011-04-29
you have several choices:

1) try to repair: boot in recovery mode from grub menu, then choose "repair" packages"
note: actually the servers are very busy due to too many download for installing/upgrading natty, so better to wait till next week.

2) reinstalling maverick if you still have its iso on your hdd
note: your data are safe if you use a /home partition

this is how a standard installation is done:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by prshah on 2011-04-29
> **tank.tmt said:**
> 
I was updating to the latest version of Ubuntu (i think 11.04) and the computer was restarted with 7 mins to go;

Can you access a recovery terminal? Look for recovery options in the GRUB menu (may have to tap shift or esc during bootup).

If you can reach a recovery terminal, please see this thread [Hardy is wonderful]("http://ubuntuforums.org/showthread.php?t=780531") for advice on how to recover from an interrupted upgrade.

Please post back here if you have problems with this advice.

---

### Post by tank.tmt on 2011-04-29
I tried using the original install disc i used which was 10.04 but it would let me install side by side or overwrite, not repair: it also said that the current installation is 11.04.

I tried using the recovery option but it didnt work so as the boot menu also had other recovery things there where the number was slightly lower i tried them.
the next one said when i selected it that the drive couldnt be found and to either wait, skip or mount; skipping didnt do anything, mounting took me to a command line; i tried entering the commands from the thread linked but it just told me that it wasn't writable or somesuch

When i try going into the proper desktop or the recovery both say something about some python failing or somesuch

---

### Post by prshah on 2011-04-29
> **tank.tmt said:**
> said when i selected it that the drive couldnt be found and to either wait, skip or mount;

Please boot back into the recovery terminal and choose "m" for manual recover. Then please post back the output from the following commands```
cat /etc/fstab|grep -E UUID^
sudo blkid
mount
```

This will give essential information required to clear the drive not found error; subsequently you can recover the interrupted upgrade using the commands in the linked thread (Eg, dpkg --configure -a).

---

