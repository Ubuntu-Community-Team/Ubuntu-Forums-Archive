---
title: "Problem with installation nginx"
date: 2019-05-24
forum: Installation &amp; Upgrades
---

### Post by zak100 on 2019-05-24
Hi,
I am using the following tutorial:
[https://www.vultr.com/docs/configure-php-7-2-on-ubuntu-18-04](https://www.vultr.com/docs/configure-php-7-2-on-ubuntu-18-04)
I am trying to install PhP on my ubuntu 18.04. Note I have skipped the create user step: 

**Create your sudo user**



The tutorial says to install nginx using the following command:
```


sudo systemctl start nginx.service

```

I am getting following errors:

> 
                        

zulfi@lc2530hz:~$ sudo systemctl start nginx.servce
Failed to start nginx.servce.service: Unit nginx.servce.service not found.
zulfi@lc2530hz:~$ sudo systemctl start nginx.service
Job for nginx.service failed because the control process exited with error code.
See "systemctl status nginx.service" and "journalctl -xe" for details.
zulfi@lc2530hz:~$ systemctl status nginx.service
&#9679; nginx.service - A high performance web server and a reverse proxy server
   Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: en
   Active: failed (Result: exit-code) since Thu 2019-05-23 23:24:26 CDT; 2min 15
     Docs: man:nginx(8)
  Process: 27611 ExecStart=/usr/sbin/nginx -g daemon on; master_process on; (cod
  Process: 27610 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; master_process

May 23 23:24:24 lc2530hz nginx[27611]: nginx: [emerg] bind() to 0.0.0.0:80 faile
May 23 23:24:24 lc2530hz nginx[27611]: nginx: [emerg] bind() to [::]:80 failed (
May 23 23:24:25 lc2530hz nginx[27611]: nginx: [emerg] bind() to 0.0.0.0:80 faile
May 23 23:24:25 lc2530hz nginx[27611]: nginx: [emerg] bind() to [::]:80 failed (
May 23 23:24:25 lc2530hz nginx[27611]: nginx: [emerg] bind() to 0.0.0.0:80 faile
May 23 23:24:25 lc2530hz nginx[27611]: nginx: [emerg] bind() to [::]:80 failed (
May 23 23:24:26 lc2530hz nginx[27611]: nginx: [emerg] still could not bind()
May 23 23:24:26 lc2530hz systemd[1]: nginx.service: Control process exited, code
May 23 23:24:26 lc2530hz systemd[1]: nginx.service: Failed with result 'exit-cod
May 23 23:24:26 lc2530hz systemd[1]: Failed to start A high performance web serv
lines 1-17/17 (END)


 
 
  





Somebody please guide me.

Zulfi.

---

### Post by TheFu on 2019-05-24
Just a guess.

> You can use Apache **_or_** Nginx as your webserver.

Only 1 web server can listen on port 80/tcp at a time. If apache is already installed, then it will have exclusive access to that port and you should probably use it instead.

You can use **netstat** to see if a port is taken or **lsof** to see which program has any specific port.

---

### Post by zak100 on 2019-05-24
$ sudo netstat -plnt

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1230/nginx: master  
tcp        0      0 127.0.0.1:5939          0.0.0.0:*               LISTEN      1928/teamviewerd    
tcp        0      0 192.168.122.1:53        0.0.0.0:*               LISTEN      1690/dnsmasq        
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN      823/systemd-resolve 
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1205/sshd           
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      10503/cupsd         
tcp6       0      0 :::80                   :::*                    LISTEN      1230/nginx: master  
tcp6       0      0 :::22                   :::*                    LISTEN      1205/sshd           
tcp6       0      0 ::1:631                 :::*                    LISTEN      10503/cupsd         

It shows me nginx installed twice. Is it a problem? Does it mean that I don't have apache installed on my system?

Somebody please guide me.

Zulfi.

---

### Post by TheFu on 2019-05-25
```
Proto Recv-Q Send-Q Local Address Foreign Address State PID/Program name
tcp 0 0 0.0.0.0:80 0.0.0.0:* LISTEN 1230/nginx: master 
tcp6 0 0 :::80 :::* LISTEN 1230/nginx: master 
```

That's IPv4 and IPv6. Looks fine.

I'd use **sudo nginx -t **to have it go through all the configs in order and show issues. Fix **any** issues, in order. 

Whenever posting shell output or logs, please, please, please, use [code tags]("https://blog.jdpfu.com/code_tags") so things line up, spacing is retained and everything looks like it does in the terminal.

If netstat is showing nginx running, then it is working within the confines of the nginx config. I suppose you changed something or were trying to run nginx when another instance was already running?

---

