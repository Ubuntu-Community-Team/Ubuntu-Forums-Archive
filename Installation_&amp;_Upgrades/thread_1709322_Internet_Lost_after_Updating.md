---
title: "Internet Lost after Updating"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by njspidey on 2011-03-18
I partial updated the ubuntu packages after repeated messages. Finally it asked me to delete obsolete files and I clicked Ok.
After some time the wireless internet Icon on the top right corner disappered.

Now I cant connect to internet by my router either wireless or wired. My wlan drivers are ok too. There seem to be no network whatsoever.

pls help asap

---

### Post by Dutch70 on 2011-03-18
Welcome to UF

First try this...
Open a terminal and type nm-applet & press enter.

If that doesn't work, you may have to reinstall network manager. I believe this is the command. 
```
sudo apt-get install network-manager
```

Also, you can right click on your top panel, select "add to panel" and look in that list for nm-applet.

---

