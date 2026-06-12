---
title: "dpkg broken after a .deb install (xplico)"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by parislanuit on 2011-09-29
Following the installation of Xplico 6.3 (deb package) that failed to install, I can't run synaptic, no updates etc. 

When  i try to use the updates manager a window says :  Impossible to install  some updates, execute a partial update to install as many updates as  possible: yes/no=>Yes
 Then a new window says : 

Package  Xplico is in an incohernet state & needs to be reinstalled but no  archive containing package has been found. Please reinstall this package  manually or delete from the system.

Reinstallation doesn't work. 

What should I do ? 

Thnks

---

### Post by Pumalite on 2011-09-29
Search "status" and change the package from no to yes.

---

### Post by parislanuit on 2011-09-30
I don't understand, what kind of status do you mean? 
thks for helping

---

### Post by dino99 on 2011-09-30
[http://www.debianhelp.co.uk/debianproblem.htm](http://www.debianhelp.co.uk/debianproblem.htm)

---

### Post by parislanuit on 2011-09-30
Here's what I get from [FONT=Verdana][SIZE=1][SIZE=2] /var/lib/dpkg/status :[/SIZE][/SIZE][/FONT]
///////////////////////////////////////
Package: xplico
Status: deinstall reinstreq half-installed
Priority: optional
Section: net
Installed-Size: 40992
Maintainer: Gianluca Costa <g.costa@xplico.org>
Architecture: amd64
Version: 0.6.3
Config-Version: 0.6.3
Depends: libc6 (>= 2.11), libice6 (>= 1:1.0.0), libmysqlclient16 (>= 5.1.21-1), libpcap0.8 (>= 0.9.8), libsm6, libsqlite3-0 (>= 3.7.3), libx11-6, libxext6, libxt6, zlib1g (>= 1:1.1.4), tshark, python3-all, python3-httplib2, apache2, php5-common, libapache2-mod-php5, php5-sqlite, php5-cli, recode, sox, lame, binfmt-support
///////////////////////////////////////////

Should I change a line manually?

---

### Post by Elfy on 2011-09-30
Try this from a terminal

```
sudo dpkg --remove --force-remove-reinstreq xplico 
```

---

### Post by parislanuit on 2011-09-30
hal@cisco:~$ sudo dpkg --remove --force-remove-reinstreq xplico
[sudo] password for hal: 
dpkg : avertissement : problème contourné par utilisation de --force :
 Le paquet est dans un état incohérent - vous devriez
 le réinstaller avant d'essayer de le supprimer.(Package in incoherent state, u should reinstall it first b4 trying to delete it)
(Lecture de la base de données... 187397 fichiers et répertoires déjà installés.)
Suppression de xplico ...
invoke-rc.d: unknown initscript, /etc/init.d/xplico not found.
dpkg : erreur de traitement de xplico (--remove) :
 le sous-processus script post-removal installé a retourné une erreur de sortie d'état 100
Des erreurs ont été rencontrées pendant l'exécution :(unerprocess script post-removal installed returned a state error 100. errors have been found during process)
 xplico


Doesn't work....

---

### Post by dino99 on 2011-09-30
on which ubuntu are you working ? 32 bits or 64 bits installation ?

---

### Post by parislanuit on 2011-09-30
64bits

---

### Post by dino99 on 2011-09-30
so you are trying to install that one ?
[http://sourceforge.net/projects/xplico/files/Xplico%20versions/version%200.6.3/xplico_0.6.3_amd64.deb/download](http://sourceforge.net/projects/xplico/files/Xplico%20versions/version%200.6.3/xplico_0.6.3_amd64.deb/download)

---

### Post by parislanuit on 2011-09-30
Yes that's the one I tried to install, i took it from sourceforge too...

(But i installed the 32bits first, it didn't work (same problem) and then i found the amd64 vesion and tried to install/reinstall/uninstall it several times without success)

Any idea?

---

### Post by dino99 on 2011-09-30
test the windoz version inside virtualbox

---

### Post by parislanuit on 2011-09-30
Thanks but what i am looking for is to get ubuntu fixed , that is my priority...

---

### Post by jerrrys on 2011-09-30
You could gksudo nautilus; do a search and manually remove xplico

---

### Post by Pumalite on 2011-09-30
take the line "
Status: deinstall reinstreq half-installed
an change it to
Status: no.....not installed
Save
Try dpkg
Its a half assed solution, but I've had success in the past.

---

### Post by matt_symes on 2011-09-30
Hi

You could attampt a manual removal by listing the installed files, removing them and editing the dpkg files.

It is something i have used in the past but not for the exact same issue you have, so i would see what others suggest before i outline the details as i am not sure exactly how it would affect your system.

Kind regards

---

### Post by parislanuit on 2011-09-30
Thanks for the help, 

After I changed the line Status i got :
 sudo apt-get upgrade
Lecture des listes de paquets... Erreur !
E: Malformed 1st word in the Status line
E: Erreur apparue lors du traitement de xplico (UsePackage3)
E: Problem with MergeList /var/lib/dpkg/status
E: Les listes de paquets ou le fichier « status » ne peuvent être analysés ou lus.


Damn that it crazzy, I wonder what xplico did to this computer!!
Anything else to get dpkg working??

---

