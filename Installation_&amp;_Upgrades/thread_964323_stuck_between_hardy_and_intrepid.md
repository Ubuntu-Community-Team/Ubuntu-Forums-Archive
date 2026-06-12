---
title: "stuck between hardy and intrepid"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by veganbikepunk on 2008-10-30
so, i tried upgrading to Intrepid from Hardy through update-manager. The first part was fast, but the 'clean up' part was taking forever, so I thought it had frozen, so I rebooted. Now it says I'm in Hardy in 'about ubuntu'. I can't go to 'software sources'. Update-manager has 616 distribution updates but it won't update them. It says 'not all updates can be installed.' Then it has the option to do a partial upgrade, but when I choose that, it says it can't upgrade from Intrepid to Hardy. How do I get to a full intrepid?

---

### Post by wbrucem on 2008-10-30
I'm in the same situation.

I've managed to work past some issues with Nvidia display, but cannot get 3D acceleration working (which I really, really need).  Xserver is one of the many packages which are listed as having updates available but are "held back".

Is there a way to reapply the upgrade, or something?

---

### Post by wbrucem on 2008-10-31
OK, I may be solving this one...

Not sure whether this was necessary, but I did
```

sudo dpkg --configure -a

```

Then followed the steps posted [in another thread]("http://ubuntuforums.org/showthread.php?t=964091").

The packages are still downloading, but it appears to be doing the missed updates.  I'll report back when I have results.

---

### Post by Venie on 2008-10-31
Hello, I have similar problem. During the configuration phase of the upgrade there was a power shortage. I can access CLI and I tried to continue configuration:

> **wbrucem said:**
> OK, I may be solving this one...
```

sudo dpkg --configure -a

```


but it stops for dependency problems. I've traced it down to dbus not being properly installed. "dpkg --configure dbus" gives"/var/run/dbus doesn't exists" (or similar)

What can I do? Is there a way to repair all or reinstall without losing my files?

---

### Post by wbrucem on 2008-10-31
I was eventually able to get everything straightened out by using **Synaptic** instead of Update-Manager.  Use the "Broken" filter to identify and correct dependency problems, then "Mark All Upgrades" and apply the changes.

I hope this works for you as well.

---

### Post by Venie on 2008-10-31
I managed to launch Synaptic over SSH on other computer, but it complained about same errors on dbus-package. So I forced uninstall of dbus and installed it again "dpkg --remove --force-all dbus && apt-get install dbus", and the upgrade resumed although in CLI. I'm still having some problems with kernel not having all drivers, but I think it might have nothing to do with the interrupted upgrade. I'll just try building new kernel and see if it helps.
Thanks for help :)

---

### Post by ssam on 2008-10-31
at boot choose the recovery option from grub. this has an option to fix partial upgrades. it might do the job.

---

### Post by jhertz on 2008-10-31
I think I'm in the same boat. My toddler powered off my computer while it was applying the dist-upgrade. Now when I boot I end u;p with a bunch of errors to the effect that /var/run and several other var folders are read only. I didn't partition the drive with separate partitions so I'm assuming it's part of the upgrade process. I was able to Ctrl + alt + f2 and get a login prompt, however when I try to run 
```
sudo dpkg --configure -a
```
I can't connect to the network (working wirelessly, I assume that the module isn't getting loaded). 
I'll try the recovery mode as well. Thanks for the thread!

---

### Post by Venie on 2008-11-01
> **jhertz said:**
> 
I can't connect to the network (working wirelessly, I assume that the module isn't getting loaded).

Try booting with the previous kernel (press esc for grub prompt when booting). It should have required module. Check [http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html](http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html) to configure your wireless from console.

---

