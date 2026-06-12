---
title: "Gui Apps in cron not working"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by swamisant on 2009-10-17
I am unable to launch any gui application using crontab. I am able to open some script like one is to reboot the modem. But it does not work for gui apps. I followed [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto), but no luck.

My sample crontab file is as below : 

[I]10 10 * * * routerreboot.exp
11 10 * * * env DISPLAY=:0 exaile[/I]

Out of these two jobs first runs properly but second does not.I have also tried with DISPLAY=:0.0 option. Please help me.

---

### Post by FuturePilot on 2009-10-17
Try using this for the display part
```
export DISPLAY=:0
```

---

### Post by swamisant on 2009-10-17
> **FuturePilot said:**
> Try using this for the display part
```
export DISPLAY=:0
```

No luck.......

---

### Post by unikuser on 2009-10-17
Something changed in karmic recently regarding default X acls(access control lists)

[http://www.leidinger.net/X/xhost.html](http://www.leidinger.net/X/xhost.html)

You have to add access to localhost for Xserver to connect to.
```

 ~$xhost +local:
non-network local connections being added to access control list
 ~$xhost
access control enabled, only authorized clients can connect
**LOCAL:**
..

```

If this does not work, **xhost +** will completely disable ACL. But, use at your own risk ;)

---

### Post by swamisant on 2009-10-17
^^^

Thanks. Disabling acl did the trick. What is the risk once we disable acl?

---

### Post by maverickmint on 2009-10-17
Hey I am also having the same issue, tried disabling the ACL. Please see below.

root@maverick-laptop:~# xhost +
access control disabled, clients can connect from any host

The cron is

maverick@maverick-laptop:~$ crontab -l
01 21 * * * export DISPLAY=:0 /usr/bin/thunderbird

and the syslog says

Oct 17 21:01:01 maverick-laptop CRON[3171]: (maverick) CMD (export DISPLAY=:0 /usr/bin/thunderbird)

Any idea?

---

### Post by swamisant on 2009-10-17
It worked for me with *env DISPLAY=:0*
Try with the same.

---

### Post by maverickmint on 2009-10-17
Sorry it is not working still !! Hope this will be fixed after the final release of Karmic.

---

### Post by swamisant on 2009-10-18
Same here after reboot the acl is enabled again.

---

### Post by unikuser on 2009-10-19
If you run the command, its one time only. If you want it permanently, Create a new file .xprofile in homedir and add the command there. 

```
gedit   ~/.xprofile 
```

Add **xhost +local:** 

Running xhost +local: is not a problem at all. But, **xhost +** will completely disable ACL. That means anyone in your network(everyone if no firewall) can run X-apps with your display as server.

---

