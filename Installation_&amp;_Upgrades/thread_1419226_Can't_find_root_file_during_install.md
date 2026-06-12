---
title: "Can't find root file during install??"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by jcitguy78 on 2010-03-01
I am installing 9.10 and when it gets to the preparing partition part, there is no partition showing up?? and i can't add one either??

---

### Post by darkod on 2010-03-01
The screen doesn't show any hdd right? Has the disk been used in raid earlier?

---

### Post by jcitguy78 on 2010-03-01
no, it's a new drive, formatted.

---

### Post by darkod on 2010-03-01
That usually happens if the disk has raid meta data on it. I know it's new, but it can happen.
Just in case to eliminate the possibility, and if you only have that one disk, boot with the Try Ubuntu option into the live desktop and run in terminal:

sudo dmraid -E -r /dev/sda

If it asks to remove raid data, that was the problem. Say yes, start the installer again and all should be fine.

Do NOT run the commnd if you are actually running raid.

Also double check that the disk is installed properly and visible in BIOS.

---

### Post by jcitguy78 on 2010-03-01
thanks i'll try that and let you know

---

