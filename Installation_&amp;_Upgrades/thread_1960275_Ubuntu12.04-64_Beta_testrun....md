---
title: "Ubuntu12.04-64 Beta testrun..."
date: 2012-04-17
forum: Installation &amp; Upgrades
---

### Post by Cariboo1938 on 2012-04-17
Hello, 
I run Ubuntu12.04 Beta on my Laptop for testing purpose and I tried to install Startup-Manager. I got the following [COLOR="Magenta"]E: Message[/COLOR]:

> sudo apt-get install startupmanager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR="Magenta"]**E: Unable to locate package**[/COLOR] startupmanager
root@HP-Pavilion-g6-1b67ca:~# 


Can somebody tell me which repository is needed to get the 'startup-manager' installed in Ubuntu 12.04?

---

### Post by sikander3786 on 2012-04-17
Startup Manager isn't in the Precise repositories, sadly:

[http://packages.ubuntu.com/search?keywords=startupmanager&searchon=names&suite=precise&section=all](http://packages.ubuntu.com/search?keywords=startupmanager&searchon=names&suite=precise&section=all)

Don't know why they ditched it.

It used to be in the Universe repos for older releases. It is there for Oneiric:

[http://packages.ubuntu.com/search?keywords=startupmanager&searchon=names&suite=oneiric&section=all](http://packages.ubuntu.com/search?keywords=startupmanager&searchon=names&suite=oneiric&section=all)

There might be other methods of achieving what you expected from Startupmanager. What was it exactly?

---

### Post by Cariboo1938 on 2012-04-17
> **sikander3786 said:**
> Startup Manager isn't in the Precise repositories, sadly:
There might be other methods of achieving what you expected from Startupmanager. What was it exactly?
Thanks for the response:)
My boot menu looks confusing. I don't know why there are two memorytests and three Windows OS to choose from. [HERE]("http://www.psychocats.net/ubuntu/startupmanager")  is the info how to clean it up and that's what I want to do.

See also Attachment

PS.:
The way I know to do this is by comment (#) the corresponding lines with sudo gedit in /boot/grub/grub.cfg[-X  --- I know, it isn't the right way to do it.

---

### Post by Mark Phelps on 2012-04-17
Startup Manager quit working properly a while back when new Beta version of GRUB2 came out.

The better approach today (unless they've updated Startup Manager) is to use GRUB-Customizer:

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

---

