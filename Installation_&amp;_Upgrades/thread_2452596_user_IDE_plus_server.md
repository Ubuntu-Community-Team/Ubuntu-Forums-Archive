---
title: "user IDE plus server?"
date: 2020-10-25
forum: Installation &amp; Upgrades
---

### Post by workaround on 2020-10-25
This is my Ubuntu version.  


 No LSB modules are available.
 Distributor ID:	Ubuntu
 Description:	Ubuntu 20.04.1 LTS
 Release:	20.04
 Codename:	focal
 
 
 Can I install server next to it or on top of it? I previously installed Server first but would not boot. I dot have installed windows.
Thanks.

---

### Post by TheFu on 2020-10-25
What do you mean my "server?"  Which server?  Apache, Postgressql, wireguard, plex, nfs, 20,000 others?  If you have any version of Ubuntu installed, just install the specific "server" packages you want.

If you need a GUI, install a desktop ISO of Ubuntu.

If you don't want the bloat from any GUI/Desktop, install Ubuntu Server, but be prepared to configure everything using text config files with an editor. There ain't no GUI on servers.

If you install Ubuntu Server, then add on a DE/Window Manager later, things that desktop users expect to work, don't.  The internal configuration are still server the server-way, so you'll need to use the text config files for many things.  That's the price.  OTOH, not having network-manager nor avahi is a huge plus in my book. If only systemd-resolved and resolvconf weren't installed ... er ... ever, I'd be much happier.

IDE? You've completely lost me there.  "Ubuntu Server" doesn't have a GUI, so the only real IDE available would be emacs, but that's almost a complete OS unto itself from back before computers had graphics cards and windows.  Even I, mainly a server-guy, would hate not to have a workstation with a GUI to have my multiple terminals to do software development. That's my "IDE".  I use a powerful editor with extensions for the language in 1 terminal, another term for the debugger, another term for manpages and a browser to web-search or access my existing documentation.  My professional code has embedded documentation inside that gets pulled out to create the official documentation for each class/function/method and how it is used, but that's a function of both the language AND the development tools provided.

---

### Post by workaround on 2020-10-25
Sorry not being clear about it. When I installed Ubuntu server it would not boot from hard drive at all. So I installed windows that fixed the partition table and I installed desktop Ubuntu and took out the windows since I don't need it. My question is if I can install Ubuntu server now or does it have to be the other way: install Ubuntu server first and then install the desktop Ubuntu?
When I try to install server Ubuntu first it just messes up the boot and will not boot up!?  Also, I get this partition overlap error!?
Thanks.

---

### Post by SeijiSensei on 2020-10-26
You don't need to install the Server version just to run server software. Identify the services you want to offer -- web, mail, file sharing, etc. -- and install the necessary packages on your existing distribution. The difference between the server and desktop versions are (1) the Server version has no graphical interface; and (2) that version includes packages like the Apache web server not present in the desktop releases. For instance, if you're looking to provide web services (e.g., WordPress) I recommend installing the "lamp-server" package:
```
sudo apt install lamp-server^
```
(mind the circumflex "^"). That will install Apache, MySQL, PHP and any interstitial packages they require.

---

### Post by workaround on 2020-10-26
So, are you saying I can as well install Apache, PHP, and MySQL and do development if I would want it to including running the Apache server? Thanks.
I just noticed below the "CODE" your comment that it will install all these packages, so no further comments. Thanks

---

