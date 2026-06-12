---
title: "Many errors, please help."
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by Jaivaz on 2005-04-08
I just upgraded from Warty, and I've foudn some problems..
----
I try to run Synaptic, I find it, click it, and nothing happens. I run the command in a terminal and get...
> root@Kamigawa:/home/horace # /usr/sbin/su-to-root -X -c /usr/sbin/synaptic
/usr/sbin/su-to-root: line 36: /usr/sbin/synaptic: No such file or directory

----------
I go into my menu files..and there is two of everything in the 'Debian' folders... 
-------
I take a screenshot and get.... 
> Cannot execute 'gnome-screenshot'

Details: Failed to execute child process "gnome-screenshot" (No such file or directory)
----
SORRY! I posted in the wrong forums, I meant to post this in the 5.04 forum.. Please forgive me and it'd be nice if you could move this.  ](*,)

---

### Post by ubuntu_demon on 2005-04-09
[QUOTE=Jaivaz]I just upgraded from Warty, and I've foudn some problems..
----
I try to run Synaptic, I find it, click it, and nothing happens. I run the command in a terminal and get...

----------
I go into my menu files..and there is two of everything in the 'Debian' folders... 
-------
I take a screenshot and get.... 

----
SORRY! I posted in the wrong forums, I meant to post this in the 5.04 forum.. Please forgive me and it'd be nice if you could move this.  ](*,)[/QUOTE]
 actually it should be here in installation help :)

If you did follow the guides correctly probably you have forgotten to do this after the distupgrade :
sudo apt-get ubuntu-base ubuntu-desktop

if that doesn't help then please read this thread and try the solutions offered there :

[http://www.ubuntuforums.org/showthread.php?t=23624](http://www.ubuntuforums.org/showthread.php?t=23624)

If you have still problems after this please post your /etc/apt/sources.list and what you have done to upgrade.

---

