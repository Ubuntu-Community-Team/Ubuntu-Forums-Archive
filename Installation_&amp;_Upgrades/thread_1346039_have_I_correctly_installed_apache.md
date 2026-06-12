---
title: "have I correctly installed apache?"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by Eugene_Bondarenko on 2009-12-04
Hi,

I've installed server and it seems to start successfully. I haven't yet configured any virtual hosts so I can't yet tell if it actually works but the start command doesn't return any errors. However when I go to system monitor, I can see 5 apache2 processes running? Is it correct? 

Another problem is this:
```

eugene@eugene-desktop:~$ apache2 -k stop
httpd (no pid file) not running

```

Could you please tell me what you think about this?

---

### Post by phillw on 2009-12-04
> **Eugene_Bondarenko said:**
> Hi,

I've installed server and it seems to start successfully. I haven't yet configured any virtual hosts so I can't yet tell if it actually works but the start command doesn't return any errors. However when I go to system monitor, I can see 5 apache2 processes running? Is it correct? 

Another problem is this:
```

eugene@eugene-desktop:~$ apache2 -k stop
httpd (no pid file) not running

```Could you please tell me what you think about this?
Hi,

I have 6 - and it works fine.

the way to stop apache2 is
```
/etc/init.d/apache2 stop

```the same for start, and restart if you have altered the configuration files & want it to refresh.

Regards,

Phill

---

### Post by Eugene_Bondarenko on 2009-12-04
Thanks you very much, that responds all the questions. :)

I also have another noobish question. When I was starting apache I had to change listen 80 to listen 8000. It started correctly but I am a bit curious what I actually did. :) Why didn't it start for 80? Because some other app was set to listen port 80? Also what's the point to set apache listen some specific port? As far as I understand all virtualhosts will be set to 80 and when I type [http://something](http://something), I'll be getting it, right? But what is this listen 8000 for? How or where can I use it?

---

### Post by phillw on 2009-12-04
> **Eugene_Bondarenko said:**
> Thanks you very much, that responds all the questions. :)

I also have another noobish question. When I was starting apache I had to change listen 80 to listen 8000. It started correctly but I am a bit curious what I actually did. :) Why didn't it start for 80? Because some other app was set to listen port 80? Also what's the point to set apache listen some specific port? As far as I understand all virtualhosts will be set to 80 and when I type [http://something](http://something), I'll be getting it, right? But what is this listen 8000 for? How or where can I use it?

There's some good documents on apache2 over here -->  [http://httpd.apache.org/docs/2.0/misc/tutorials.html](http://httpd.apache.org/docs/2.0/misc/tutorials.html)

Regards,

Phill.

---

### Post by Eugene_Bondarenko on 2009-12-04
Thanks, I've successfully set up and understood everything :)

---

