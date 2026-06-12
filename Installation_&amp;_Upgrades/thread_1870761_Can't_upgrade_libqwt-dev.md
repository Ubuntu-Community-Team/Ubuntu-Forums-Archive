---
title: "Can't upgrade libqwt-dev"
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by dernier_recours on 2011-10-27
Hi

There is always an update asked for libqwt-dev in the update manager. It is downloaded at each upgrade, but never installed. Here is what it looks like:


anonymous@anonymous-TECRA-R700:~$ sudo apt-get upgrade
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets suivants seront mis à jour*:
  libqwt-dev
1 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 0 o/103 ko dans les archives.
Après cette opération, 0 o d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n]*? O
(Lecture de la base de données... 218102 fichiers et répertoires déjà installés.)
Préparation du remplacement de libqwt-dev 6.0.0-1ubuntu1 (en utilisant .../libqwt-dev_6.0.0-1ubuntu1_amd64.deb) ...
Dépaquetage de la mise à jour de libqwt-dev ...
Paramétrage de libqwt-dev (6.0.0-1ubuntu1) ...
anonymous@anonymous-TECRA-R700:~$ sudo apt-get upgrade
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets suivants seront mis à jour*:
  libqwt-dev
1 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 0 o/103 ko dans les archives.
Après cette opération, 0 o d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n]*? O
(Lecture de la base de données... 218102 fichiers et répertoires déjà installés.)
Préparation du remplacement de libqwt-dev 6.0.0-1ubuntu1 (en utilisant .../libqwt-dev_6.0.0-1ubuntu1_amd64.deb) ...
Dépaquetage de la mise à jour de libqwt-dev ...
Paramétrage de libqwt-dev (6.0.0-1ubuntu1) ...
anonymous@anonymous-TECRA-R700:~$

---

### Post by raja.genupula on 2011-10-27
Hi man could you please provide me the information in english because i am unable to understand it.

Thanks.

---

### Post by dernier_recours on 2011-10-27
Sorry. There it goes. It presents twice the same operation to show that the upgrade that looked successful is indeed not done.

anonymous@anonymous-TECRA-R700:~$ sudo apt-get upgrade
[sudo] password for anonymous: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libqwt-dev
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/103 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 227162 files and directories currently installed.)
Preparing to replace libqwt-dev 6.0.0-1ubuntu1 (using .../libqwt-dev_6.0.0-1ubuntu1_amd64.deb) ...
Unpacking replacement libqwt-dev ...
Setting up libqwt-dev (6.0.0-1ubuntu1) ...
anonymous@anonymous-TECRA-R700:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libqwt-dev
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/103 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 227162 files and directories currently installed.)
Preparing to replace libqwt-dev 6.0.0-1ubuntu1 (using .../libqwt-dev_6.0.0-1ubuntu1_amd64.deb) ...
Unpacking replacement libqwt-dev ...
Setting up libqwt-dev (6.0.0-1ubuntu1) ...
anonymous@anonymous-TECRA-R700:~$

---

### Post by raja.genupula on 2011-10-28
have you checked the same thing again by restarting your PC.?

---

### Post by dernier_recours on 2011-10-28
Yes. This problem is active since last week or so. I'm on 11.10.

---

### Post by raja.genupula on 2011-10-28
```
zcat -f /var/log/dpkg.log* | grep "\ install\ " | sort

```

give me the output of that and then try to look for same package in synaptic and try to install from there

---

### Post by dernier_recours on 2011-10-28
This is what I got. 

2011-10-28 15:12:26 install libqwt-dev <none> 6.0.0-1ubuntu1

---

### Post by bradynathan on 2011-11-04
I was receiving the same error after upgrading to oneiric 64bit.  As this is a development package and I am not developing an application that would need those libraries, I chose to remove it.  Have not noticed any problems as a result.

---

