---
title: "Standard update broke my package manager, nothing seems to work!"
date: 2011-11-17
forum: Installation &amp; Upgrades
---

### Post by equusaustralus on 2011-11-17
Hi, 

I ran a standard update on oneiric this morning, and something seems to have gone wrong with the package manager. 

Tried running sudo dpkg --configure -a to fix it, but this is the output I got: 
> $ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libglib2.0-bin:
 libglib2.0-bin depends on libglib2.0-0 (= 2.31.0+git20111115.3a7960f7-0ubuntu1~11.10~ricotz0); however:
  Version of libglib2.0-0 on system is 2.30.0-0ubuntu4.
dpkg: error processing libglib2.0-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing libglib2.0-0 (--configure):
 libglib2.0-0:amd64 2.30.0-0ubuntu4 cannot be configured because libglib2.0-0:i386 is in a different version (2.31.0+git20111115.3a7960f7-0ubuntu1~11.10~ricotz0)
dpkg: error processing libglib2.0-0:i386 (--configure):
 libglib2.0-0:i386 2.31.0+git20111115.3a7960f7-0ubuntu1~11.10~ricotz0 cannot be configured because libglib2.0-0:amd64 is in a different version (2.30.0-0ubuntu4)
Errors were encountered while processing:
 libglib2.0-bin
 libglib2.0-0
 libglib2.0-0:i386


and sudo apt-get -f install returned this: 

> $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libglib2.0-0
The following packages will be upgraded:
  libglib2.0-0
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0 B/1,890 kB of archives.
After this operation, 73.7 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 156321 files and directories currently installed.)
Preparing to replace libglib2.0-0 2.30.0-0ubuntu4 (using .../libglib2.0-0_2.31.0+git20111115.3a7960f7-0ubuntu1~11.10~ricotz0_amd64.deb) ...
Unpacking replacement libglib2.0-0 ...
dpkg: error processing /var/cache/apt/archives/libglib2.0-0_2.31.0+git20111115.3a7960f7-0ubuntu1~11.10~ricotz0_amd64.deb (--unpack):
 './usr/share/doc/libglib2.0-0/NEWS.gz' is different from the same file on the system
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libglib2.0-0_2.31.0+git20111115.3a7960f7-0ubuntu1~11.10~ricotz0_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


The Software Center can't fix it either, keep getting this error: 

> libglib2.0-0 2.31.0+git20111111.faebf0f6-0ubuntu1~11.10~ricotz0 (using .../libglib2.0-0_2.31.0+git20111115.3a7960f7-0ubuntu1~11.10~ricotz0_amd64.deb) ...

Unpacking replacement libglib2.0-0 ...

dpkg: error processing /var/cache/apt/archives/libglib2.0-0_2.31.0+git20111115.3a7960f7-0ubuntu1~11.10~ricotz0_amd64.deb (--unpack):

 './usr/share/doc/libglib2.0-0/ChangeLog.pre-2-2.gz' is different from the same file on the system

No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)

Errors were encountered while processing:

 /var/cache/apt/archives/libglib2.0-0_2.31.0+git20111115.3a7960f7-0ubuntu1~11.10~ricotz0_amd64.deb

dpkg: dependency problems prevent configuration of libglib2.0-bin:

 libglib2.0-bin depends on libglib2.0-0 (= 2.31.0+git20111115.3a7960f7-0ubuntu1~11.10~ricotz0); however:

  Version of libglib2.0-0 on system is 2.31.0+git20111111.faebf0f6-0ubuntu1~11.10~ricotz0.

dpkg: error processing libglib2.0-bin (--configure):

 dependency problems - leaving unconfigured

dpkg: error processing libglib2.0-0:i386 (--configure):

 libglib2.0-0:i386 2.31.0+git20111115.3a7960f7-0ubuntu1~11.10~ricotz0 cannot be configured because libglib2.0-0:amd64 is in a different version (2.31.0+git20111111.faebf0f6-0ubuntu1~11.10~ricotz0)

Errors were encountered while processing:

I hope I'm missing something obvious here, any ideas? :confused:

Thanks in advance for any help, life sucks with a broken package manager! :)

---

### Post by surfer on 2011-11-17
are you sure your /etc/apt/sources.list points to the correct release?

