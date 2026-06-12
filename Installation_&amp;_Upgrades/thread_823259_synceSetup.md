---
title: "synceSetup"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by intruderukr on 2008-06-09
I'm still trying to sync my ipaq mobile 5 device.  Am trying to follow these instructions:
[COLOR="Red"]Check existence of needed plugin

Run the following command:

$ msynctool --listplugins

This will list all the available plugins and one that must be present is the following:

synce-opensync-plugin

If you don't see the above plugin in the output of msynctool, then download the plugin and copy this file to /usr/lib/opensync/python-plugins. After that, when you rerun msynctool --listplugins you should see the synce-opensync-plugin in the output and you can continue with creating an opensync group. [/COLOR]
 but I'm not able to create a new folder in the lib directory.   I'm not familiar enough with the terminal to do that.  Please send me simple instructions...please?
thanks!

---

### Post by Partyboi2 on 2008-06-09
To do it the gui way you can press Alt+f2 and type in 
```
gksudo nautilus
```
This will open up nautilus the file manager with admin rights which will allow you to copy and paste the file to /lib directory

---

### Post by maxpathan on 2008-06-09
I have followed the wiki pages to install sync etc to get my HTC Kaiser (running windows 6) to syc with Ubuntu.

It seems to work, in that it prompts if I want to replace or duplicate contact entires, to which I enter replace.

However I added an extra contact on my pocket pc, but it did not sync it with Evolution? When I look at the ActivSync prog on my mobile, it says it shows that the pocketpc was synced with LINUX.

Any idea what I need to do to get this to work. Sorry for the lack of details, but I am not in front of my Ubuntu PC.

Max

---

