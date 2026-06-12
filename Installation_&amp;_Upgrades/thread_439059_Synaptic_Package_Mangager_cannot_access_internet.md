---
title: "Synaptic Package Mangager cannot access internet"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by Claes Göran Engström on 2007-05-10
:confused: I'm new to Ubuntu - (linux) and have a trouble with the otherwise excellent installation. The problem is that the Synaptic Package Manager (mouthful) does not does not recognise my internet connection. A test of available servers could not find any. 

My browser does not have this problem.

---

### Post by taurus on 2007-05-10
What happens when you run these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by vdubber on 2007-05-10
I have a similar problem, with any command that tries to access the repositories, see the post below that no-one has answered. Is it a router or firewall problem, if so what can I do?

[http://ubuntuforums.org/showthread.php?t=438911](http://ubuntuforums.org/showthread.php?t=438911)

Thanks

---

### Post by Claes Göran Engström on 2007-05-10
cgeng@cgeng-ubuntu:~$ sudo aptitude update
Password:
E: Kunde inte erhålla låset /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?
cgeng@cgeng-ubuntu:~$ sudo aptitude upgrade
E: Kunde inte erhålla låset /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Läser paketlistor... Färdig
Bygger beroendeträd         
Reading state information... Färdig
Initializing package states... Färdig
Building tag database... Färdig       
E: Kunde inte erhålla låset /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
cgeng@cgeng-ubuntu:~$

---

### Post by taurus on 2007-05-10
Did you have synaptic running when you ran those two commands?  You cannot run two processors, synaptic and aptitude, at the same time.  You need to close synaptic first.

```
ps -A
```

---

### Post by Claes Göran Engström on 2007-05-10
Sorry about last message :oops: 
Quick translation from Swedish (where applicable)
cgeng@cgeng-ubuntu:~$ sudo aptitude update
Password:
E: Kunde inte erhålla låset (could not receive lock)  /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?
cgeng@cgeng-ubuntu:~$ sudo aptitude upgrade
E: Kunde inte erhålla låset (ditto) /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Läser paketlistor... Färdig (Reading package lists .... Done)
Bygger beroendeträd     (Building dependency tree)   
Reading state information... Färdig (Done)
Initializing package states... Färdig (ditto)
Building tag database... Färdig     (and done)  
E: Kunde inte erhålla låset /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
cgeng@cgeng-ubuntu:~$

---

### Post by taurus on 2007-05-10
Do you have synaptic running?  What's the output of this command from a terminal?

```
ps -A
```

---

### Post by Claes Göran Engström on 2007-05-10
Thanks, quite correct - Synaptic was running. Aptitude found a ftp site in Finland and upgraded. Synaptic still unable to do so, however. Also seems to effect Sound juicer's ability to connect to musicbrainz (also synaptic?)

---

