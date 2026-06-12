---
title: "[SOLVED] Installing flash plugin"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by Manu S S on 2008-07-31
I am using Ubuntu 7.04 Gutsy. I want to install flash player plugin for my firefox browser. All search results in google explained terminal command methods for installing it. They seem too complex... A few of them did not work too. Is there any way to install flash player plugin for Firefox browser automatically without any terminal commands? Thanks in advance...

---

### Post by iaculallad on 2008-07-31
The terminal would be your closest ally:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Manu S S on 2008-07-31
When I tried it I get this message.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 215 not upgraded.
Need to get 18.2kB of archives.
After unpacking 160kB of additional disk space will be used.
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/multiverse flashplugin-nonfree 9.0.124.0ubuntu1~gutsy1
  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu1~gutsy1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu1~gutsy1_i386.deb)  404 Not Found [IP: 91.189.88.45 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by Manu S S on 2008-07-31
What could be the problem? And how to solve it?

---

### Post by iaculallad on 2008-07-31
The download server for the package cannot be reach. Try to change your download server to point to "Main Server".

System->Administration->Software Sources, under the "Ubuntu Software" tab. Check all the values for Main, Multiverse, Restricted, and Universe. Change the "Download From:" to point to "Main Server". Click on Close and choose Reload on the next window that pops up. After that, you could again drop to your terminal and issue the command a posted a while ago.

---

### Post by Manu S S on 2008-07-31
The above process worked and it was written in my terminal that download completed and install completed. But even after restarting my machine I am unable to see Youtube videos or use chat in Yahoo mail... A message comes saying you to have Flash player 9.0 or higher installed...

---

### Post by Manu S S on 2008-07-31
When I try the command again, it gave the message...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 215 not upgraded.

---

### Post by nukleuzN on 2008-07-31
Reading package lists... Done
Building dependency tree
Reading state information... Done
**flashplugin-nonfree is already the newest version.**
0 upgraded, 0 newly installed, 0 to remove and 215 not upgraded.

What kind of browser do you use?! FireFox?

---

### Post by nukleuzN on 2008-07-31
How do i delete post's?!

---

### Post by Manu S S on 2008-07-31
Yes, I use Firefox browser...

---

### Post by aysiu on 2008-07-31
> **Manu S S said:**
> I am using Ubuntu 7.04 Gutsy. I want to install flash player plugin for my firefox browser. All search results in google explained terminal command methods for installing it. They seem too complex... A few of them did not work too. Is there any way to install flash player plugin for Firefox browser automatically without any terminal commands? Thanks in advance... This tutorial explains how to do it without terminal commands:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

**But...**

> **Manu S S said:**
> When I try the command again, it gave the message...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
**flashplugin-nonfree is already the newest version.**
0 upgraded, 0 newly installed, 0 to remove and 215 not upgraded. You appear to already have Flash installed.

What happens when you visit a page that needs Flash?

---

### Post by voteforpedro36 on 2008-07-31
Does just going to a site with Flash prompt you to install it? It did for me.

EDIT: My bad, I'm late.

---

### Post by Manu S S on 2008-08-01
The prolblem got solved... Flash player 9.0 had indeed installed in my system. I could see the flash player version as 9.0 in synaptic package manager but when I typed about: plugins in firefox window it listed an 8.0 version. So I had to copy the plugin file from flashplugin-nonfree folder in /usr/lib into my firefox plugin folder. Upon doing this step I could see flash content in firefox. Anyway thanks a lot to all who helped me in this forum... :)

---

