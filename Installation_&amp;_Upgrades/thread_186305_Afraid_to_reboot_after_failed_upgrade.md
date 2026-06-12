---
title: "Afraid to reboot after failed upgrade"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by txinga on 2006-06-01
I changed every occurrence of "breezy" to "dapper" in sources.list:-k 
Then did sudo apt-get update && sudo apt-get dist-upgrade
During the download of the 1500+ packages had a few failures. 
Ran sudo apt-get update --fix-missing
Then sudo apt-get dist-upgrade again then got some more errors
don't know what to do now. system still runs kinda. I'm downloading the desktop cd right now thinking I'm probably going to have to do a clean install. Cannot run updates cause of broken package. Cant fix package cause synaptic won't accept my password now.
Hmm....

Update: Well I had to reboot after all. Did a ctrl+alt+backspace to see what version I had and couldn't get back into system. Now the gui is gone. Ran dpkg-reconfigure xserver-xorg and it's missing dependencies. 

Running sudo apt-get -f install now...

---

### Post by txinga on 2006-06-01
well I guess it's just too fried at this point. guess I'll shut er down and rebuild it from scratch now. Bummer

---

### Post by ubuntu_demon on 2006-06-01
see : [https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)
the troubleshooting section below gives some information.

regarding the failed upgrade look here :
[http://www.ubuntuforums.org/showthread.php?t=186325](http://www.ubuntuforums.org/showthread.php?t=186325)

regarding the graphics problem start here :
[http://www.ubuntuforums.org/showthread.php?t=186311](http://www.ubuntuforums.org/showthread.php?t=186311)

I'm going to sleep soon. Good luck!

---

### Post by txinga on 2006-06-01
Well after the console update finished with lots of xorg failures I rebooted and xfce came up. Hmm... So I downloaded gnome desktop and it all seems to be working again. That was a weird experience.

All my desktop settings from before are there. All my docs etc. Thank you Lord.

---

### Post by txinga on 2006-06-01
Well after the console update finished with lots of xorg failures I rebooted and xfce came up. Hmm... So I downloaded gnome desktop and it all seems to be working again. That was a weird experience.

All my desktop settings from before are there. All my docs etc. Thank you Lord.

---

### Post by ubuntu_demon on 2006-06-01
no problem :)

I'm going to sleep now. Good bye !

---

