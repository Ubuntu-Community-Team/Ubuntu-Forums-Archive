---
title: "Old Compaq laptop and feisty"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by Matrix452 on 2007-06-08
I'm encoutnering a problem when i attempt to install fistey xubuntu on my old Compaq Presario 1260 laptop. The problem occures when the installer attempts to redraw the partition map of the drive and format the main partition for the main drive it says that the instalelr does not have permission to edit the partition. The instalation fails there and no matter how many times i attempt to install it gives me the same error.

---

### Post by bodycoach2 on 2007-06-08
That's a really old laptop. First, I'd recommend doing a "dban" Darik's Boot & Nuke on it, just in case. Then, though it sounds like you may have done this already, use only the Alternate Install CD. Make sure you've burnt the CD at the lowest speed possible.

How much Memory do you have? If it's under 160 MB, I'd recommend using Pupply Linux, right off the CD on that machine. Or, so a Ubuntu Server installation, and then sudo apt-get install icewm.

---

### Post by Matrix452 on 2007-06-10
That worked, thanks for your help

---

