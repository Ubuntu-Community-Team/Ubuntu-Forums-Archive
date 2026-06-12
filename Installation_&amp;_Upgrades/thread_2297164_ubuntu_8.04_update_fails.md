---
title: "ubuntu 8.04 update fails"
date: 2015-10-01
forum: Installation &amp; Upgrades
---

### Post by bruce39 on 2015-10-01
NEW to ubuntu. I have installed ubuntu 14.04.3 on my Dell optliplex GX620 and it ran somewhat jurky or slow. I cleared the HD and installed 8.04. It is much more to my liking. The install even found the onboard spearker. First time since XP. Any way when I run avalable updates it fails to connect. Please see attachment.
 [ATTACH=CONFIG]264770[/ATTACH]

I hope I can continue with 8.04. Yes I know I can but arn't the update helpful?

---

### Post by howefield on 2015-10-01
8.04 is several years past end of life and therefore no longer supported. You could point your sources.list to old.releases but this release no longer gets updates so not remotely recommended, not even slightly. Better to try a currently supported lighter version of Ubuntu, eg, Xubuntu or perhaps Lubuntu.

---

### Post by bruce39 on 2015-10-01
Thanks. Didn't know there was X or L Ubuntu. The main reason is to learn LinuxCNC which version would be best?

---

### Post by Bucky Ball on 2015-10-01
Welcome. [LinuxCNC looks obsolete]("http://linuxcnc.org/index.php/english/download") also as it was based on 8.04 LTS and then 10.04 LTS, both of which are unsupported. 

It also looks like the only download is an ISO, meaning, it is a full install in itself. You don't install it as an application and use it in an operating system. LinuxCNC is one! :)

As the project looks defunct, you could check the apps it was using and see if you could replicate it with a minimal install of Ubuntu (just the kernel) then add the applications you need only. :-k

---

### Post by grahammechanical on 2015-10-01
It is still under development with a new version released just about a month ago.

[http://linuxcnc.org/index.php/english/news](http://linuxcnc.org/index.php/english/news)

It can be installed on precise (12.04). Which is supported up to April 2017.

[http://linuxcnc.org/docs/2.7/html/getting-started/getting-linuxcnc.html](http://linuxcnc.org/docs/2.7/html/getting-started/getting-linuxcnc.html)

Regards.

---

### Post by Bucky Ball on 2015-10-02
Good news. I dug but didn't find so nice. :)

---

