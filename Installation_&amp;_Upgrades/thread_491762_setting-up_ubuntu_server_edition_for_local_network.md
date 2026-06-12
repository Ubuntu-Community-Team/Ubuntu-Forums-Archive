---
title: "setting-up ubuntu server edition for local network"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by md5hash on 2007-07-04
i just installed ubuntu 7.04 server edition, on a separate box 
i need a simple guide on how to configure this server for local or intranet only.

need it asap

thanks,

---

### Post by md5hash on 2007-07-04
bump! anyone please

---

### Post by floydwilde on 2007-07-04
there are a lot of possible application for a local intranet server.  What specifically are you trying do?  Setup a local webserver?  Use samba?

---

### Post by md5hash on 2007-07-04
im trying to setup a LAMP server.

---

### Post by floydwilde on 2007-07-04
[https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP](https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP)

---

### Post by md5hash on 2007-07-04
actually im done with the setup the problem is when i try to access the webserver from my browser **[http://iportal](http://iportal)**  it says **Host name lookup for 'iportal' failed** but when i use the ip addess [http://130.xx.x.xx](http://130.xx.x.xx) its okay..

omg whats is wrong?

---

### Post by md5hash on 2007-07-04
bump!

---

### Post by hibernatus on 2007-07-04
> **md5hash said:**
> actually im done with the setup the problem is when i try to access the webserver from my browser **[http://iportal](http://iportal)**  it says **Host name lookup for 'iportal' failed** but when i use the ip addess [http://130.xx.x.xx](http://130.xx.x.xx) its okay..

omg whats is wrong?

1 : what is : iportal

is it your hostname or a virtual host that you have set up in Apache?

2 : if you ping iportal what's the result

3 : what's the resulte of the following command : 
 hostname -a

---

### Post by md5hash on 2007-07-04
> **hibernatus said:**
> 1 : what is : iportal

is it your hostname or a virtual host that you have set up in Apache?

2 : if you ping iportal what's the result

3 : what's the resulte of the following command : 
 hostname -a

a1: iportal is my hostname, LAMP is already running and i have excuted few scripts but using its IP address not the host name

a2: i did ping the ip address of iportal, heres the reply
64 bytes from 130.10.1.15: icmp_seq=2 ttl=64 time=0.180 ms

a3: iportal

i really dont know whats wrong

.:im using server editing, no gui

---

### Post by newOldUser on 2007-07-12
I think your problem is in the translation of "iPortal" to an IP address.  This is normally done by DNS (Data Name Server?).  My guess is that you do not have one running, most home setups don't.  You could go through the time and trouble of setting one up, it's beyond me, or you could alter the "hosts" file on every machine that you want to use the iPortal server.  I don't have all the information in front of me but do a serach for the "Hosts" file and then edit it. Basically you add the name of the server and the IP address. Before your machine goes out looking for a DNS server to resolve your name it will check the Hosts file to see if you have something hard coded.  Hosts file exist on both Linux and Windows machines so both can get to your iPortal server.

Note:... for this to work the server, iPortal, must boot up with the same IP address everytime. Usually not a problem.

Good luck

---

### Post by md5hash on 2007-07-12
i just added iportal and its ip address to the dns server, but still its not working. i installed samba, smbfs then it work. i dont know why but its working. do you have an explanation

---

### Post by floydwilde on 2007-07-12
Samba is for sharing filesystems between computers, and doesn't really have anything to do with what your trying to do.   The host file is in /etc/hosts, here is a snippet from mine, on my workstation:

john@satori:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       satori.lan      satori
192.168.2.1 batwap
192.168.2.117 orson

satori is the workstation, and that is the entry that ubuntu put in for it.  batwap is my router, and orson is another computer i use for a development server.  So when I want to ssh or bring up orson in my web browser I can just type orson and it will map to the ip number.  I may have added that satori bit on the localhost line, so I don't have to type satori.lan to bring up the webserver on the localhost. 

If you installed the webserver on the server your using you could also use localhost as the hostname.  Although I think about it now and since you mention samba you're probably connecting from a windows machine. 

In windows the host file is in win32 or system folder or something, just do a ctrl-f search for hosts in explorer.  Then in there make sure you have an entry like one of those above to map an ip to iportal.

otherwise just use the ip address?

---

