---
title: "Ubuntu Update Server"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by paulnz on 2007-04-03
Hi,

I'm fairly new to Ubuntu but picking it up quickly after migrating three new Windows 2003 servers with the Server edition of Ubuntu. However there is one thing plaguing me still...

If I want to do an upgrade of the distribution or an update of some other sort, currently each server has to download the same packages to install itself. What I am wondering is if I can dedicate one of my servers to act as an "update" server for the other servers. I will be updating the servers in the same order each and every time, and since the servers are all functionally equivalent (they are load balancing web servers) they all require the same upgrades and updates.

I've read that apt-get looks at /etc/apt/sources.list to identify where to get updates from but I haven't read anywhere of anyone changing this to point to an internal server at all - or what location to point it to on the internal server etc. Also, would I need to perform updates a different way after this?

Hopefully someone can shed some light! There is probably another command or tool to do this but unfortunately I don't know what I don't know... :( 

Any help is much appreciated! Thanks,

Paul

---

### Post by Swab on 2007-04-03
This is a package called apt-mirror which you can install from the repos.  

More information on it here:  [http://apt-mirror.sourceforge.net/](http://apt-mirror.sourceforge.net/)

I've never used it, but it looks fairly straight forward.

---

### Post by paulnz on 2007-04-03
Thanks for your quick reply!
I had a look at apt-mirror and it may be a little overkill for my situation... However it did lead me to find apt-proxy which looks like it will do the job perfectly.

Where apt-mirror downloads all the packages and creates a true "mirror", apt-proxy simply caches the packages it downloads so it only downloads them once - perfect for what I want.

Thanks for your help! I knew there was an easy answer...

---

### Post by Swab on 2007-04-03
Great!  Hope it all works out for you :)

---

