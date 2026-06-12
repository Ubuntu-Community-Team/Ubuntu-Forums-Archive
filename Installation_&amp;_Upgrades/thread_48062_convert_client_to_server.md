---
title: "convert client to server"
date: 2005-07-11
forum: Installation &amp; Upgrades
---

### Post by viniosity on 2005-07-11
I did a default install of Hoary on a computer I am using as a server.  Not only did I get a bunch of packages I don't need, but a side effect is that i can't use VNC without actually being logged into the machine.  So if for some reason I need to restart the server VNC becomes useless.

Is there some way to scale back the install so that I can get to the minimal set of packages that would have presumably been installed had I selected the server install?

---

### Post by magoo on 2005-07-11
What do you want to use VNC for on a server?
You ain't going to manage it "à-la" micro$oft, no? (click and ride)  :grin: 

If you have good knowledge in the packages you need, deborphan is cool but use it at your own risks.

but my advise would be to reinstall it from scratch then you know what's on.

I don't know if ubuntu uses the tasksel function of debian. It enables you to do what you are looking for. But be carefull if it is not ubuntu-proof.

btw, server install give something like 280MB of system, no X, no sshd by default (at least for debian).It is REALLY stripped down.
I will have to try the ubuntu server setup once.

---