what is the output of
```
$ lsb_release -av
```
and
```
$ cat /etc/apt/sources.list
```

---

### Post by jchristophe77 on 2011-11-17
Hi,

I had exactly the same problem. I checked the /etc/apt/sources.list, and all are for oneiric.

---

### Post by matt_symes on 2011-11-17
Hi

> 
Preparing to replace libglib2.0-0 2.30.0-0ubuntu4 (using  .../libglib2.0-0_2.31.0+git20111115.3a7960f7-0ubuntu1~11.10~ricotz0_amd64.deb)  ...I think this is what is causing the problem for the OP. 

@jchristophe77 You may have a different problem. Do you see a line the same as above ?

@OP. Try this as a fix.

```
sudo apt-get clean
```Remove (or rename) the ricotz0_amd64 PPA from /etc/apt/sources.list.d/

```
sudo apt-get install -f
```Hopefully that will fix it and pull the correct version down.

Kind regards

---

### Post by jchristophe77 on 2011-11-17
yes, I have this one (in french) : 

Préparation du remplacement de libglib2.0-0 2.31.0+git20111114.469e1a15-0ubuntu1~11.10~ricotz0 (en utilisant .../libglib2.0-0_2.31.0+git20111115.3a7960f7-0ubuntu1~11.10~ricotz0_amd64.deb) ...
Dépaquetage de la mise à jour de libglib2.0-0 ...
dpkg : erreur de traitement de /var/cache/apt/archives/libglib2.0-0_2.31.0+git20111115.3a7960f7-0ubuntu1~11.10~ricotz0_amd64.deb (--unpack) :
 './usr/share/doc/libglib2.0-0/ChangeLog.pre-2-2.gz' is different from the same file on the system
dpkg-deb: error: subprocess coller was killed by signal (Relais brisé (pipe))
Des erreurs ont été rencontrées pendant l'exécution :
 /var/cache/apt/archives/libglib2.0-0_2.31.0+git20111115.3a7960f7-0ubuntu1~11.10~ricotz0_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by matt_symes on 2011-11-17
Hi

@[jchristophe77]("http://ubuntuforums.org/member.php?u=1119370")

Try the steps i posted in #4.

Kind regards

---

### Post by equusaustralus on 2011-11-22
Hi guys, 

Thanks for all the replies! :D

Unfortunately, I couldn't even open gedit to edit the sources.lst file... so I thought a reboot might fix that. What ended up happening is that it ubuntu refused to boot, but would just drop from the pink boot screen to the text and that would flash incessantly. Recovery mode and trying various things from the root prompt also didn't work. 

So I decided to reformat and reinstall the whole thing :S Certainly not the most elegant solution, but I needed it fairly urgently. 

Thanks again!

---

### Post by Aditya Telang on 2011-11-23
I have some problems with my update manager....:confused:

No matter how much i try to update my Ubuntu 11.10 the update manager still shows error saying my updates r due 17 days...
It does install the updates...but i don't know whether all of them are updated..??

HELP.......:(:(:(

I m attaching a screen shot of it after updating my ubuntu..

---

### Post by equusaustralus on 2011-11-23
Hmmm have you tried opening a terminal and typing "sudo apt-get update" (without the inverted commas)? 

Also, you might try going to Settings -> Ubuntu Software, then change the bit where it says Download from: to the Main server, or the United States server, or anything different from the one you have now...

---

### Post by BC59 on 2011-11-23
> **Aditya Telang said:**
> I have some problems with my update manager....:confused:

No matter how much i try to update my Ubuntu 11.10 the update manager still shows error saying my updates r due 17 days...
It does install the updates...but i don't know whether all of them are updated..??

HELP.......:(:(:(

I m attaching a screen shot of it after updating my ubuntu..

First go to **Software Sources** through dash writing Soft on search.

Then from the first tab Ubuntu Software go down to **Download from**:

Then scroll down to **Other** and choose your country from the list. Go now right to  **Select Best Server** and choose a working server. When the system stops searching click at right **Choose Server**

Then close.

To update now better open a terminal with CTRL+ALT+T and copy paste this:


```
sudo apt-get update && sudo apt-get upgrade
```

---

