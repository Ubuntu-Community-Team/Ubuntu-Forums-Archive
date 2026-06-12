---
title: "Intrepid upgrade broken my lirc settings"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by AndrewWalker on 2008-11-10
I did have lirc working perfectly with hardy but upgrading to intrepid broke it again. The problem I have is with a winTV -nova-T card (not a nova-T 500).
With hardy it worked correctly except the remote conf file  /usr/share/lirc/remotes/hauppauge/lircd.conf.nova-t
was incorrect. All the buttons worked except back/exit which was incorrectly mapped. I could edit that button and all was well. 
After upgrading to Intrepid however, lirc went back to a broken back/exit button and the /usr/share/lirc/remotes/hauppauge/lircd.conf.nova-t file no longer works or even exists in the lirc package.
I tried to reconfigure lirc but my remote no longer even exists as an option, the nova-T 500 exists but it's a different card and whilst my remote still works, I have no idea which script controls it and therefore can't re-edit it to get the incorrect button to work. Also /dev/lirc0 no longer exists and with lirc daemon stopped my remote control still works with mythtv with the usual problem but how? 
Can anyone give me a clue where to look? This all looks pretty screwed up to me!

---

