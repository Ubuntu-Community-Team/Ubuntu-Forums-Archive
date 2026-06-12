---
title: "How to share /home partition with multiple Ubuntu based systems without erasing data"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by Nick_Jinn on 2010-07-19
How exactly can this be done?

---

### Post by anon.jdh on 2010-07-19
I read this great article on moving your home partition, maybe it can help you:

[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

If you have say 2 different Linux installs and a dedicated /home partition you wish to use, just make that partition the same /home partition for both systems (using the guide).

Hope this helps.

---

### Post by Nick_Jinn on 2010-07-19
Wont that delete the data on that partition? I think I tried that once before and the other OS ended up limited to the root partition without a home partition. That isnt supposed to happen, right?

---

### Post by ronnielsen1 on 2010-07-19
The problems with sharing /home among multiple distros are the config files. If you have one distro running rat poison, one running kde and one running gnome it might give some strange results trying to keep it separate. It's a lot better to have a separate home. I use different variations of my name to have entirely different setups in different /homes. I just use Ubuntu right now but you can use openbox on one user and gnome on another. The possibilities are endless. Too much choice? Not in my world

---

### Post by theozzlives on 2010-07-19
In the smb.conf (like the bottom)

```
[home]
path = /home/<yourusername>
available = yes
browsable = yes
read only = no
writeable = yes
guest ok = yes

```

---

### Post by ronnielsen1 on 2010-07-19
To attempt to clarify, I have one home partition. I have /home/ron that has different settings than /home/ron7

You always have access to any folders on your hard drive. It's easy to throw a link on your desktop to /mnt/hda1/home/user (or wherever)

---

### Post by anon.jdh on 2010-07-19
Let me clarify, you need a fresh partition for your new /home. and the contents will be copied from your current /home partition.

Back-up your /home directory first 

If something goes wrong, boot from a LiveCD and change the /etc/fstab back to how it was originally.

Remember you are doing this on more than one system.

If it works properly, both systems will have identical home directory contents, pointing to the same /home partition.

---

### Post by Nick_Jinn on 2010-07-19
> **anon.jdh said:**
> Let me clarify, you need a fresh partition for your new /home. and the contents will be copied from your current /home partition.

Back-up your /home directory first 

If something goes wrong, boot from a LiveCD and change the /etc/fstab back to how it was originally.

Remember you are doing this on more than one system.

If it works properly, both systems will have identical home directory contents, pointing to the same /home partition.


Awesome.

Is there a step by step wiki for this?

---

### Post by oldfred on 2010-07-19
Those that recommend sharing /home want you to have a different name for each which defeats the purpose of sharing the data.

It is much better to create a /data partition and link that into each install.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data older but still relavent
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

