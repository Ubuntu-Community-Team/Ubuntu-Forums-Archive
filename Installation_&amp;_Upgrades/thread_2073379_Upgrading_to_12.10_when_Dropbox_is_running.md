---
title: "Upgrading to 12.10 when Dropbox is running"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by togo59 on 2012-10-19
My installation phase was about 65% through when it tried to install a Dropbox update. It simply stopped (I left it over night). At this point there's no "Cancel" option and a reboot will potentially leave the OS in a broken state.

If that's happened to you, use a terminal and do "sudo top"; identify the pid of Dropbox; kill it by typing "k" and then the PID.

You do not need to remove or purge Dropbox.

This solved the problem for me.

---

### Post by Trebacz on 2012-10-20
Awesome. I also ran into the same problem. Left it running overnight. Dropbox was using nearly 100% of the CPU, but the installation procedure was not moving.

It seemed to be stuck at 48% of the installation of dropbox according the 12.10 distribution upgrade process.

killed it and things seem to be progressing merrily now. Thanks

---

### Post by Trebacz on 2012-10-20
Not sure if the two were related, but after having to kill the dropbox process kde didn't start on reboot (I run kubuntu). My system just sat there trying to load kdm. Turns out the kde desktop was not installed (possibly uninstalled then not reinstalled).

I just ran "sudo apt-get install kubuntu-desktop" and all was well on the next reboot.

---

### Post by StarGazer83 on 2012-10-25
phew, this advice just saved my computer. Had exactly the same Dropbox-problem, upgrade went to a complete stop at 59% downloading Dropbox. Thank you so much:):):)

---

### Post by judedawson on 2013-01-24
Thank you so much for the post !!!!!!!! 

I encountered the same problem today & was starting to panic.

You made my day, mate :)

---

### Post by Adelard on 2013-12-15
Thank you!

Just wanted to add that the same problem/solution applies to Kubuntu 13.10.

Thanks again!

---

### Post by oldos2er on 2013-12-16
Old thread closed.

---

