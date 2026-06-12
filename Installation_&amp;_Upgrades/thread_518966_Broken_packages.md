---
title: "Broken packages"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by Keisad on 2007-08-06
I have a broken package on my system, and it is called "vmware-player".

I cannot reinstall it, since I cannot download or install since there is a broken package on there entirely. I can't remove it either, because of the following error:

In synaptic:

E: vmware-player: subprocess pre-removal script returned error exit status 1

Through the command line:

```
root@casper:~# sudo dpkg --remove --force-all vmware-player
(Reading database ... 176464 files and directories currently installed.)
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
/etc/init.d/vmware-player: 765: /usr/lib/vmware-player/net-services.sh: not found
   Virtual ethernet                                                    done
invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
/etc/init.d/vmware-player: 765: /usr/lib/vmware-player/net-services.sh: not found
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:

```

Please help, I am running gutsy and am afraid of the horde of updates awaiting my elongated absence.

---

### Post by Steve1961 on 2007-08-06
According to this post:

[http://ubuntuforums.org/showthread.php?t=425313&highlight=force+removal](http://ubuntuforums.org/showthread.php?t=425313&highlight=force+removal)

sudo killall vmnet-natd

sudo apt-get remove --purge vmware-player

---

### Post by Keisad on 2007-08-06
I have tried all of the recommended methods for removing, including all the ones listed in the above posted thread. None of them worked.

Is it possible for me to manually remove all of the package files? Would synaptic recognize it as missing if i did that? Is there any way to do it manually?

---

### Post by rillip on 2007-08-06
It looks as though it cannot remove because there are services it cannot stop.  You've tried to kill it and still get the error, can you prevent it from running at all?  Not sure if you have it setup to run automatically but I'd try disabling that.  Another alternative could be to boot from the liveCD,so the drive isn't mounted, then mount the drive.  There's no way it could be running then, so maybe that would allow you to remove it.

---

### Post by Keisad on 2007-08-09
Hm. Well, in a flury of madness and uncertainty, I tore it off my computer using my faithful "rm-r".

Processes were not a problem, else I would have not have been able to delete certain files. They all deleted fine when I did it. 

For reference, if your having this problem, follow these steps:

1. Type "locate vmware" to find any files of vmware on your computer. 
2. Delete them. However you want to.
3. Go into synaptic and remvoe the package "vmware-player"
4. It will then think the dumb thing never installed, and shall remove any other instances of it as such.

---

