---
title: "Where to report bug if my bug reporting system crashes?"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by atlee on 2010-03-31
Hi all,

Everyday, nearly once every second reboot i get a few app crashes, cant report it, the reporting manager crashes, where to report manually as i know the steps what crashed it and the app that crashed or do i goto the bug site and find the app and report against the same error?

---

### Post by VMC on 2010-03-31
> **atlee said:**
> Hi all,

Everyday, nearly once every second reboot i get a few app crashes, cant report it, the reporting manager crashes, where to report manually as i know the steps what crashed it and the app that crashed or do i goto the bug site and find the app and report against the same error?

If you don't know the correct package name go [here]("https://wiki.ubuntu.com/Bugs/FindRightPackage") first.

Then go to [Launchpad]("https://launchpad.net/ubuntu/"), and type in the  package in question. See if any bugs already filed. If not, report a bug yourself.

---

### Post by lavinog on 2010-03-31
Make sure you have the latest updates too.  Some bugs may have already been fixed.

---

### Post by atlee on 2010-04-01
I know the packages that are crashing but when I click submit bug, the submitting program crashes, i have all patches upto date. Weird I also have 10.04 on my older laptop machine no crashes since installed and applied updates, different architectures I'm guessing.

---

### Post by lavinog on 2010-04-01
> **atlee said:**
> I know the packages that are crashing but when I click submit bug, the submitting program crashes, i have all patches upto date. Weird I also have 10.04 on my older laptop machine no crashes since installed and applied updates, different architectures I'm guessing.

You could try doing a memtest.
I am not very experienced with grub2 though...I think you need to hold down shift to pull up the grub menu if you are not dual booting.

---

### Post by dino99 on 2010-04-01
> **atlee said:**
> I know the packages that are crashing but when I click submit bug, the submitting program crashes, i have all patches upto date. Weird I also have 10.04 on my older laptop machine no crashes since installed and applied updates, different architectures I'm guessing.

When i'm in trouble like you are, first i do several things:

- try to identify errors logged (/var/log or system-admin-log viewer)
- clean my system: sudo apt-get clean/autoclean/autoremove
- be sure that i only use official repo for this distro ( no release mixed or ppa or third party) (sources.list)
- repair broken packages: sudo apt-get install -f
- if your troubles comes after a dist-upgrade, maybe there are old config/settings left behind and conflict, you can install bleachbit to clean most of the broken symlinks ( take care to understand what you do, use it as root)

- then update, upgrade and reboot

If troubles are still there, you can now try to report. If it fail again: remove/purge then reinstall the packages you suspect (apport, ...)

---

### Post by Paqman on 2010-04-01
Before entering you bug manually in Launchpad you could try prodding apport to report it. As long as apport is actually working you can force it to report a bug about itself like so:
```
ubuntu-bug apport
```

---

### Post by atlee on 2010-04-01
> **Paqman said:**
> Before entering you bug manually in Launchpad you could try prodding apport to report it. As long as apport is actually working you can force it to report a bug about itself like so:
```
ubuntu-bug apport
```

Well apport works with the terminal command but lets say something applet crashes, then apport asks if i want to report, thats when apport crashes. I will see if i can replicate.

---

### Post by atlee on 2010-04-01
> **lavinog said:**
> You could try doing a memtest.
I am not very experienced with grub2 though...I think you need to hold down shift to pull up the grub menu if you are not dual booting.

I definetly don't have faulty memory, got good quality ram corsair XMS ddr3 1600mhz, nothing wrong there, 9.10 works flawlessly, crashes here and there on 10.04, new clean install because upgrading crashes even more.

---

### Post by atlee on 2010-04-01
> **dino99 said:**
> When i'm in trouble like you are, first i do several things:

- try to identify errors logged (/var/log or system-admin-log viewer)
- clean my system: sudo apt-get clean/autoclean/autoremove
- be sure that i only use official repo for this distro ( no release mixed or ppa or third party) (sources.list)
- repair broken packages: sudo apt-get install -f
- if your troubles comes after a dist-upgrade, maybe there are old config/settings left behind and conflict, you can install bleachbit to clean most of the broken symlinks ( take care to understand what you do, use it as root)

- then update, upgrade and reboot

If troubles are still there, you can now try to report. If it fail again: remove/purge then reinstall the packages you suspect (apport, ...)

well just checking through the log, found the stuff below:
/usr/lib/gvfs/gvfs-gdu-volume-monitor
/usr/lib/indicator-applet/indicator-applet-session
/usr/bin/gnome-panel
so the 3 above crash continuously randomly

```

apport (pid 1635) Wed Mar 31 23:21:29 2010: called for pid 1477, signal 6
apport (pid 1635) Wed Mar 31 23:21:29 2010: executable: /usr/lib/gvfs/gvfs-gdu-volume-monitor (command line "/usr/lib/gvfs/gvfs-gdu-volume-monitor")
apport (pid 1635) Wed Mar 31 23:21:29 2010: wrote report /var/crash/_usr_lib_gvfs_gvfs-gdu-volume-monitor.1000.crash
apport (pid 1657) Wed Mar 31 23:21:30 2010: called for pid 1651, signal 6
apport (pid 1657) Wed Mar 31 23:21:30 2010: executable: /usr/lib/indicator-applet/indicator-applet-session (command line "/usr/lib/indicator-applet/indicator-applet-session --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=22")
apport (pid 1657) Wed Mar 31 23:21:30 2010: wrote report /var/crash/_usr_lib_indicator-applet_indicator-applet-session.1000.crash
apport (pid 1629) Wed Mar 31 23:56:02 2010: called for pid 1382, signal 11
apport (pid 1629) Wed Mar 31 23:56:02 2010: executable: /usr/bin/gnome-panel (command line "gnome-panel")
apport (pid 1629) Wed Mar 31 23:56:03 2010: wrote report /var/crash/_usr_bin_gnome-panel.1000.crash
apport (pid 1564) Thu Apr  1 07:57:18 2010: called for pid 1555, signal 6
apport (pid 1564) Thu Apr  1 07:57:18 2010: executable: /usr/lib/indicator-applet/indicator-applet-session (command line "/usr/lib/indicator-applet/indicator-applet-session --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=22")
apport (pid 1564) Thu Apr  1 07:57:19 2010: wrote report /var/crash/_usr_lib_indicator-applet_indicator-applet-session.1000.crash

```

Cleaned my system
I only use official repos
I have tried upgrading over top of 9.10 but receive more errors so i always clean install, after all updates fixed alot of crashes but still left with a few

I don't know much about linux but using MacOSX for a while and editing files and using terminal, feels very similar

/usr/lib/gvfs/gvfs-gdu-volume-monitor - Is this linked with ALSA???
/usr/lib/indicator-applet/indicator-applet-session - Is this the speech bubble applet up in the top right corner???
/usr/bin/gnome-panel - Bottom or top panel???

---

