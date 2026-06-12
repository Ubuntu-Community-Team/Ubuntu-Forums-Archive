---
title: "Can't View Majority of SSL Websites w/ Any Browser"
date: 2015-06-22
forum: Installation &amp; Upgrades
---

### Post by Dylan_Duryee on 2015-06-22
Hey there, I'm 'newer' to Ubuntu. I've recently just installed Ubuntu w/ duel boot (Windows 7). I can't view certain SSL websites, but some I can. Whenever I try to connect, it'll state connection refused. I've looked around on the forums and some other places to see if anything will help. I read that I probably shouldn't attempt to do same things that other people had to do, just in case their error was different from mine. 

To go along with this error, I can't install anything from the 'Ubuntu Software Center'. Whenever I attempt to do so, I get the error 'The package system is broken'. If I run the command in terminal that it states (apt-get install -f), I get this error:


```

debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable(Reading database ... 170213 files and directories currently installed.)
Preparing to unpack .../libc6_2.19-0ubuntu6.6_amd64.deb ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing archive /var/cache/apt/archives/libc6_2.19-0ubuntu6.6_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.19-0ubuntu6.6_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Please help, thanks!

---

### Post by Dylan_Duryee on 2015-06-24
Hello, can someone please help? I've fixed my issue with not being able to install stuff, but I still can't view some websites.

---

### Post by Vladlenin5000 on 2015-06-25
Have you updated your system after correcting those issues? If not then do it before anything else:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

If the problem persists in a fully updated system as per above then please give us an example of a website that isn't opening.
Also try another browser just in case. Chromium is in the repositories and can be easily installed with Ubuntu Software Centre.

---

