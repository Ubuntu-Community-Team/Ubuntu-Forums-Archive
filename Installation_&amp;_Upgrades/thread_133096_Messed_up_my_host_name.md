---
title: "Messed up my host name"
date: 2006-02-19
forum: Installation &amp; Upgrades
---

### Post by tvsidekick on 2006-02-19
I'm in the process of trying to configure a wifi card and while in system/admin./networking, I have changed my host name.  Now, when I reboot, I get this window:  "Could not look up internet address for localhost localhost. localdomain (my mistake).  This prevents Gnome from operating properly.  It may be possible to correct the problem by adding localhost localhost to the file etc/hosts."   Of course, that file is read only.  (can I change that?)  With Gnome not "operating properly", I can't get back into networking configeration to fix my mistake.  I would like to get back to wrestling with my wifi card.  Any ideas?

---

### Post by jrib on 2006-02-19
[LIST]
[*]reboot
[*]at the grub menu, select 'recovery mode' (press ESC if the menu doesn't come up when you boot)
[*]you are now in a root shell
[*]append whatever is in /etc/hostname to the first line of /etc/hosts which corresponds to 127.0.0.1.  Use 'nano' or 'vim' as your editor.
[/LIST]

**example file contents:**
/etc/hostname:
```
ubuntu
```
/etc/hosts:
```
127.0.0.1 localhost.localdomain localhost ubuntu
```

---

### Post by tvsidekick on 2006-02-19
Thanks for the reply.   Actually, while in recovery mode, I discovered that I could get back into network configeration and replace my hostname with the correct one.   Incidently, the "hosts" file disappeared from etc.  Is that a bad sign? Hope I didn't delete it or anything.  By the way, I am now on the forum using Windows on my dual-boot.  I can't seem to figure out how to get my Belkin  PCI wifi to be recognized by Firefox on ubuntu.  Do I need to add it in network devices?  Help says to hit the "add" button in the device tab, but there is no "add" avaliable.  The card is recognized in network ("tools?") with the generic 127.0.0.1 address and as a loopback device, and pings very nicely, thank you.  Sorry, guess this should have been another thread.  You can see by my beans number that I haven't been here for long.  I appreciate the patience of the veterens on this great forum.

---

