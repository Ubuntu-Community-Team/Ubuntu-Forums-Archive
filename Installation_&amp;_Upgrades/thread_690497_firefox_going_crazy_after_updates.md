---
title: "firefox going crazy after updates"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by alejaaandro on 2008-02-07
hi everybody.. 
i installed the updates this morning but didn't have any time to work on my computer.. now i come back and see that firefox is acting a little weird:
it wouldn't open the first couple of times.. when it finally did, it crashed after a while.. 
when i tried it again, it worked ok but i couldn't see some stream videos ([http://www.skai.gr/master_avod.php?id=73012&cid=1485&bc=1485&lsc=1](http://www.skai.gr/master_avod.php?id=73012&cid=1485&bc=1485&lsc=1)) which i used to be able to see. Plus, i can't see flash-based sites
i had a popup telling me to install missing plugins :flashplayer and another one but i can't remember which. i went with flashplayer but it said it was already installed, so i installed the second one.
now i have no popup about missing plugins but i still cant see the video.. instead, i get a message "connecting, please wait" where the video was supposed to be.. 
i have no idea what the updates were since i always install all of them (i' m not sure if i can decide for myself correctly because i 'm relatively new to Linux)

i have ubuntu 7.10... any ideas? how can i check the updates so i can see if there was something to do with firefox, or if it's just a coincidence and i have another problem?

---

### Post by ajgreeny on 2008-02-07
The updates probably included the recent flashplugin-nonfree, so you may be correct in thinking that flash is the problem.  Try completely uninstalling it in synaptic, then rebooting or at least logging out and back in then reinstalling the flash plugin again.

Alternatively you can go to the adobe site and download the linux flashplayer from:-
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

When you unpack that archive it will contain a file called libflashplayer.so which you can manually put in the appropriate places, which on my machine are:-
/usr/lib/flashplugin-nonfree/libflashplayer.so
/home/andrew/.mozilla/plugins/libflashplayer.so

---

### Post by alejaaandro on 2008-02-07
thanks a lot... it worked just fine

---

