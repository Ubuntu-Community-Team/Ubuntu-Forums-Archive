---
title: "Flashplayer wont install"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by jayneella on 2006-09-20
Hello
Im trying to install flash player, i have downloaded it and it appears as an icon on my desktop and in my home directory, however when i type in the flash player to my command line in a console it says no such file/directory....:-({|=

---

### Post by rwabel on 2006-09-20
If I want to upgrade to the latest flashplayer from backport I get:
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
rwabel@ubuntu:~$

---

### Post by Dinerty on 2006-09-20
**Originally created by **Artifical Intelligence**

Manually:

Download Flash from here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BIOW)
to your Desktop.

Close your browser(s), to the terminal, batman

Code:

```
cd Desktop 
tar -zxf install_flash_player_7_linux.tar.gz 
cd install_flash_player_7_linux 
sudo sh flashplayer-installer
```


When you see this:

Quote:
Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla):

type: [B]/usr/lib/mozilla-firefox
[/B]
Done.

Now you need install the fonts that flash needs:

Code:

```
sudo apt-get install gsfonts-x11 
sudo fc-cache -f -v
```


Done.

---

### Post by ajgreeny on 2006-09-20
This is apparently a problem with Adobe removing the linux version of flash player from their website while they get ready to launch flash 9 for windows, according to another thread somewhere on this forum, (you might have found it if you had searched before posting).
It will get fixed (I assume) but in the meantime if you get a problem with flash missing from your system after this cock-up, you can force the version back to the original *7.0.63.3ubuntu3* using synaptic and then wait for the problem to be sorted  by Adobe

---

### Post by rwabel on 2006-09-20
this is a problem with the backport version:
[http://www.ubuntuforums.org/showthread.php?t=261179&page=2](http://www.ubuntuforums.org/showthread.php?t=261179&page=2)
[http://www.ubuntuforums.org/showthread.php?t=261363](http://www.ubuntuforums.org/showthread.php?t=261363)

---

### Post by David Oxland on 2006-10-27
> **rwabel said:**
> this is a problem with the backport version:
[http://www.ubuntuforums.org/showthread.php?t=261179&page=2](http://www.ubuntuforums.org/showthread.php?t=261179&page=2)
[http://www.ubuntuforums.org/showthread.php?t=261363](http://www.ubuntuforums.org/showthread.php?t=261363)



I'm having this problem too in that during the download process in terminal it hangs and must be force closed and says, when synatpic is run again" error occured you must run "dpkg --configure -a'"  when I do that, it hangs again so now Synaptic is unuseable.  Where to next?  This is in a fresh install of Edgy 
Thanks

---

