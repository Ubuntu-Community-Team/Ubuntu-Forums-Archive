---
title: "[SOLVED] problems installing flash plugins in firefox"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by IanB2 on 2008-05-18
I hope someone can help.

I'm running xubuntu 8.04 and have just done a second fresh install in trying to eliminate this problem. I'm unable to install any of the three flash plugins in firefox. As far as I can tell the sources file is OK as I've been installing applications from multiverse with no problems.

During for example the adobe flash install I get the following error message: 

'W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb)
  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)'

I get the same results with any of the other flash plugins.

---

### Post by Partyboi2 on 2008-05-19
Are you using a proxy?

---

### Post by IanB2 on 2008-05-19
Thanks ..... I'm kind of newish to Linux and remember (dimly) setting up some parental controls on my other ubuntu box using a proxy server (although I don't really understand how it works ... but it does!).

As I couldn't get foxmarks add-on to work in Firefox 3, I copied the .mozilla folder from my home directory to the laptop. This of course imported the same settings and cause the error message. I've renamed the .mozilla folder and relaunched Firefox to get back to the default settings. I was then able to install the flash plugin.

Sometimes the obvious is easy to miss!

---

