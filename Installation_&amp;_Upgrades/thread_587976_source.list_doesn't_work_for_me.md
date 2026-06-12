---
title: "source.list doesn't work for me"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by figo2476 on 2007-10-23
sudo apt-get update

output
---------------------
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_AU
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_AU
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_AU
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/main Translation-en_AU
........
.......

No clue so far

---

### Post by pjhsv on 2007-10-23
What is the output of the "route" command?

Is everything else on the internet working correctly?

---

### Post by figo2476 on 2007-10-23
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     1000   0        0 eth0
10.0.0.0        *               255.0.0.0       U     0      0        0 eth0
default         mygateway1.ar7  0.0.0.0         UG    0      0        0 eth0

Can connect to net

---

### Post by figo2476 on 2007-10-23
It gave some warnings during the installation.
Like "cannot connect to security.ubuntu.com"

---

### Post by figo2476 on 2007-10-23
Anyone...?

---

### Post by zvacet on 2007-10-24
Try with main server in **system>administration>software sources** or some other local server.

---

### Post by isagani on 2007-10-24
are you behind a firewall maybe? in an office they usually have firewalls.

---

### Post by mauricevh on 2007-10-24
I got exactly the same problem. Really annoying!
Changing software sources doesn't help because it has to reload and therefore it has to download the packages and this doesn't work.
Someone an idea?

---

### Post by figo2476 on 2007-10-24
* Switch back to 7.04... source.list works for me. I don't think it is firewall issue.
* security.ubuntu.com is up, but kubuntu cannot connect it during the installation stage.

---

### Post by ThrobbingBrain66 on 2007-10-24
> **mauricevh said:**
> I got exactly the same problem. Really annoying!
Changing software sources doesn't help because it has to reload and therefore it has to download the packages and this doesn't work.
Someone an idea?

It should work though.  After you change the mirror that you're downloading from, the lists get downloaded from the new mirror.  If the mirror you selected is in working order, everything should be fine.

@figo2476:  This isn't a problem that should send anyone back to Feisty....it's easy enough to fix.

---

### Post by figo2476 on 2007-10-24
* The switch aims to test, not encouraging downgrade.
* Could someone provide me a source.list, so I can try other mirrors.
   e.g. US mirrors....

---

### Post by figo2476 on 2007-10-24
Sorry to mention that. I am using kubuntu 7.10......

---

### Post by figo2476 on 2007-10-24
oh.... I found the list..... Now it is time to test it

---

### Post by figo2476 on 2007-10-25
hm....It doesn't work.......even change the source.list.....

---

### Post by figo2476 on 2007-11-02
> **ThrobbingBrain66 said:**
> It should work though.  After you change the mirror that you're downloading from, the lists get downloaded from the new mirror.  If the mirror you selected is in working order, everything should be fine.

@figo2476:  This isn't a problem that should send anyone back to Feisty....it's easy enough to fix.

It may be easy to fix, but I don't know how to fix.... after > 3 weeks....

---

### Post by ggauche on 2007-11-02
I have been having the same problem with Gutsy.  I've tried other sources.list files - no relief.
Any ideas?

---

