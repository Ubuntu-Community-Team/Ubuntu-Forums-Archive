---
title: "After installation cannot login to Ubuntu Appliance Nextcloud"
date: 2020-06-17
forum: Installation &amp; Upgrades
---

### Post by shadowaero2 on 2020-06-17
[COLOR=#555555][FONT=&amp]I am still very new to both linux, ubuntu and raspberry pi's.  But can usually follow instructions well enough to do various raspberry pi projects. But i am stumped on this one. I Installed the NextCloud Ubuntu Appliance for Raspberry Pi using these instructions.
[/FONT][/COLOR]
[IMG]https://assets.ubuntu.com/v1/49a1a858-favicon-32x32.png[/IMG] [Ubuntu]("https://ubuntu.com/appliance/nextcloud/raspberry-pi")[IMG]https://help.nextcloud.com/t/nextcloud-via-ubuntu-appliance-install-issue/84977[/IMG]**[Install NextCloud on a Raspberry Pi - Ubuntu Appliance | Ubuntu]("https://ubuntu.com/appliance/nextcloud/raspberry-pi")**

Install and setup the NextCloud Ubuntu appliance on the Raspberry Pi.


[COLOR=#555555][FONT=&amp]I imported my ssh keys to ubuntu’s site here:
[https://login.ubuntu.com/ssh-keys](https://login.ubuntu.com/ssh-keys)
I am able to ssh in from my mac.[/FONT][/COLOR]
[COLOR=#555555][FONT=&amp]The raspberry pi Ubuntu Core shows this on the screen.[/FONT][/COLOR]
[COLOR=#555555][FONT=&amp]Ubuntu Core 18 on 192.168.2.130
it says my host key fingerprints
RSA xxxxxxx
ECDSA xxxxxx
ED25519 xxxxxx[/FONT][/COLOR]
[COLOR=#555555][FONT=&amp]To login:
ssh [EMAIL="username@192.168.2.130"]username@192.168.2.130[/EMAIL][/FONT][/COLOR]
[COLOR=#555555][FONT=&amp]Personalize your account at [https://login.ubuntu.com]("https://login.ubuntu.com/")[/FONT][/COLOR]
[COLOR=#555555][FONT=&amp]But i have no idea how to launch nextcloud on the raspberry pi. I also tried to use browser on mac to go to nextcloud.local and get err connection refused. Also tried in browser going to 192.168.2.130. I tried nextcloud.local:443 as well. Not sure what to do.  I set a firewall rule in router to direct http traffic to port 80 and https port 83 to raspberry pi. [/FONT][/COLOR]

---

### Post by TheFu on 2020-06-18
Did you read this? [https://ubuntu.com/appliance/nextcloud/raspberry-pi](https://ubuntu.com/appliance/nextcloud/raspberry-pi)  Seems you are missing the:

> On Raspberry Pis and PCs:

[http://nextcloud.local](http://nextcloud.local)
  On a Virtual machine:
http://<IP-of-your-appliance> 

That's not the https version.  No need for a router rule for local access. I'd disable that ASAP. Nextcloud isn't secure out of the box. Takes a few hours to properly secure any webapp before it should be placed on the internet.  They do assume you are using a supported Ubuntu Desktop release AND that avahi/mDNS is running on that desktop.

I've never used any Ubuntu "Appliances" because they require login (i.e. tracking) from Canonical. How would I manage them when the internet is down?  The point of hosting your own nextcloud instance is to have it working when the internet isn't available, at least for me.

BTW, ssh login credentials have NOTHING to do with webapp logins.  The appliance instructions should have provided an administrator account and login.  Perhaps the webapp login page has a "first time" wizard to help you setup stuff. Hopefully, some bad person on the internet didn't already find that and take over your r-pi and use it to launch other attacks.

I've been running Nextcloud a few years inside a VM, but not on a r-pi.  If something claims to be an appliance, I'd assume that the main program it supplies would startup at boot.

You can run a scan on the IP address for the r-pi to see which ports are open and available. If your ssh is working, you can use a few on-the-box commands to do the same.
```
# Open ports with listeners, not localhost
ss -lnt|egrep -v 127
netstat -tunl|grep LISTEN|grep -v 127
netstat -tulpn |grep LISTEN|grep -v 127
```

Port 443/tcp is the https, as you know.  To use that, you'll have to set it up manually, get some certs.  I've never seen that automated.  Plus, webapps like nextcloud really need to block most of the internet from having any access and only allow very specific subnets access, especially when running from your home that has other network devices.  IMHO.

Anyways, does netstat show anything?

---

### Post by jkubla2336 on 2020-07-13
I'm having the exact same problem as s[COLOR=#000000]hadowaero2.  I followed the directions at [/COLOR][https://ubuntu.com/appliance/nextcloud/raspberry-pi](https://ubuntu.com/appliance/nextcloud/raspberry-pi)
I can successfully login to the web interface, but I need to add an external hard drive.  I need to be able to SSH into the appliance in order to be able to do that.

Is there any updates as to what the problem could be.  I've retried four times now without any luck.

---

### Post by wildmanne39 on 2020-07-13
Hello and welcome to the forum jkubla2336, please start your own thread if you need support instead of posting in someone else's it get confusing for the OP and the volunteers helping in the thread and most of the time even if the issue appears the same the underlying cause is different.

---

