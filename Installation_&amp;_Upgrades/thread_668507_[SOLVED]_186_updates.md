---
title: "[SOLVED] 186 updates"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by chicoharv on 2008-01-15
I have 186 updates that won't update as I get an error message:
E:dpkg was interrupted, you must manually run"dpkg--configure - a"
E: cache -> open() failed,please report

How and what do I do, I am not that versed on linux yet to understand this.

---

### Post by DMK62 on 2008-01-15
Hi

Try rebooting the computer and go to Applications > Accessories > Terminal and in the terminal enter

sudo dpkg --configure -a

It may take a while to complete depending on how many packages could not be updated. After that finishes running do the followingin the terminal.

sudo apt-get update

then 

sudo apt-get upgrade

If all the packages were upgraded it should say that there are 0 to upgrade.

HTH

Dale

---

### Post by chicoharv on 2008-01-15
Thanks, rebooted and then only 104 updates came up, downloaded and installed,

---

### Post by DMK62 on 2008-01-16
You're welcome. Good to hear you were able to continue with the updates.

Dale

---

