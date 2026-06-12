---
title: "ssh problem after updating."
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by lemming882 on 2008-01-14
After I did my updates to my Ubuntu 7.10 I am no longer able to SSH into any of my servers.  The ssh command on it's own is giving me this error:

```
HOST-desktop:~$ ssh
Segmentation fault (core dumped)
```

I have tried to do a reinstall of the package and here is the output I got from trying that.

```
HOST-desktop:~$ sudo apt-get install ssh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ssh
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
4 not fully installed or removed.
Need to get 0B/1088B of archives.
After unpacking 32.8kB of additional disk space will be used.
Selecting previously deselected package ssh.
(Reading database ... 124700 files and directories currently installed.)
Unpacking ssh (from .../ssh_1%3a4.3p2-8ubuntu1.1_all.deb) ...
Setting up openssh-client (4.3p2-8ubuntu1.1) ...
chgrp: cannot access `/usr/bin/ssh-agent': No such file or directory
dpkg: error processing openssh-client (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openssh-server:
 openssh-server depends on openssh-client (= 1:4.3p2-8ubuntu1.1); however:
  Package openssh-client is not configured yet.
dpkg: error processing openssh-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ssh:
 ssh depends on openssh-client; however:
  Package openssh-client is not configured yet.
 ssh depends on openssh-server; however:
  Package openssh-server is not configured yet.
dpkg: error processing ssh (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ssh-krb5:
 ssh-krb5 depends on openssh-client; however:
  Package openssh-client is not configured yet.
 ssh-krb5 depends on openssh-server; however:
  Package openssh-server is not configured yet.
dpkg: error processing ssh-krb5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ssh-askpass-gnome:
 ssh-askpass-gnome depends on openssh-client | ssh (>= 1:1.2pre7-4) | ssh-krb5; however:
  Package openssh-client is not configured yet.
  Package ssh is not configured yet.
  Package ssh-krb5 is not configured yet.
dpkg: error processing ssh-askpass-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openssh-client
 openssh-server
 ssh
 ssh-krb5
 ssh-askpass-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Anyways it could be something very easy that I'm over looking and would appreciate some input.

Shane

---

### Post by Partyboi2 on 2008-01-15
what happens if you try to install openssh-client first
```
sudo apt-get install openssh-client
```

---

### Post by lemming882 on 2008-01-15
In doing that I get about the same error:

```
HOST-desktop:~$ sudo apt-get install openssh-client
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-client is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up openssh-client (4.3p2-8ubuntu1.1) ...
chgrp: cannot access `/usr/bin/ssh-agent': No such file or directory
dpkg: error processing openssh-client (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openssh-server:
 openssh-server depends on openssh-client (= 1:4.3p2-8ubuntu1.1); however:
  Package openssh-client is not configured yet.
dpkg: error processing openssh-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ssh:
 ssh depends on openssh-client; however:
  Package openssh-client is not configured yet.
 ssh depends on openssh-server; however:
  Package openssh-server is not configured yet.
dpkg: error processing ssh (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ssh-askpass-gnome:
 ssh-askpass-gnome depends on openssh-client | ssh (>= 1:1.2pre7-4) | ssh-krb5; however:
  Package openssh-client is not configured yet.
  Package ssh is not configured yet.
  Package ssh-krb5 is not installed.
dpkg: error processing ssh-askpass-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openssh-client
 openssh-server
 ssh
 ssh-askpass-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Partyboi2 on 2008-01-15
try
```
sudo dpkg --configure -a
```

---

### Post by lemming882 on 2008-01-15
Nothing outputted on this command.

---

### Post by lemming882 on 2008-01-15
Hmmm any other suggestions before I blow the thing away and start fresh.  

I would hate to do this since I finally have everything where I want it and Beryl is oh so pretty right now. ;)

---

### Post by drewcoon on 2008-05-18
Bump I'm having this problem as well :(

```

drewc@linxp:~$ sudo dpkg --configure -a
Setting up openssh-server (1:4.7p1-8ubuntu1.2) ...
/etc/ssh/sshd_config: line 5: Bad configuration option: Listen
/etc/ssh/sshd_config: terminating, 1 bad configuration options
invoke-rc.d: initscript ssh, action "restart" failed.
dpkg: error processing openssh-server (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ssh:
 ssh depends on openssh-server; however:
  Package openssh-server is not configured yet.
dpkg: error processing ssh (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openssh-server
 ssh
drewc@linxp:~$ 

```

Exact same problem (dependency issues?), this happened after an update and now it repeats itself everytime I update something via synaptic.

---

