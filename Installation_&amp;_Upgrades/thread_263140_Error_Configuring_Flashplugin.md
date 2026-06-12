---
title: "Error Configuring Flashplugin"
date: 2006-09-22
forum: Installation &amp; Upgrades
---

### Post by Chazall1 on 2006-09-22
Today when I recieved new program updates, I did what I normaly did, Look at all the Updates to be installed, Checked Install, about half way through the process I got an additional pop up window that Stated, "Configuring Flashplugin-nonfree. This window is now coming up everytime I install or uninstall any application. The configure flashplugin-nonfree downloads and I get an ERROR message, Errors were encountered while processing E: Subprocess /usr/bin/pdkg returned an error code (1) a package failed to install Trying to recover: Setting Up flashplugin-nonfree (7.0.68-Ubuntu-dapper1)

Why is this happening, and How do I resolve this problem????????

Thanks

---

### Post by j5tixc on 2006-09-22
I'm experiencing exactly the same thing. Very annoying error, dkpg somehow tries to go to work on the file downloaded from Adobe, and that doesn't work.

EDIT: I removed the flashplugin-nonfree package and downloaded the plugin from Adobe, put it in ~/.mozilla/plugins and everything works!

---

### Post by ogami1972 on 2006-09-26
Here's what i did:
1. remove libflash-mozplugin (i used synaptic- remember to right click and choose "complete removal" so as to remove any leftover config files!)

2.remove "flashplugin-nonfree"

3. reboot ( some steps maybe unecessary, but this is EXACTLY how i did it).

4 In synaptic , go 'settings>>properties' and select 'show package properties in main window'. apply. you should now see tabs 'description', 'common', 'dependencies', etc.

5. search or whatever to find and select 'flashplugin-nonfree'. go 'package>>force version...' and select the ".o63' version ( if you do not see an 0.63 version, let me know and i will send you my sources.list).

6. Install. Reboot ( again, probably unecessary)

7. In synaptic, search or whatever to find and select flashplugin-nonfree'.
 go 'package>>lock version'. Keep it locked and watch these forums until you hear '.068' flash is working.

8. Open firefox and enjoy the latest lonelygirl15 video!:D

---

