---
title: "problem installing skype 4.2.0.11 on ubuntu 12.04"
date: 2013-10-02
forum: Installation &amp; Upgrades
---

### Post by albert13 on 2013-10-02
Hi all!

I need some help and I hope that someone will have the answer.

Yesterday, I installed skype 4.2.0.11 on ubuntu 12.04 but after rebooting skype a couple of times I experienced a bug, basically it crashed, so I did some search on the net and I used the following commands to remove the app (which is impossible to find in "ubuntu software center"):

sudo apt-get remove skype
sudo apt-get remove skype-bin
sudo apt-get purge skype
sudo apt-get autoremove

after I used these commands, I tried to reinstall the app which I downloaded from skype website (.deb file). I got these lines back (unable to reinstall the app)

Unpacking skype:i386 (from .../skype-ubuntu-precise_4.2.0.11-1_i386.deb) ... 
dpkg: error processing /home/xxxx/Downloads/skype-ubuntu-precise_4.2.0.11-1_i386.deb (--install): 
 trying to overwrite '/usr/share/icons/hicolor/32x32/apps/skype.png', which is also in package skype3.0.0.93-mt 1-2 
dpkg-deb (subprocess): data: internal gzip write error: Broken pipe 
dpkg-deb: error: subprocess <decompress> returned error exit status 2 
dpkg-deb (subprocess): failed in write on buffer copy for failed to write to pipe in copy: Broken pipe 
Processing triggers for hicolor-icon-theme ... 
Errors were encountered while processing: 
 /home/xxxx/Downloads/skype-ubuntu-precise_4.2.0.11-1_i386.deb

Please need help! I use skype daily at work.

Thanks in advance!!

---

### Post by ajgreeny on 2013-10-02
If you enable the canonical-partner repos in your software-sources you can install skype through the normal channels and it may resolve your problems.

Go to the **Other Software** tab and tick the box, then refrersh; job done hopefully.

PS: I suggest you try to use synaptic package manager rather than software-centre; it is by far the better package manager of those available, in my opinion.

---

