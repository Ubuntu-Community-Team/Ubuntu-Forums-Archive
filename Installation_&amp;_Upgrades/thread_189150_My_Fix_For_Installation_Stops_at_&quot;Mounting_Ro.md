---
title: "My Fix For Installation Stops at &quot;Mounting Root File System&quot;"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by bobt12 on 2006-06-04
When I tried to install Dapper on my old 800Mhz AMD system it would stop at mounting root file system. I waited at least 20 to 30 minutes with no change. I tried several of the boot options that were suggested in the help section of the installer.  I finnally got it to work by going to Other Options and at the boot prompt typing ide=nodma. The installation then worked and the system boots fine and works fine. The only thing that does not work is the hibernate and suspend. I have to shut the system down. Its kind of a pain because of the long boot times but it does work.

---

### Post by Kapre on 2006-06-04
[QUOTE=bobt12]When I tried to install Dapper on my old 800Mhz AMD system it would stop at mounting root file system. I waited at least 20 to 30 minutes with no change. I tried several of the boot options that were suggested in the help section of the installer.  I finnally got it to work by going to Other Options and at the boot prompt typing ide=nodma. The installation then worked and the system boots fine and works fine. The only thing that does not work is the hibernate and suspend. I have to shut the system down. Its kind of a pain because of the long boot times but it does work.[/QUOTE]

Bobt - what's your specs? How many RAM do you have? For a GNOME desktop you must at least have 256 (which is my personal perception - althought they say 128 will work). Did you create a swap? This will help you better if you have a smaller memory. Also, would suggest to install xubuntu.

K

---

### Post by bobt12 on 2006-06-05
I have 256 MB ram. The system works OK its a little slow at times, but I just use this as a play machine, the installer did the partitioning so I would assume it put in swap space. I have Breezy installed on another hard drive.  My other computer is an Emac.

---

### Post by fastb on 2006-06-06
Where should I write that ide=nodma

---

### Post by edemark on 2006-06-06
when you boot up the live cd there is a menu about tasks to be started like for example start or install ubuntu etc. On that screen use f6 (other options)

good luck

---

