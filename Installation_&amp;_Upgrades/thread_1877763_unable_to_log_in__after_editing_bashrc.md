---
title: "unable to log in  after editing bashrc"
date: 2011-11-08
forum: Installation &amp; Upgrades
---

### Post by suspect x on 2011-11-08
Problem after editing the .bashrc file to add some colores to "[COLOR=Lime]user@host:dir$[/COLOR]" 
I've added a file to "/etc/skel/colors.sh" and I can't login again
iam using ubuntu 10.04 LTS lucid

---

### Post by Shazaam on 2011-11-08
Boot up a livecd, mount the drive you need, then edit the files in question. Reboot.
You will need to do this as root. Here is the terminal command (be careful as you get ABSOLUTE root rights on the drive(s); mistakes can be permanent) once the livecd boots to a desktop...
```
gksudo nautilus
```

As a reminder, before you edit system files back them up. That way you can go back and use the originals if you make a mistake.

---

### Post by suspect x on 2011-11-10
thanks for helping me ,
but can I ask you to put the standard .bashrc file so I can compare both files !
thanks

---

### Post by nothingspecial on 2011-11-10
A standard .bashrc is located at

/etc/skel/.bashrc

You can copy it to your home folder.

---

### Post by suspect x on 2011-11-10
am afraid that I've accidentally overwritten that file :-(

---

