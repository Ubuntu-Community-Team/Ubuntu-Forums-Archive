---
title: "Cant use apt-get update.. or the update manager"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by boon4376 on 2007-10-29
ok so i have no idea how i broke this,.. but anyways, whenever i run apt-get update, or try and check for updates using the update manager  get these errors:

Update manager:

[QUOTE=UpdateManager]
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181[/QUOTE]

apt-get update:
[QUOTE=apt-get update]
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Get:5 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Translation-en_US
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release
  
Get:6 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release [26.9kB]
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Packages
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Sources        
Fetched 27.1kB in 6s (4369B/s)                                                 
Reading package lists... Done
[B]W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181
W: You may want to run apt-get update to correct these problems[/B]
[/QUOTE]

I've tried reseting the synaptic authentication keys to default, but that doesnt work. Any ideas?

Im using 7.10 , so why is it trying to get fiesty stuff?

---

### Post by Pumalite on 2007-10-29
You have to get the key for tuxfamily org, or comment it out in your sources.list.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

---

### Post by taurus on 2007-10-29
> **boon4376 said:**
> ok so i have no idea how i broke this,.. but anyways, whenever i run apt-get update, or try and check for updates using the update manager  get these errors:

Update manager:

apt-get update:

I've tried reseting the synaptic authentication keys to default, but that doesnt work. Any ideas?

**Im using 7.10 , so why is it trying to get fiesty stuff?**

Did you add that repo to your /etc/apt/sources.list?

---

### Post by JBAlaska on 2007-10-29
The GUI way: Go to System, Administration, Software sources, third party tab and unchech all lines that reference feisty, reload and try apt-get again

---

### Post by Pumalite on 2007-10-29
Most probably this is an upgrade and Feisty repos were left behind, so in that case; comment them out.
The funny thing is that is asking for the key.

---

### Post by Leetbumble on 2007-11-10
I was getting the same error for avant window navigator (gutsy) and (edgy). I just removed both the source lists to get rid of the error until I figure out what I did wrong... 

AWN runs perfect though so i dont know what could be wrong

---

