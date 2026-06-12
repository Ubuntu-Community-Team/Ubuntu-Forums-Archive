---
title: "Which Install Method?"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by maxweld on 2007-07-06
I am about to do a complete fresh install of Ubuntu 7.04 for my main machine at home.

This machine will acts as both my desktop, and as a server for a couple of other machines on my home network. In its capacity as a server it is used as a file server, mail server, and web server (LAMP). On the desktop, I use Gnome.

I am a keen user of LVM, and would like to set this up from the install, if at all possible. I am also interested in LTSP, as I have a couple of older machines which could perhaps be usefully deployed as thin clients.

Can you suggest which install method/CD image to use as the basis?
Thanks

---

### Post by reckless2k2 on 2007-07-06
you can really use any images you want. either way you are going to have to install additional packages. if you go with the server image, you'll need to install ubuntu-desktop to get a gui frontend. if you install the desktop image, you'll need to install the servers after. the advantage of the desktop is that you can specify which servers you'd like to use and such. LAMP on the server image might give you more than what you need to ubuntu specific recommendations you might not want or need. for instance, i use zimbra for mail server rather than the ubuntu stock postfix.

---

