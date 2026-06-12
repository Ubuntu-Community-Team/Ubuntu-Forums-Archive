---
title: "FTP Server"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by psmul on 2007-05-22
Hi,

I've read a few guides on how to start an FTP server. The thing is ... I don't get them !!!

Where / when do they tell me wich map to share, where / when do they tell me to create users.

Can someone please explain to me (in an easy way) how to make a working FTP server?

Thanks in advance

---

### Post by psmul on 2007-05-22
bump

---

### Post by NumberOne on 2007-05-22
I am a relatively new user and I set proftpd and it was pretty easy.  I used the GUI Gproftpd.  No command line setup needed.  Just install from the repositories and go from there.

---

### Post by bobbocanfly on 2007-05-23
TO get g/proftpd working properly

```
sudo apt-get install proftpd gproftpd
<When its all finished run>
sudo gproftpd

```

---

### Post by NumberOne on 2007-05-23
Once you have it installed there will be a menu choice to launch gProftpd, ir your using the ubuntu desktop.

---

### Post by worbyjj on 2007-06-01
> **bobbocanfly said:**
> TO get g/proftpd working properly

```
sudo apt-get install proftpd gproftpd
<When its all finished run>
sudo gproftpd

```


Q1) When I enter the above, I get the following error message:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package proftpd

I get that it couldn't find the package, but where is it looking for the package?  Am I supposed to have added some extra repositories at some point?  Also, when I use "Synaptic Package Manager", proftpd does not exist.

It feels like I'm missing something obvious, but I'm not sure where to begin.

Q2)  Also ftp related... Once you've installed your ftp server and your computer is behind a router, do you have to port forward the port that the ftp server is using?  If so, what port does it use?

Thanks for any help.

---

