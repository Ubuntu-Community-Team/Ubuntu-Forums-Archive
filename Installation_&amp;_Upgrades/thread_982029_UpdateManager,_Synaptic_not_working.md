---
title: "UpdateManager, Synaptic not working"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by IvanSum on 2008-11-14
I have been using Ubuntu 8.04 for several months and love it.  A few days ago, UpdateManager stopped working.  When I got notice of updates I clicked on the icon and Update started.  When i clicked on Install, it hung.  I later discovered that it does the same for Check.   I then noticed that Synatic doesn't run.  When I launch it, the task bar shows "Starting admin..." for a few seconds and then goes away.  Same thing for Software Sources.

I finally tried apt-get upgrade and it successfully installed the updates.  I noticed, while doing this, that every time I run sudo, I get the following error:sudo: unable to resolve host ivan-dsktp-64amd-x2 . (which is the name of my system).

Also, after the updates were installed, a reboot was required ans I got the 
attached error.

Any help?
Ivan

---

### Post by quimico69 on 2008-11-14
I see this is your first post, WELCOME.

If you are getting an "unable to resolve" error, it probably means there is a problem with your host resolution.  Have there been any recent changes in your network configuration? It is a home computer connected through an ISP or is it a computer at an enterprise net?

I've gotten error notifications like the one you attached when I had problems in the network configuration, even though the applet in question does not require net access.

---

### Post by IvanSum on 2008-11-14
This is a home networked computer, using an isp.  I have a win-xp and  another Ubuntu computer.  I have been working on getting my windows and Ubuntu files sharing working and hve gotten it to work this week.  Where do I look to see if my net config is the problem?

Thanks,
Ivan

---

### Post by Kevbert on 2008-11-14
Welcome to Ubuntu.
Unfortunately the error in your attachment is a sound bug which may be fixed (if you're lucky) with the latest updates. It may be that you can't download updates due to a damaged package or incomplete install of a package.  Please go to Applications-Accessories-Terminal and enter the following commands:
```
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update
```
You may be able to update via terminal. Normally the last command is used to get an updated package list and from there you can upgrade all packages with
```
sudo apt-get upgrade

```
If terminal works then hopefully your Update Manager will work again.
If you get any problems please don't hesitate to ask.

---

### Post by quimico69 on 2008-11-14
Well, if you are posting this from your home computer, then your networking is fine, and following Kevbert's advise should help you.  If you cannot access the net from your home machine, then apt-get will not work either, and you will have to ask your ISP about the proper settings to connect.  Usually it is dynamic address assignment (DHCP) meaning that the computer has to request an IP address every time it connects to the net.  You can specify DHCP using the Network Manager, clicking on the icon showing one monitor hiding another one in your task bar, close to the date applet.

---

### Post by IvanSum on 2008-11-14
Thanks.  I tried it and got no effect.  Attached is the terminal session log.
Ivan

---

### Post by Kevbert on 2008-11-14
Post the result from terminal of
```
cat /etc/hosts
```

---

### Post by IvanSum on 2008-11-14
```
ivan@ivan-dsktp-64amd-x2:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 ivan-dsktp-64amd-x2.mshome

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
ivan@ivan-dsktp-64amd-x2:~$ 
```

---

### Post by quimico69 on 2008-11-14
Ok, lets see the contents of a couple of files.  Please attach the files /etc/hosts and /etc/network/interfaces

---

### Post by IvanSum on 2008-11-14
```
ivan@ivan-dsktp-64amd-x2:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0
ivan@ivan-dsktp-64amd-x2:~$
```

---

### Post by Kevbert on 2008-11-14
Open the hosts file for editing with:-
```
gksudo gedit /etc/hosts

```
and change the line that says
```
127.0.1.1 ivan-dsktp-64amd-x2.mshome
```
to
```
127.0.1.1 ivan-dsktp-64amd-x2
```
save the file and that should fix the problem.

---

### Post by IvanSum on 2008-11-14
That got it!   Thanks.  

While I have you, is there a good place to find out how to get ssh and ftp working on my home network (lan)?  I've been to [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto) and right off the bat "ssh localhost" give me  "https://help.ubuntu.com/community/SSHHowto".
Ivan

---

### Post by IvanSum on 2008-11-14
I noticed the "Thanks" count by your profile.  I wanted to add to it, but don't see how to do it.  How do I.
Ivan

---

### Post by quimico69 on 2008-11-14
> **IvanSum said:**
> I noticed the "Thanks" count by your profile.  I wanted to add to it, but don't see how to do it.  How do I.
Ivan

At the lower right corner you see an icon that looks like a gold medal with a green plus sign.  Click on it.

Glad to see that Kevbert got you all the way to the solution.

---

### Post by Kevbert on 2008-11-15
> **IvanSum said:**
> That got it!   Thanks.  

While I have you, is there a good place to find out how to get ssh and ftp working on my home network (lan)?  I've been to [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto) and right off the bat "ssh localhost" give me  "https://help.ubuntu.com/community/SSHHowto".
Ivan

Sorry I can't really help you there. I'm using up to three PCs to a router which aren't sharing files. Normally the community pages are the best. The other place you could try is [http://www.ubuntugeek.com/](http://www.ubuntugeek.com/) and put your search terms in there.

---

