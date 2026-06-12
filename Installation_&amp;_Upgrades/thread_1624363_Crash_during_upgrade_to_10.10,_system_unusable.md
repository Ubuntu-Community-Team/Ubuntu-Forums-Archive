---
title: "Crash during upgrade to 10.10, system unusable"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by johann_p on 2010-11-17
The upgrade from Ubuntu 10.04 32 bit, which was running fine, to 10.10 crashed during the installation of the packages. When I boot the computer now, I see the login screen, but neither the mouse, nor the keyboard work, no login is possible and no switching to a text login screen is possible. Power off is the only working option.

When I boot using the safe mode, I see the boot messages and then:

```

Begin: Running /scripts/init-bottom ...
Done.
mountall: Keine Verbindung zu Plymouth

```After this, the system hangs and can only be powered off.
The last message is in German because this is a German Ubuntu installation, it is equivalent to
```
mountall: Could not Connect to Plymouth
```

I am very frustrated about this ... anything to save the system?

---

### Post by mörgæs on 2010-11-18
Plymouth is a central part of Ubuntu, so I don't think that it is worth the effort to rescue the system. Better to save your files and do a fresh install.

On a working system you could try to run 
```
sudo apt-get remove plymouth
```
without confirming!!! to see how much depends on Plymouth.

---

### Post by sikander3786 on 2010-11-18
Before re-installation, you can try to boot into Recovery Mode and drop to Root Shell and perform these commands.

Connect to internet,

```
dhclient eth0
```

Replace eth0 with your network interface.

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

```
sudo apt-get dist-upgrade
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by johann_p on 2010-11-18
Unfortunately, booting into recovery mode did not work either ... same lockup.

What I ended up doing is something that was recommended on the German Ubuntu board:
   [http://wiki.ubuntuusers.de/chroot/Live-CD](http://wiki.ubuntuusers.de/chroot/Live-CD) (in German).

It boils down to doingt this:
 * booting an Ubuntu Live CD
 * mounting all the relevant mount points in some directory of the live CD system (/mnt)
  * copying over relevant data
  * starting a chroot shell with the directory where the hard disk system is mounted as root
  * repairing the broken installtion there by repeatedly doing 
    "apt-get -f install" and "apt-get upgrade" and "apt-get dist-upgrade"
  * exiting the chroot shell 
  * rebooting

After rebooting the system was usable and with some additional package updates/upgrades it now looks like new and is running 10.10

---

