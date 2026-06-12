---
title: "Ubuntu installed in text mode only"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by IZWicky on 2009-12-10
Hello,

I installed Ubuntu 9.10 in my virtual machine (VMWare) but it installed in text mode only, no graphics, just like terminal.

I've installed other Ubuntu versions in my virtual machine alot of times and never had this problem, what can it be?

---

### Post by MelDJ on 2009-12-10
try typing sudo gnome-desktop and see what happens

---

### Post by spcwingo on 2009-12-10
Try this...log in on the terminal and run this command.

```
sudo apt-get install --reinstall ubuntu-desktop
```

If it says something to the effect of "ubuntu-desktop not currently installed", then run this one:

```
sudo apt-get install ubuntu-desktop
```

Let me know if that does the job.

---

### Post by IZWicky on 2009-12-13
@spcwingo:

I tried both, but it reaches a time where the installation crashes or the server simply stops responding and I have to restart the server.

---

### Post by spcwingo on 2009-12-13
Did you md5sum the ISO or run the "check CD for defects" options from the boot disc menu before you installed from it?

---

### Post by IZWicky on 2009-12-19
I did both and didn't had problems.:confused:

EDIT:

The installation process is also different, I mean the blue background with gray windows.

---

