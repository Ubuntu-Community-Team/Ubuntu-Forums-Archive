---
title: "¨Upgrade - Failed - Ubuntu 16.04 LTS to 18.04 LTS¨."
date: 2019-04-20
forum: Installation &amp; Upgrades
---

### Post by ronnie-vc10 on 2019-04-20
[ATTACH=CONFIG]283063[/ATTACH] Hello, I have just responded to the Ubuntu facility  

 ¨Upgrade available for Ubuntu 16.04 LTS to 18.04 LTS¨.

 
 
 Before upgrading, I ensured that the 16.04 LTS system was fully updated.  

 I then clicked on the Ubuntu 18.04 LTS upgrade installation icon.  
 The software download completed successfully, and the ¨18.04 LTS Beaver¨ Desktop was shown.
 
 
 Due to other commitments, I delayed installing additional software on the new 18.04 LTS and shut down the system.
 
 
 Later, in starting the new 18.04 LTS it showed the 18.04 LTS Desktop ¨without any icons¨, but it now showed 3 animated chevrons coming from the bottom of screen (see attached image).

 
 
 As this has been like this for 2 days now, and I cannot get any icons or access Terminal etc. Can anyone tell me what is [or not] happening, ie is the system still downloading upgrades / installing software?
 
 
 I have tried closing / shutting down and rebooting, but Desktop is still as above!
 
 
 What are the options available to assist me get the Desktop back on the Ubuntu 18.04 LTS system?
 
 
 My PC is a cirrus7 nimbus with SSD.	
 Operating System: 64-bit.  
 
 
 Thank you in advance for any offers of help from Forum members.
 
 
 Ronnie

---

### Post by westie457 on 2019-04-20
Is the pic before or after you have logged in?

There is a number of ways to fix this.
One is using a 'tty' terminal, usually Ctrl+Alt+F2 keys. Log in here and run a few commands, then Ctrl+Alt+F7 to get back to the GUI.
Another way is via the Grub menu and 'Rescue Mode' drop to a 'Root Terminal' and run a few commands, the final command here will be 'reboot'.

Which route you choose to take the commands will be the same except the 'tty' will need 'sudo' to work.
Below is the 'Root' commands - no sudo needed here```
dpkg --configure -a
apt install -f
apt update
apt upgrade
```

If you use the root terminal use a wired connection. If you use the tty wireless should still work, if not then plug a cable in.

Repeat the commands until 'dpkg' returns an empty line and 'apt' reports everything is up to date.

---

### Post by Dennis N on 2019-04-20
> Later, in starting the new 18.04 LTS it showed the 18.04 LTS Desktop ¨without any icons¨, but it now showed 3 animated chevrons coming from the bottom of screen (see attached image). As this has been like this for 2 days now, and I cannot get any icons or access Terminal etc.

The image is Ubuntu's lock screen. But I don't see the top panel, which is not a good sign. Normally, typing anything here should immediately reveal the regular log in screen. Does it? How did you get a screenshot if nothing works?

---

