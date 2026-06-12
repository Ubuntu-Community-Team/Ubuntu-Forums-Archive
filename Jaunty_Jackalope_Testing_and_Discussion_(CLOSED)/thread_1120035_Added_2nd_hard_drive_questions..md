---
title: "Added 2nd hard drive questions."
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by GARoss on 2009-04-08
I have this old computer that has 2 hard drives. I installed Ubuntu jaunty on the old c:, all @ ext4. Then I used GParted to reformatted the 2nd hard drive to ext4 as well. After a reboot the system mounts the 2nd hard drived but I cannot do anything else with it; cannot create a new folder or copy files into it. 
Under *Computer:///* the 2nd HD called *80.0 GB Media, CD-ROM/DVD-ROM Drive & old c: is Filesystem*. Opening 80.0 GB Media under *Location* it says */media/disk* & it has a folder named *lost + found* which cannot be opened.
:confused:Where did I go wrong or what haven't I done?

---

### Post by taavikko on 2009-04-08
Ownership of the folder,
if "ls -l /media/disk" says that root, then it's owned by root.

Make yourself (and group ) the owner,
```
sudo chown -R $USER:$USER /media/disk/
```

Lost and found is reserved for system to place lost files, not for user to fiddle around. (though this can be disabled, if needed)

---

### Post by GARoss on 2009-04-08
Thanks! That fixed it.

---

