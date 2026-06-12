---
title: "fresh install but locked out of one h/drive"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by broekskw on 2008-02-03
great finally got my other comp going with ubuntu, but on fresh install on my desktop i have a drive that is labeled sd4 and if i click on it and open it, it is labeled lost & found and i am locked out, see the attached screen shots, this is the rest of my h/drive that i am going to use for downloads,pictures etc, how do i get permission to access this folder

---

### Post by broekskw on 2008-02-03
anyone have any ideas :guitar: reading on google but still can not find the fix for this problem:confused:

---

### Post by BennBuntu on 2008-02-03
maybe was owned under a different username last time?
try root nautilus

```
gksudo nautilus 
``` 

If that lets you in, change ownership to your new username with chown

```
sudo chown -R "new user name here" /"path to the drive"
```

-R makes it recursive, so everything inside the drive will be owned by you too.

---

### Post by broekskw on 2008-02-03
BennBuntu thanks tried that command from a terminal and got another window open showing my root desktop folder, this is my 5gb root folder not the 12gb partition

:confused::confused:

---

### Post by broekskw on 2008-02-03
when i try to unmount it i get this error

---

### Post by BennBuntu on 2008-02-03
yep, from there navigate to the drive

prolly in /media/

or straight up

```
gksudo nautilus /media/sda4/
```

---

### Post by PmDematagoda on 2008-02-03
The "lost+found" folder is where the journal of the file system is found, you should not do any changes to it. 

Since sda4 is not part of a root partition or home partition, did you try to create a directory in the drive?

---

### Post by broekskw on 2008-02-03
thanks BennBuntu and PmDematagoda, so here is my question before i go any further, this sda4 h/drive is it still able to save downloads to , video, movies,mp3 files.that i would have access to, if so then everything is ok , i just thought that not  getting into this lost and found folder meant that the rest of this sda4 folder was also locked out??

---

### Post by BennBuntu on 2008-02-03
yep, by default, lost and found is owned by root, so not for normal access.

---

### Post by broekskw on 2008-02-03
BennBuntu that command worked great, folder window came up and can  get into lost&found no problem(not changing anything in it as perPmDematagoda) , also can create a new folder for all my donloads,so do i have to use this command all the time to unlock??
:lolflag:

---

### Post by BennBuntu on 2008-02-03
can you make folders without using sudo?

if not, this command will make the drive yours

```
sudo chown -R broekskw2 /media/sda4/
```

---

### Post by PmDematagoda on 2008-02-03
It is highly recommended that you do not change the permissions as well since I have heard that you can get some problems when you change the permissions of the lost+found folder. You can try and set the permissions of the lost+found folder back to the originals using:-```

sudo chown root:root lost+found
```

---

### Post by broekskw on 2008-02-03
BennBuntu thanks for everything:popcorn: did that command and all is good,

so what did i do wrong on a fresh install to get this sda4 locked
had a 40gb h/drive with winxp on, used gparted to resize my 40gb to a 5gb ext and a 1gb swap and then the 12gb ext partition , then reloaded live cd and ran install,

at boot up i do not get in my menu a selection to load up window xp so i put in my fresh super grub disc but will not load just goes to the 4sec screen to hit esc key for menu or load ubuntu

back to the drawing board with this

ps PmDematagoda changed back to root will leave well enough alone:guitar:

---

### Post by BennBuntu on 2008-02-03
Don't know much about supergrub, but sounds like maybe you didin't tell the ubuntu installer to use the 12GB as /home/
assuming that's what you wanted. When installer is in the partition management, set the mount point as /home/

---

