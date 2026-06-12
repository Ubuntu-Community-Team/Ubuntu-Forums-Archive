---
title: "Setting Home mount point"
date: 2006-02-21
forum: Installation &amp; Upgrades
---

### Post by tadashi on 2006-02-21
Just wondering if I am doing something wrong or if this is situation normal:

I tried setting up a FAT32 drive as /home so both Linux would use that for data and My Windows My Document Directory would also be on that.  However, it would do this but then I am stuck in an endles loop asking for my name, user name, and password.  Is it because the system cannot write to the FAT32 drive?

Is there a way around this?  That is moving the /home directory without breaking the system?

---

### Post by taurus on 2006-02-21
As far as I know, I don't think you can create /home with vfat (fat32) filesystem...  If you want to share files between Ubuntu and Windows, create a partition like /data and format it as vfat then!  Otherwise, you will be in that never ending loop of username and password thing!!!

---

