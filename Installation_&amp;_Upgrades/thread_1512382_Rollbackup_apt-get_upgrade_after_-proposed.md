---
title: "Rollbackup apt-get upgrade after -proposed?"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by superdoopernoob on 2010-06-18
I was trying to do two things at once and hosed my install.  I started following instructions from one to add lucid-proposed as a software source.  The other said to run a sudo apt-get upgrade.  If I am correct this upgraded all the packages to the proposed/unstable version.  I am a super noob and am running into a lot of issues with this configuration.  Is there any way to "rollback" the upgrade to the current stable versions rather than proposed?

Thanks!

---

### Post by leorolla on 2010-06-18
posted twice

---

### Post by leorolla on 2010-06-18
1. What exactlly were these instructions?

2. What issues are you running into?

3. Could you give us some information about your package managing  settins? Please, open a terminal and run
```
apt-cache policy
```
Copy the output of the terminal and paste it here. Please put [ CODE]  before and [/CODE] after the copy-pasted text so it will look like the  command I wrote just above.

---