### Post by colinmb on 2011-12-18
This is still a problem. I have libqwt6 and libqwt-dev installed:
```
cmb@home:~$ aptitude seach qwt
i   libqwt-dev                                                 - Qt widgets library for technical applications (development)          
p   libqwt-doc                                                 - Qt widgets library for technical applications (documentation)        
p   libqwt4c2                                                  - Qt widgets library for technical applications (runtime)              
p   libqwt5-doc                                                - Qt widgets library for technical applications (documentation)        
p   libqwt5-qt4                                                - Qt4 widgets library for technical applications (runtime)             
p   libqwt5-qt4-dev                                            - Qt4 widgets library for technical applications (development)         
i A libqwt6                                                    - Qt widgets library for technical applications (runtime)              
p   libqwtplot3d-doc                                           - 3D plotting library based on Qt/OpenGL (documentation)               
p   libqwtplot3d-qt4-0                                         - 3D plotting library based on Qt4/OpenGL (runtime)                    
p   libqwtplot3d-qt4-dev                                       - 3D plotting library based on Qt4/OpenGL (development)                
p   python-guiqwt                                              - efficient 2D data-plotting library                                   
p   python-qwt3d-doc                                           - Documentation for the Python-qwt3d library                           
p   python-qwt3d-qt4                                           - Python bindings of the QwtPlot3D library                             
p   python-qwt5-doc                                            - Python Qwt5 technical widget library, documentation and examples     
p   python-qwt5-qt4                                            - Python version of the Qwt5 technical widget library                  
v   python2.6-guiqwt                                           -                                                                      
v   python2.7-guiqwt                                           -
```

libqwt-dev appears to be at the latest version:
```
cmb@home:~$ aptitude show libqwt-dev
Package: libqwt-dev                      
New: yes
State: installed
Automatically installed: no
Version: 6.0.0-1ubuntu1
Priority: optional
Section: libdevel
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 668 k
Depends: libc6 (>= 2.2.5), libgcc1 (>= 1:4.1.1), libqt4-designer (>= 4:4.5.3), libqtcore4 (>= 4:4.7.0~beta1), libqtgui4 (>= 4:4.5.3),
         libqwt6 (= 6.0.0-1ubuntu1), libstdc++6 (>= 4.1.1), libqt4-dev
Breaks: libqwt5-qt4-dev (< 6.0.0-1)
Replaces: libqwt5-qt4-dev (< 6.0.0)
Description: Qt widgets library for technical applications (development)
 The Qwt library contains Qt GUI Components and utility classes which are primarily useful for programs with a technical background.
 Most of these widgets are used to control or display values, arrays, or ranges of type double. 
 
 This package contains the Qwt development files for Qt.
Homepage: http://qwt.sourceforge.net
```
...but every 'upgrade' issued to aptitude wants to upgrade libqwt-dev again:
```
cmb@home:~$ aptitude upgrade -s
The following packages will be upgraded: 
  libqwt-dev 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/103 kB of archives. After unpacking 0 B will be used.
Do you want to continue? [Y/n/?]
```

Is there a version misrepresentation in aptitude?

--Colin

---

### Post by LiXarDoh on 2012-01-05
I'm experiencing the same problem and it seems to be having an impact on my not being able to update to the most current version of XASTIR in the repository.
I have a 32 bit 11.10 on a Dell.

---

### Post by jiapei100 on 2012-03-12
I've got exactly the same problem as discussed above.


Cheers
Pei

---

### Post by popitto on 2012-05-09
hello,
anyone found a solution for this problem?
i'm having the same issue described in this thread :confused:
i'm on ubuntu 12.04 32bits !

cheers,

---

### Post by axeoth on 2012-05-27
I have the same issue on Ubuntu Precise.

---

### Post by axeoth on 2012-05-27
This has been reported here:

[https://bugs.launchpad.net/ubuntu/+source/qwt/+bug/921430](https://bugs.launchpad.net/ubuntu/+source/qwt/+bug/921430)

---

### Post by niccolo.canestrari on 2012-06-05
the error is in the package, the control file line 9 is:

**Replaces: libqwt5-qt4-dev (<< 6.0.0-)**

it should be

**Replaces: libqwt5-qt4-dev (<< 6.0.0-1)**

A "**1**" is missing, it is clearly a typo.

---

### Post by Introspection on 2012-06-07
How can we correct this typo?

---

