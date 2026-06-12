---
title: "cant fix brocken pakages"
date: 2012-09-10
forum: Installation &amp; Upgrades
---

### Post by Chris11 on 2012-09-10
I get a error message (do not enter, one way rafic signe) in the info area, I cant open update manager and I cant fix brocken packages, i think the borcken package is update-manager. I get the folowing output in the terminal:

> christop@christop-1015PEM:~$ sudo dpkg --configure -a
[sudo] password for christop: 
christop@christop-1015PEM:~$ sudo apt-get install -f
Leyendo lista de paquetes... ¡Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/mx.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
E: No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.
christop@christop-1015PEM:~$

what should I doo?

---

### Post by Rex Bouwense on 2012-09-10
Try using 
```
sudo apt-get update
sudo apt-get upgrade
```
in the terminal.  Or alternatively try the Synaptic Package Manager.

---

### Post by Chris11 on 2012-09-10
sudo apt-get update gives me this error message


....
Des:99 [http://cosmos.cites.illinois.edu](http://cosmos.cites.illinois.edu) precise-security/universe Translation-en [26,5 kB]          
Descargados 29,2 MB en 8min. 16seg. (58,7 kB/s)                                                     
Leyendo lista de paquetes... ¡Error!
W: Error de GPG: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: Las siguientes firms fueron inválidas: BADSIG C2518248EEA14886 Launchpad VLC
W: Error de GPG: [http://archive.canonical.com](http://archive.canonical.com) precise Release: Las siguientes firms fueron inválidas: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages
E: No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.
christop@christop-1015PEM:~$

---

### Post by cortman on 2012-09-10
Hi, run these commands in order:

```

sudo apt-get clean
 sudo rm -r /var/lib/apt/lists/*
 sudo touch /var/lib/apt/lists/lock
 sudo mkdir /var/lib/apt/lists/partial
 sudo apt-get clean
 sudo apt-get update

```

---

### Post by Chris11 on 2012-09-11
thank you Cortman, these commands did the job... :guitar:

---

### Post by cortman on 2012-09-11
Great! Go ahead and mark the thread [SOLVED] using the thread tools in the upper right.
Good luck!

---

