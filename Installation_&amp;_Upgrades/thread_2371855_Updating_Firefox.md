---
title: "Updating Firefox"
date: 2017-09-19
forum: Installation &amp; Upgrades
---

### Post by mrityunjay23 on 2017-09-19
I am trying to update my Firefox version. But it is not updating my Firefox version. I have tried following commands.
```

sudo add-apt-repository ppa:ubuntu-mozilla-security/ppa 
sudo apt-get update 
sudo apt-get install firefox

```
I have tried to add ppa respository through software center also.
After executing first command. It gives following error.
```
Cannot add PPA: 'ppa:ubuntu-mozilla-security/ppa'.
Please check that the PPA name or format is correct.
```

---

### Post by vasa1 on 2017-09-19
What does```
apt policy firefox
```show? And what version of Ubuntu are you on?

---

### Post by mrityunjay23 on 2017-09-19
Ubuntu version: 14.04.2 LTS and Firefox version is 39.0. 

Out put of command ```
sudo apt policy firefox
[sudo] password for mrityunjay: 
E: Invalid operation policy
```

Actually I want to add grammerly in firefox. But it is not getting add sucessfuly.

---

### Post by vasa1 on 2017-09-19
[s]Please try```
apt-get policy firefox
```instead **and there's no need for *sudo***.[/s]

As Impavidus points out, that should be ```
apt-cache policy firefox
```Sorry about that!

---

### Post by mrityunjay23 on 2017-09-19
```
sudo apt-get policy firefox
[sudo] password for mrityunjay: 
E: Invalid operation policy
```

---

### Post by vasa1 on 2017-09-19
> **mrityunjay23 said:**
> ```
sudo apt-get policy firefox
[sudo] password for mrityunjay: 
E: Invalid operation policy
```No need for *sudo*!!! Please don't include *sudo* in the command!

---

### Post by Impavidus on 2017-09-19
I'm a bit rusty on 14.04 but I think the command is```
apt-cache policy firefox
```
Ubuntu 14.04 is still supported and should have offered your Firefox 55 even without a PPA.

---

### Post by mrityunjay23 on 2017-09-19
```
mrityunjay@mrityunjay-A7GMX-K:~$ apt-cache policy firefox
firefox:
  Installed: 39.0+build5-0ubuntu0.14.04.1
  Candidate: 39.0+build5-0ubuntu0.14.04.1
  Version table:
 *** 39.0+build5-0ubuntu0.14.04.1 0
        500 http://172.16.68.10/ubuntu/ trusty-updates/main amd64 Packages
        500 http://172.16.68.10/ubuntu/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     28.0+build2-0ubuntu2 0
        500 http://172.16.68.10/ubuntu/ trusty/main amd64 Packages

```
```

mrityunjay@mrityunjay-A7GMX-K:~$ apt-get policy firefox
E: Invalid operation policy

```

I am wanted to run grammerly on firefox. But I am not able to run grammerly on my firefox.

---

### Post by vasa1 on 2017-09-19
> **Impavidus said:**
> I'm a bit rusty on 14.04 but I think the command is```
apt-cache policy firefox
```
Ubuntu 14.04 is still supported and should have offered your Firefox 55 even without a PPA.
You're absolutely right. My bad :(

---

### Post by deadflowr on 2017-09-20
Isn't
```
http://172.16.68.10/ubuntu/
```
A private LAN address?

---

### Post by mrityunjay23 on 2017-09-20
I do not know

---

### Post by mrityunjay23 on 2017-09-20
[SUP]When I follow instruction of following website then also my firefox is not getting update.

```
https://support.mozilla.org/en-US/kb/install-firefox-linux
[/SUP]
```

---

### Post by deadflowr on 2017-09-20
> **mrityunjay23 said:**
> I do not know

Typically 192.168.X.X
172.16.x.x
and
10.0.x.x
are common local area (private) network allocated addresses.

The apt sources.list would never have these as the archive addresses unless you manually set it for that.

The reason for it being set like this is that you are probably connecting to an internal local repository server, using something like apt-cache or apt-mirror.
In which case you need to update the mirror/cache server.
(Or tell the server admin to update the repository)

---

### Post by vasa1 on 2017-09-20
> **mrityunjay23 said:**
> I do not know
You'll have to do better than that!

Where is this computer located? Is it in 
your home
your college
your workplace?

What is the output of ```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by mrityunjay23 on 2017-09-28
My system has Ubuntu 14.04.2 LTS  and Firefox 55.0.3 and I have allowed  popup windows in firefox. I have downloaded firefox from below site and  then I have opened tar file. I open firefox by clicking firefox.exe  file.
      [https://www.mozilla.org/en-US/firefox/new/?scene=2](https://www.mozilla.org/en-US/firefox/new/?scene=2)

To check grammer of my pdf file I use grammerly website. When I try to upload a new document on the website [www.grammelry.com]("http://www.grammelry.com") it does not get open.  So I can not able to upload it. May any body help please? One of my friend, who has Ubuntu 14.04.5 and Firefox (<55 version) on his system. This wesite works.

---

### Post by vasa1 on 2017-09-28
Threads merged. You were asked for clarifications but you have provided none :(

---

