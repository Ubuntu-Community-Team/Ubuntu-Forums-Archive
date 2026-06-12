---
title: "Kubuntu rc: kate settings do not save"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by forcecore on 2009-04-17
every time i open kate settings are default ?

---

### Post by Götz on 2009-04-19
I have exactly the same problem in Jaunty maybe since Intrepid. I think it is a KDE upstream bug, but I don't know how to fix this. :(

Take a look at this [http://ubuntuforums.org/showthread.php?t=857866](http://ubuntuforums.org/showthread.php?t=857866)

---

### Post by inportb on 2009-04-19
> **forcecore said:**
> every time i open kate settings are default ?

Have you ever done anything with Kate as root? Because if you let Kate create its configuration files as root, you would not be able to modify them later as a regular user. The trick, of course, is to let the files be created as your regular user. Either chown them over, or remove the files and re-run Kate as a regular user.

---

### Post by Götz on 2009-04-19
> **inportb said:**
> Have you ever done anything with Kate as root? Because if you let Kate create its configuration files as root, you would not be able to modify them later as a regular user. The trick, of course, is to let the files be created as your regular user. Either chown them over, or remove the files and re-run Kate as a regular user.

I think that is not the cause of the problem, I have 0 files in /root/ and ~/.kde/share/config/katerc has "-rw------- 1 1000 1000" permission.

---

