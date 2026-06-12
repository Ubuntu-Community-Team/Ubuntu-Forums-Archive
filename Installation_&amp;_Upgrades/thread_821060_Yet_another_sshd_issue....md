---
title: "Yet another sshd issue..."
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by amishphysicist on 2008-06-06
Hi All,

I just installed Ubuntu 8.04 Hardy Heron and am unable to ssh to my machine from other on my network.

I did the usual apt-get/aptitude/install commands that people recommend:

```
sudo aptitude install openssh-server
sudo apt-get install openssh-server
sudo apt-get install ssh
sudo /etc/init.d/ssh restart

```

I still can't ssh on over from a different box in the same network.  I haven't done any other fancy firewall config or anything like that. I can ssh out, but not back.

What else do I have to do to make it so I can ssh into my machine?

thanks,

-nate

---

### Post by Pumalite on 2008-06-06
sudo aptitude install openssh-client

---

### Post by amishphysicist on 2008-06-09
Hmm. it doesn't look like that command updated anything:


```
root@nlieby-lin:/lsurf# sudo aptitude install openssh-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done 
```

thanks,

-nate

---

### Post by Pumalite on 2008-06-09
Maybe this might help:
[http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-openssh-server-config.html](http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-openssh-server-config.html)

---

### Post by Vivaldi Gloria on 2008-06-09
You have two computers, say A and B. I assume that A runs sshd and from B you try to ssh A.

Questions:

1) Are these in a LAN? Because the default option of sshd allows only LAN connections.

2) Is sshd really working on A? How about first giving the command

```
/usr/sbin/sshd
```

in A and then trying again.

3) What happens when you do

```
ssh localhost
```

in A?

---

### Post by amishphysicist on 2008-06-10
Both of these computers are on a LAN connection.  All of this worked until I killed off my old ubuntu.

Here are the outputs from the commands you gave:
```
nlieby@nlieby-lin:/lsurf/var$ /usr/sbin/sshd 
Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
```

```
 nlieby@nlieby-lin:/lsurf/var$ ssh localhost
The authenticity of host 'localhost (127.0.0.1)' can't be established.
RSA key fingerprint is 3b:9b:c7:f4:ee:18:67:3f:4c:ad:86:48:5f:7a:14:81.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
```

The weird thing is that the localhost login doesn't accept my usual password for my username, so that makes me wonder.

thanks,

-nate

---

### Post by Vivaldi Gloria on 2008-06-10
> **amishphysicist said:**
> The weird thing is that the localhost login doesn't accept my usual password for my username, so that makes me wonder.


Hmmm. That is weird. So it turns out that you cannot even ssh from the same computer. I suggest that you make a new thread to Security Discussions subforum

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

and post a copy of your /etc/ssh/sshd_config there and write that when you ssh localhost your pswd is not accepted. There are more experienced guys over there. Actually, may be it is better to ask an admin to move this thread over there.

---

### Post by amishphysicist on 2008-06-10
New thread is here: [http://ubuntuforums.org/showthread.php?t=825112]("http://ubuntuforums.org/showthread.php?t=825112")

thanks,

-nate

---

