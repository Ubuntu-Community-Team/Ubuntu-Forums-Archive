---
title: "Can't access certain areas of GNOME"
date: 2005-05-10
forum: Installation &amp; Upgrades
---

### Post by snackzilla on 2005-05-10
Hi--

I just installed Hoary and been trying get everything set up. I noticed that several recipes involve going into System -> Administration -> Login Screen Help or User Groups, or Synaptic Program Manager, but I can't access any of it! The little cursor widget jsut spins for a few seconds and then nothing happens. I logged in as root in the terminal window, but I still can't access Login Screen Help or User Groups, and it is really frustrating me. Please help. Thanks.

---

### Post by Xian on 2005-05-10
[QUOTE=snackzilla]I just installed Hoary and been trying get everything set up. I noticed that several recipes involve going into System -> Administration -> Login Screen Help or User Groups, or Synaptic Program Manager, but I can't access any of it! [/QUOTE]
Let's try a shortcut just to troubleshoot. Open a terminal (not root) and type:

$ sudo gdmsetup
<enter password>

Does that bring up the Login Screen Setup?

---

### Post by snackzilla on 2005-05-11
> Let's try a shortcut just to troubleshoot. Open a terminal (not root) and type:
$ sudo gdmsetup
<enter password>


I just tried it and it worked. However I still couldn't access Login Setup, User Groups, and Root Terminal from GDE. 

One thing: I noticed that when I first logged into Ubuntu I got a message saying 
(and this is off the top of my head) that Ubuntu wan't configured correctly and that I need to add it to /etc/host. The only cause of this is that I use a wiresless USB adapter (Belkin F5D7050) and it porbably wasn't recognized by Ubuntu during the install, but I don't think that should be cause of the error message and hence my not being able to access certain areas of GNOME. 

Any guidance toward resolving these issues is greatly appreciated. Thanks.

---

