---
title: "Gnome Settings Daemon fails in Hardy Heron"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by pbewig on 2008-04-30
I built a computer last Christmas and ran it without difficulty
using Gutsy Gibbon.  Last evening I installed Hardy Heron and
on first logging in to my account see the following error message:

    There was an error starting the GNOME Settings Daemon.

    Some things, such as themes, sounds, or background
    settings may not work correctly.

    The last error message was:

    Did not receive a reply. Possible causes include:
    the remote application did not send a reply, the
    message bus security policy blocked the reply, the
    reply timeout expired, or the network connection
    was broken.

    GNOME will still try to restart the Settings Daemon
    next time you log in.

The problem recurs when I logout/login and when I reboot.

The computer has an Asus motherboard and AMD-64 CPU.  About
GNOME reports Version 2.22.1, Distributor Ubuntu, Build Date
4/15/2008.  Dmesg shows no obvious gnome errors.

Can someone offer advice?

Many thanks,

Phil

---

### Post by jpeddicord on 2008-04-30
Did you run an upgrade from 7.10 or a fresh install? Also, could you open a terminal and post the results of running:```
gnome-settings-daemon
```

---

### Post by pbewig on 2008-04-30
I performed an upgrade from 7.10.  The following messages appear
when I run gnome-settings-daemon:

    ** (gnome-settings-daemon:7279): WARNING **: Failed to
    acquire org.gnome.SettingsDaemon

    ** (gnome-settings-daemon:7279): WARNING **: Could not
    acquire name

Thanks for the quick response.

Phil

---

### Post by ubnewbie2 on 2008-04-30
I've seen this once since I upgrade to 8.04.   However, I have seen it before when running gutsy.  It just seems to happen occasionally.

---

### Post by pbewig on 2008-04-30
I have not seen this in Gutsy Gibbon, only since upgrading to Hardy Heron.  The problem recurs every time I login, for all users (not just me), and has survived multiple reboots.

Phil

---

### Post by pbewig on 2008-04-30
I just noticed that the shutdown icon at the top-right corner of the screen changes its appearance.  When I first login, the icon is an image of a running man.  After several minutes (I didn't time it, but probably about five to ten minutes), the icon changes to the standard circle with a half-line through the top (is there a proper name for that icon?).

Does that help?

Phil

---

### Post by kacheng on 2008-05-01
I've am also encountering this after an upgrade from Gutsy.

It only happens for one user, but for that user it is consistent and it definitely slows the profile down.  For example to run the upgrade manager and have it check for new updates takes 10 sec on the good profile, but takes 2 min on the bad profile.

Also the theme seems to jump back and forth from Ubuntu to and from a default Gnome one.

Have you noticed performance issues?

---

### Post by wedge2k on 2008-05-03
I have the same problem, although i have a fresh install of Hardy.  Not sure when it stopped working because it was working for a while after the install.

---

### Post by pbewig on 2008-05-04
I still don't have a solution.  Can anyone help?

Many thanks,

Phil

---

