---
title: "trouble installing anything on gutsy"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by henrico on 2008-04-21
whenever I try 'sudo aptitude install [whatever]' or 'sudo apt-get install [whatever]' in Terminal, I get the message: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

Then, I run 'sudo dpkg --configure -a'. The following happens:

Setting up flashplugin-nonfree (9.0.124.0ubuntu1~gutsy1) ...
Downloading...
--00:07:46--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 84.53.154.70
Connecting to fpdownload.macromedia.com|84.53.154.70|:80... 

(*A few weeks before this problem, I wanted to get a flash player for internet content, trying all sorts of things* :-?). The abovementioned happens and it just never ends (It keeps reconnecting,struggling to connect to a website even though my internet connection is open)

Please Help

---

### Post by bapoumba on 2008-04-25
Sorry to be so late answering. It happened to me too, when upgrading flashplugin behind my corporate network proxy. I took the laptop home, no proxy on my network, and finished the upgrade. I had the exact same error message. I did not investigate further but my guess is that the proxy did not allow downloading on port 80.

---

