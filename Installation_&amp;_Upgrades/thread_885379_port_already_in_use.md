---
title: "port already in use"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by cybernet on 2008-08-10
how can i see what program use the port 10000
thank you :)

i'm using Ubuntu Ultimate 1.7 ( ubuntu 7.10 )

---

### Post by cdtech on 2008-08-10
Thats the standard port for the "webmin".

**P.S.**
you can see all ports used:
```
cat /etc/services
```

---

### Post by cariboo on 2008-08-10
If you;ve got namp installed you could try:

```
sudo nmap -sS -sV -O -p- -PI -PT <your ip address>
```

Running the above on my internal server results in something like this:

```
Interesting ports on willy (XXX.XXX.XXX.XXX):
Not shown: 65525 closed ports
PORT      STATE SERVICE     VERSION
21/tcp    open  ftp         ProFTPD 1.3.1
22/tcp    open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1.2 (protocol 2.0)
80/tcp    open  http        Apache httpd 2.2.8 ((Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g mod_musicindex/1.2.1)
139/tcp   open  netbios-ssn Samba smbd 3.X (workgroup: APLUS)
443/tcp   open  http        Apache httpd 2.2.8 ((Ubuntu) PHP/5.2.4-2ubuntu5.3 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g mod_musicindex/1.2.1)
445/tcp   open  netbios-ssn Samba smbd 3.X (workgroup: APLUS)
631/tcp   open  ipp         CUPS 1.2
3306/tcp  open  mysql       MySQL 5.0.51a-3ubuntu5.1
8888/tcp  open  http        GNUMP3d streaming server 3.0
10000/tcp open  http        Webmin httpd
MAC Address: XX:XX:XX:XX:XX:XX (D-Link)
Device type: general purpose
Running: Linux 2.6.X
OS details: Linux 2.6.17 - 2.6.23
Uptime: 0.468 days (since Sat Aug  9 13:57:00 2008)
Network Distance: 1 hop
Service Info: OSs: Unix, Linux
```

I obscured the ip and mac addresses

Jim

---

