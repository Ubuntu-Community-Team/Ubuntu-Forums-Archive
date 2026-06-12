---
title: "How can I upgrade to Hardy Heron if it is not offered in the Update Manager?"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by crazyfish666 on 2008-05-24
When Hardy Heron came out I got an option in the Update Manager to upgrade to it, but I wanted to back up properly first and have only just gotten around to doing this. But, the upgrade option in the Update Manager disappeared about a week ago and I can't seem to find instructions on any other simple way to upgrade. How can I do this?

---

### Post by Kevbert on 2008-05-24
Enter the following codes from terminal:
```
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by crazyfish666 on 2008-05-24
> **Kevbert said:**
> Enter the following codes from terminal:
```
sudo apt-get update
sudo apt-get upgrade

```

I did that and it didn't do anything very grand. I just shut it down afterwards (with 'sudo init 0' since my computer has no shut down option) and logged back on (starting x manually as I have had to do for a while). Absolutely nothing looks different. Same background and all. How do I check what I am running? Hardy or Gutsy...

Thanks

---

### Post by newbreed on 2008-05-24
you enter one at a time?

---

### Post by Kevbert on 2008-05-24
Try:
```
sudo apt-get dist-upgrade
```
If this doesn't work try using 'aptitude' in place of 'apt-get'.
This should take a while.
To check the version you're running:
```
lsb_release -a
```

---

### Post by atomkarinca on 2008-05-24
I guess the code you're looking for is

```
sudo apt-get dist-upgrade
```

---

### Post by crazyfish666 on 2008-05-24
> **Kevbert said:**
> Try:
```
sudo apt-get dist-upgrade
```
If this doesn't work try using 'aptitude' in place of 'apt-get'.
This should take a while.
To check the version you're running:
```
lsb_release -a
```

Well, the second code still says I am running Gutsy and the first code (both in that form and with apt-get replaced with aptitude) the apt-get version took about 2 seconds and the aptitude took about 10, both said "0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded".

The second code still says Gutsy.

Any ideas?

---

### Post by tom56 on 2008-05-24
From a terminal in GNOME:
```
gksudo update-manager -d
```
If that doesn't work try:
```
gksudo update-manager -c
```

---

### Post by Kevbert on 2008-05-24
It looks like something must be broken.  Try:
```
sudo apt-get install -f
```
This should repair any broken packages. Then try to upgrade again.
If this does not work change the Server that you use in System-Admin-Software Sources before having another go at updating.
Good luck.

---

