---
title: "FakeRAID on ubuntu 10.10"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by Linux_noob616 on 2010-10-14
I downloaded kubuntu 10.10 x64 and it only sees my 2tb hard drive over my 3 RAID 0 drives.

In 10.04 i could at least see my RAID array, It would only mess up when installing Grub.

If anyone knows how to get it working please let me know.

---

### Post by Linux_noob616 on 2010-10-15
anyone?

---

### Post by ronparent on 2010-10-15
You have posted inadequate information to permit much of a reply. What is the output og 'ls /dev/mapper'?

---

### Post by Linux_noob616 on 2010-10-15
> **ronparent said:**
> You have posted inadequate information to permit much of a reply. What is the output og 'ls /dev/mapper'?

Not sure what you mean by that or how i get it. When i enable dmraid (which is already enabled it tells me) i get the name of my array "nvidia_cbfdcbae"

Which is located in /dev/mapper/

If thats any help..

EDIT: Using the advanced option in the installer i can select my RAID manually, i was able to get to the point where i could choose time. But then it crashed and i got this.


```
Traceback (most recent call last):
  File "/usr/lib/ubiquity/ubiquity/frontend/kde_components/PartMan.py", line 369, in on_partition_edit_use_combo_changed
    self.ctrlr.dbfilter.default_mountpoint_choices(method):
AttributeError: 'NoneType' object has no attribute 'default_mountpoint_choices'
```

---

### Post by ronparent on 2010-10-15
What else is located in /dev/mapper?

---

### Post by Linux_noob616 on 2010-10-15
> **ronparent said:**
> What else is located in /dev/mapper?

nvidia_cbfdcbae
nvidia_cbfdcbae1
nvidia_cbfdcbae2

After i tried the install i got 

nvidia_cbfdcbae5
nvidia_cbfdcbae6

Added as well. i don't believe either became anything however.

Also a file called "control"

EDIT: Okay so i restarted and formatted the drive using kubuntu 9.04 restarted with 10.10 and it picked up the RAID just fine, and installed with out a hitch.

---

### Post by ronparent on 2010-10-15
Great! Glad to hear it. Have fun.

---

