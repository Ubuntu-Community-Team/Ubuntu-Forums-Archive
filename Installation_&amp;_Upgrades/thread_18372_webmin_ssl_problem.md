---
title: "webmin ssl problem"
date: 2005-03-06
forum: Installation &amp; Upgrades
---

### Post by pocoloco on 2005-03-06
first of all great forum. It realy helped me alot sofar. I'm a newb in ubuntu, i've tryed fedora in the past. But somehow i didn't feel at home there.  8-[ 

I have this problem with webmin. After i install webmin from console with apt-get en installation went succesvol. i try to log-into webmin from my xp machine, i tryed both using the linuxbox ip on wich webmin is running:
- [http://ip](http://ip) of the box:10000
- [https://ip](https://ip) of the box:10000

In my xp machine internet explorer gives me the following error:

Error - Bad Request This web server is running in SSL mode. Try the URL [https://ubox:10000/](https://ubox:10000/). En when i click it i get nothing.
I've also tryed the webmin-ssl version with no luck

I would greatly apreciate any help

Thnx
Ron

---

### Post by pocoloco on 2005-03-07
isn't there even 1 person that can at least steer me in the right direction? :cry: 


thnx alot in advanced

---

### Post by dewey on 2005-03-07
Force that computer to have a static internal ip. ( I set mine to 192.168.1.111 )  And then, in my case, I used:
```
https://192.168.1.111:10000
``` 
And It came right up.  But I had problems with users and the like, and so have other people, I recommend compiling from source, it also gives you a newer version, with some security updates.

[edit:]Also, don't forget to setup **Port Forwarding** if connecting through a router, otherwise the packets won't know where to go.  To check if webmin is running properly, go to the machine with webmin, and browse to your own ip, port 10000, https.  If you can connect locally, but not remotely, check your port forwarding settings in your router.

---

### Post by pocoloco on 2005-03-08
thnx alot dewey. It's working now with static ip.

---

