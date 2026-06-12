---
title: "Upgraded to 11.04; system unable to start"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by Arancaytar on 2011-08-21
I have an HP625 notebook with AMD64 Athlon processors, and I was running the amd64 version of Ubuntu 10.10.

The upgrade to 11.04 went smoothly aside from a worrying error warning me that the BLCR kernel module could not be installed.

Despite that, the computer restarted without problems and allowed me to log in. It took about two minutes to log in (almost instant with 10.10), but at least it worked. Ubuntu Classic worked as well, though the graphics were a bit broken (lines on the screen and stuff). Also, I had to restart the computer a second time before I could log in with Ubuntu Classic.

Since the third restart, the display goes blank (but not out) before reaching the login screen, which also happens when booting into single user mode. The last message on screen before this happens announces it is loading the cpufreq module.

I'm close to reinstalling 11.04 to a different partition, but first I'd like to find out if this is fixable. (I have a flash drive with Puppy 5.2.8, which is currently the only way the computer will run at all).

---

### Post by Arancaytar on 2011-08-21
I have discovered that the recovery option (kernel argument "single") actually does work until it gets to the menu offering different recovery actions, but at that point the keyboard does not function. A few seconds after this, the screen goes blank again.

I've looked into the the kernel, boot and system logs using the live system, but there is no obvious problem there.

---

### Post by raja.genupula on 2011-08-21
i think due to bugs . what ever run the update and upgarde , even in command login (ctrl+alt+f1)
```
sudo apt-get update 
sudo apt-get upgrade 

```

---

### Post by ptsant on 2011-08-21
> **Arancaytar said:**
> I have discovered that the recovery option (kernel argument "single") actually does work until it gets to the menu offering different recovery actions, but at that point the keyboard does not function. A few seconds after this, the screen goes blank again.

I've looked into the the kernel, boot and system logs using the live system, but there is no obvious problem there.

I have a very similar problem. Ubuntu 11.04 installation went fine. However, when I decided to install the
numerous updates (why a downloaded CD does not already contain said updates is beyond me) the system broke. In fact, I think the culprit is the installation of grub and the removal of grub-uefi.

Since then nothing boots at all (win, ubuntu) and I get the same situation as you, with a keyboard that does not function. Installing on top of other stuff (win boot), breaking a perfectly working system, including OTHER OSes is the kind that of thing that only microsoft did. And I never got any warning at all, no menu to choose or other option. Yes I could have read each of the 200 updates to see if I should choose it, but don't you think the user has to be warned of such actions, like changing a boot system?

Anyway, I am royally pissed off. Especially if I have to reinstall windows which has nothing to do with my ubuntu system and sits on a separate drive with its own uefi boot.

---

### Post by Arancaytar on 2011-09-11
Update: 11.04 includes some broken WiFi drivers, which made the system freeze when loaded.

The following article helped me troubleshoot this.

[http://bigbrovar.aoizora.org/index.php/2011/04/30/turning-wireless-on-causes-laptop-to-freeze-on-ubuntu-11-04-natty-narwhal-my-work-around/](http://bigbrovar.aoizora.org/index.php/2011/04/30/turning-wireless-on-causes-laptop-to-freeze-on-ubuntu-11-04-natty-narwhal-my-work-around/)

Blacklisting the affected kernel module and downgrading the bcmwl-kernel-source package were what fixed it for me.

---

