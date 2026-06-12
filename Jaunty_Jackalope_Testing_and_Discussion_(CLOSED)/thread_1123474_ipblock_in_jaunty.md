---
title: "ipblock in jaunty"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mbw290 on 2009-04-12
I installed ipblock in Jaunty Alpha and when I try to run the gui nothing happens.  Anyone know how I can get this to work, or get another ipblocker

---

### Post by lovinglinux on 2009-04-12
You can use [moblock](http://moblock-deb.sourceforge.net/), which is very good. I didn't test it on Jaunty, but I guess there is a package for it.

You can also install mobloquer, which is a GUI for moblock.

For support see [http://ubuntuforums.org/showthread.php?t=803183](http://ubuntuforums.org/showthread.php?t=803183)

---

### Post by mbw290 on 2009-04-12
I don't see a jaunty package.  Is there possible that there isn't one?

---

### Post by mbw290 on 2009-04-12
Nevermind.  I got the program installed.  How do I determine the ports I need to enter to configure it?

---

### Post by uljanow on 2009-04-12
I have uploaded iplist-0.25 to the repo, should be finished in 10min. I'll also update the installation instructions for jaunty.

---

### Post by mbw290 on 2009-04-12
Thanks Where can I find these?

---

### Post by uljanow on 2009-04-12
In a few minutes at [http://ppa.launchpad.net/ssakar/ppa/ubuntu/pool/main/i/iplist/](http://ppa.launchpad.net/ssakar/ppa/ubuntu/pool/main/i/iplist/) .

But to use the repo try this:
```
sudo wget [http://iplist.sf.net/sources.list.d/jaunty.list](http://iplist.sf.net/sources.list.d/jaunty.list) -O /etc/apt/sources.list.d/iplist.list
```

---

### Post by lovinglinux on 2009-04-12
> **mbw290 said:**
> Thanks Where can I find these?

If you download the new version of iplist, then uninstall moblock first, otherwise they will conflict with each other.

---

### Post by mbw290 on 2009-04-12
How do I determine which ports to enter while configuring moblock?

---

### Post by lovinglinux on 2009-04-12
> **mbw290 said:**
> How do I determine which ports to enter while configuring moblock?

These are ports to be whitelisted, which means any traffic passing through them will not be checked by moblock. You can specify outgoing ports or incoming ports to be whitelisted. Which ports you will whitelist depends on what you need. You only whitelist ports that you don't want to be checked by moblock.

You should whitelist a port only when you need to allow a large number of IPs to connect and you get many of them blocked by moblock. If you need to whitelist just a few IPs, then you should whitelist them using the allow.p2p file, instead of whitelisting the port in the config. Whitelisting IPs is more secure than whitelisting ports, because you will only allow trusted IPs to connect. 

For example, if you use moblock just to filter p2p connections, then you probably be safe to whitelist outgoing connections on http and https (ports 80 and 443). You don't have to whitelist incoming connections on those ports tho. Nevertheless, some p2p peers with bad intentions can specify their torrent client to use incoming port 80 or 443, so they won't be blocked by your moblock when you request the connection.

I used to block http and https outgoing connections, but it was kind of annoying, since my ip lists are huge and many trusted sites were blocked. So I decided to allow outgoing connections on http ports. But I also use Deluge's blocklist plugin, so even if a bad peer uses port 80 to receive connections, my torrent client will not try to connect to it. This way I can surf the web without hassle while using torrent, without worrying about unwanted p2p connections on port 80.

If you want to use moblock to protect you from dangerous web sites, then you should not whitelist http ports. If you still get many trusted sites blocked, then you should consider changing the ip lists instead of whitelisting the port.

Could you please tell why you are using moblock so I can recommend a specific configuration for you?

---

### Post by mbw290 on 2009-04-12
I really appreciate your help!  I simply wish to use moblock for torrenting.

---

### Post by lovinglinux on 2009-04-12
> **mbw290 said:**
> I really appreciate your help!  I simply wish to use moblock for torrenting.

So I think you will be fine whitelisting http and https outgoing connections only. Never whitelist the port used by the torrent client. If you use Deluge, you can specify incoming and outgoing ports, so you get a better control of what is filtered and what is not. Torrent applications usually use 6881-6889 port range, but some ISPs throttle traffic on these ports, so it might be a good idea to use a port in the range between 49152 and 65535. 

It is a good idea to monitor moblock's logs, to determine if other clients activities are being blocked (like IM, FTP etc). You can always add or remove whitelisted ports by editing */etc/blockcontrol/blockcontrol.conf*. Simply add the following line:

```
WHITE_TCP_OUT="http https"
```

Additionally, mobloquer offers an easy way to modify whitelisted IPs and ports using a GUI.

Please notice that some people use non-standard ports for torrent (http, https, ftp and others). You never know if they use those ports because they don't know about port standards or if they are up to something. If you are really paranoid like me, you can use the torrent client blocklist feature as an additional layer of security.

You could also not whitelist any ports and just allow the IPs of web sites you visit on-demand. This would be the safest method.

Don't forget that if you use a firewall manager like Firstarter or UFW, then you should start moblock after you start the firewall manager, otherwise moblock's rules won't work.

---

### Post by pelle.k on 2009-04-15
@uljanov
I'm guessing you need to replace the dependency java6-runtime with somthing that provides it, like say default-jre, openjdk-6-jre or sun-java6-jre
This is what happens when you i tried installing iplist_0.25-0ubuntu1~jaunty_i386.deb
> This package is uninstallable
Dependency is not satisfiable: java6-runtime

btw, thanks for all the (hard?) work you've put into this app...!

---

