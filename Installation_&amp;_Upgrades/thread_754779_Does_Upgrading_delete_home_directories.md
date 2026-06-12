---
title: "Does Upgrading delete home directories?"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by boazarad on 2008-04-14
If I were to install Ubuntu 8.04 over and existing 7.1 release (or 8.04 beta for that matter) would the users home directories be harmed?

Will this still hold if i use the same main username during installation?

---

### Post by scragar on 2008-04-14
if you are planning a normal upgrade your home directory would be fine, if you wanted to install over your current version it would delete your home directory along with anything else on the drive(unless you use the guided-resize optioon to put hardy alongside gutsy)

---

### Post by boazarad on 2008-04-14
When installing a fresh install, and selecting the main partition as a target partition, but instructing the installer not to format the drive - you receive a warning that some files may be overwritten.

Does this include the home directories?

---

### Post by scragar on 2008-04-14
I am unsure what files would be deleted, and honestly I would not trust it. You best bet is to create a seperate /home partition at some point, and use that(choose manual when partitioning to set it to mount in /home or /home/username ), since this partition will always be safe, and should you ever need to reinstall it is easy to restore(also great if at some point you no longer wish to use linux and decide to get rid of it and install something else)

---

### Post by boazarad on 2008-04-14
Thanks scragar,
I was hoping that under linux, the practice of partitioning in order to be able to conveniently format the os was unnecessary. I guess this is not the case...

---

### Post by bapoumba on 2008-04-14
If you perform a fresh install, the entire root (/) partition will be written over. If your /home is not on a separate partition, it will be gone. A dist-upgrade will keep /home, even if on the same partition as /

I prefer fresh installs (it cleans a lot of what I do for tests) with a separate /home (my user settings are kept, specially the desktop tweaks).
After proper backups, you can separate your /home :
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by king.pest on 2008-04-14
hey, 

whereas it's best if you have a separate /home partition, it's possible to make a *fresh* install without having it and without loosing any data. that's a bit tricky and I would advise not to do it, but... sometimes it's the only way (if you have a very small hard drive, for example). 

first you have to either boot up a live-cd or an alternate-install-cd, and switch to some free VC prior to starting the installation program (you can do it with Alt+Ctrl+F2 for /dev/tty02 for example). then you have to mount your partition that contains /home directory (I assume you have one partition for / and /home, otherwise there wouldn't be a problem, right?) running something like this:
```
mkdir old && mount -t ext3 /dev/sda3 old
```
where /dev/sda3 is the name of your partition and ext3 is the filesystem which it uses (change to something else if you need). then, having your old root filesystem mounted, 'cd' into it, and 'rm -rf' all the directories except /home. once you have them removed, try:
```
cd ../ && umount old && exit
```
then go back to the installer (either to GUI if using a live-cd with Alt+Ctrl+F7 or to the old debian installer with Alt+Ctrl+F1 if using the alternate-cd) and proceed with the installation. when asked about partitioning, choose your old / filesystem as the new / filesystem and remember to uncheck the box that says "format". I'm not sure if the ubiquity installer will let you do that, that's way I'd advise using the alternate disc, but anyways you will have a *fresh* installation without a separate /home partition and without loosing any data. 

good luck!

---

