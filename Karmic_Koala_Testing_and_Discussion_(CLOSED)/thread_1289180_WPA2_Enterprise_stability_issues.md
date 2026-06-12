---
title: "WPA2 Enterprise stability issues"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Joshua Lückers on 2009-10-12
At school they use WPA2 Enterprise with Tunneled TLS and PAP.
Since a week or so my connection is unstable, it doesn't disconnect but sometimes it takes ages before a webpage loads.. 
I also tunnel via ssh to a server at school so I can evade the proxy (which is allowed for us IT students) but the ssh connection doesnt stay alive thanks to the stability issue.

How can I find out what my problem might be? It does work fine in Ubuntu 9.04.

---

### Post by slakkie on 2009-10-12
For the time being, add the Jaunty repo's to your sources.list

Add the following bit into /etc/apt/preferences:

```

Package: *
Pin: release o=Ubuntu,a=karmic
Pin-Priority: 550

```

This is to allow jaunty packages to be installed, but it will prefer karmic.

Then run aptitude update. Install the network-manager of Jaunty:

```

aptitude install network-manager=0.7.1~rc4.1.cf199a964-0ubuntu2

```

This will downgrade your network-manager package.

Another solution is to add the PPA of the network-manager devs:

```

# sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BC8EBFE8
deb http://ppa.launchpad.net/network-manager/trunk/ubuntu karmic main
#deb-src http://ppa.launchpad.net/network-manager/trunk/ubuntu karmic main

```

Since I assume you have that /etc/apt/preferences file, 

```

aptitude install network-manager=0.8~a~git.20091009t060001.bc653d2-0ubuntu1~nmt1

```

And see if it is fixed in the new package. Otherwise, file a bug report or join #nm on freenode.

---

### Post by Joshua Lückers on 2009-10-12
Thanks. I will try to use the latest network-mananger by adding the PPA.

---

### Post by MALEADt on 2009-10-12
> **Joshua Lückers said:**
> At school they use WPA2 Enterprise with Tunneled TLS and PAP.
Since a week or so my connection is unstable, it doesn't disconnect but sometimes it takes ages before a webpage loads.. 
I also tunnel via ssh to a server at school so I can evade the proxy (which is allowed for us IT students) but the ssh connection doesnt stay alive thanks to the stability issue.

How can I find out what my problem might be? It does work fine in Ubuntu 9.04.

+1 on difficulties, but not the issues you describe. It seems in here that the connection gets lost, after which the driver isn't able to scan for AP's anymore. I need to look closer at it though.

---

### Post by Joshua Lückers on 2009-10-14
I have collected a log of what NetworkManager does: [http://pastebin.com/me0a0b81](http://pastebin.com/me0a0b81)
Any ideas what my issue might be?

---

