---
title: "Why does SoftwareUpdater say I don't have enough space on my boot partition when I do"
date: 2014-07-13
forum: Installation &amp; Upgrades
---

### Post by shaansweb on 2014-07-13
Hello,

For some reason, Software Updater says it needs a total of 72.9 MB of space on my /boot partition for an update and is consequently asking me to free up space so it can run. This is puzzling because the Disks application says there are still 87 MB available on the drive. Does anyone know what's causing this problem and how I can fix it? Thanks
[IMG]http://i.imgur.com/dwEvcLM.png[/IMG]

---

### Post by lyhtsm on 2014-07-14
I've heard that something like nodes will cause 'not enough space' even when there is.
But it is a long long ago memory and I really can't find the forum at all, sorry about that.

---

### Post by bapoumba on 2014-07-14
Please post the output to :
```
df -h
df -i
```
This thread is marked as solved, is it ?

---

### Post by grahammechanical on 2014-07-14
The message is asking for at least and additional 2,626 K of space. So, it seems that in order to fit 72.9 M into a space of 87 MB it needs a little more than 14 MB room to manoeuvre. The utility is doing more than storing those 72.9 MB in that partition. They are more than likely to be Linux kernel files. The utility needs to install that kernel while at the same time deactivate the existing kernel and to do this with out crashing the OS. It needs room for manoeuvre, if you ask me. And you did.

If you look in the boot folder of that /boot partition you will see that there is a 20MB Gzip archive for every Linux kernel. I am guessing that the space is needed to extract what is in that Gzip file.

If we are going to have a /boot partition then we need to regularly remove old kernels to avoid this situation.

Regards.

---

