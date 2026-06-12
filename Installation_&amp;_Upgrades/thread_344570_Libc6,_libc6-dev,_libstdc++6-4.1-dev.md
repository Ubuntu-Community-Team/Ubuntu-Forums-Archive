---
title: "Libc6, libc6-dev, libstdc++6-4.1-dev"
date: 2007-01-23
forum: Installation &amp; Upgrades
---

### Post by LeDieu on 2007-01-23
Hi,

I just started my ubuntu machine (edgy eft) and i got some updates. Only when i started the update (there was a update for libc6 and libc6-dev) i got an error that i got a broken package. I tried to remove it but the error is coming back. I have taken a look in aptitude my self and when i try do download libc6 and libc6-dev by myself i get the text that the package libstdc++6-4.1-dev is broken.
Even when i try to remove the package completely and then install again i get the error. I think that the error is in the package. Is this possible?

I hoop someone can help me with this problem.

Greetz,
LeDieu

---

### Post by L0rd_D4rk on 2007-01-23
I think that I have the same problem, here is the full output from aptitude, i hope it will be useful to find a solution.

```
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
Se actualizarán los siguientes paquetes:
  libc6 libc6-amd64 libc6-dbg libc6-dev libc6-dev-amd64 libc6-i686 libc6-xen libtotem-plparser1 totem totem-xine 
10 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B/20,8MB de ficheros. Después de desempaquetar se usarán 0B.
¿Quiere continuar? [Y/n/?] 
Escribiendo información de estado extendido... Hecho
(Leyendo la base de datos ...  
309837 ficheros y directorios instalados actualmente.)
Preparando para reemplazar libc6 2.4-1ubuntu12 (usando .../libc6_2.4-1ubuntu12.2_i386.deb) ...
Matching libraries: /usr/lib/libdl.so.2 /lib/ld-linux.so.2

A copy of glibc was found in an unexpected directory.
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library and try again.
dpkg: error al procesar /var/cache/apt/archives/libc6_2.4-1ubuntu12.2_i386.deb (--unpack):
 el subproceso pre-installation script devolvió el código de salida de error 1
Se encontraron errores al procesar:
 /var/cache/apt/archives/libc6_2.4-1ubuntu12.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Un paquete no se pudo instalar. Intentado recuperarse:

```

I don't know if doing something like **dpkg --force-all -i /var/cache/apt/archives/libc6_2.4-1ubuntu12.2_i386.deb** would solve the problem but I prefer to wait to a more professional solution :D 

I'm running Ubuntu 6.10 (kernel 2.6.17-10-386) from the official repos, except from Beryl-SVN and NVIDIA beta driver.

---

### Post by LeDieu on 2007-01-23
Some more information:

This is my output from the command: sudo apt-get install -f

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  putty-tools mysql-query-browser-common libtdb1 adept-common debtags
  apt-index-watcher libxine1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6 libc6-i686
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6 libc6-i686
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/5253kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 100918 files and directories currently installed.)
Preparing to replace libc6 2.4-1ubuntu12 (using .../libc6_2.4-1ubuntu12.2_i386.deb) ...
Matching libraries: /usr/lib/libpthread.so.20 /lib/ld-linux.so.2

A copy of glibc was found in an unexpected directory.
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library and try again.
dpkg: error processing /var/cache/apt/archives/libc6_2.4-1ubuntu12.2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.4-1ubuntu12.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I hope this helps becaus at this moment i cant update at all.

LeDieu

---

### Post by syoung on 2007-01-23
Getting the exact same problem this morning when I powered on.

---

### Post by hectare on 2007-01-23
I also got update pkg list which contained libc6 , but i did not upgrade ,i have posted the query regarding upgrade of libc6 here [http://ubuntuforums.org/showthread.php?t=344636](http://ubuntuforums.org/showthread.php?t=344636)
Hopefuly someone with know how will answer.

---

### Post by LeDieu on 2007-01-23
> **hectare said:**
> I also got update pkg list which contained libc6 , but i did not upgrade ,i have posted the query regarding upgrade of libc6 here [http://ubuntuforums.org/showthread.php?t=344636](http://ubuntuforums.org/showthread.php?t=344636)
Hopefuly someone with know how will answer.

I understand that i can choose to not update my libc6 but at this moment my hole aptitude application does not work. Every time i get the message that i have to execute the command "sudo apt-get -f install" but if i do that i get the error from libc6 that there is a read/unpack error. So libc6 update is not necessary but get my aptitude working is.

---

### Post by lcohen999 on 2007-01-23
I have the same update, it failed

I rebooted, now I get a libc error and a kernel panic

I have no idea how I can recover....!

---

### Post by Frostbane on 2007-01-23
I'm having the exact same problem. I'll try to work on it some more and see if there is anything I can discover.

Edit:

Read that there were problems with the package and dependencies with libpthread from [http://shearer.org/Debugging_Dpkg_Problems](http://shearer.org/Debugging_Dpkg_Problems) and i tried it but it did not work for me; in fact, now my xserver won't run anymore after reboot, can't reinstall xserver either because of the dep problem with libc6. 

I could really use some help with this issue, I'll continue checking back and see if you guys come up with anything.

---

### Post by Ezequiel on 2007-01-23
Hey, I had the same problem. And I found the solution here: [http://shearer.org/Debugging_Dpkg_Problems](http://shearer.org/Debugging_Dpkg_Problems)

The first thing I would recommend to you is: do not restart, your X session won't be able to work again. If you happened to have reseted the system you will be able to log in "recovery mode".

The steps I used to solve where:
cd /usr/lib
mkdir temp
mv libpthread* temp
dpkg -i  /var/cache/apt/archives/libc6_2.4-1ubuntu10_i386.deb

and then

apt-get install -f
to continue with the dependencies.

Hope it works for you too!
Bye

Edit: After doing this you can move back the libpthread* files to the /usr/lib dir

---

### Post by WW on 2007-01-23
Ezequiel,

Your instructions temporarily move files from /lib, but the instructions in the shearer.org link move files from /usr/lib.  Is it really /lib?

WW

---

### Post by bastiegast on 2007-01-23
Im having the same problem, and for me, the updater removed an enormous bunch of packages, they were gone before I could hit cancel. I tried the above but it doesn't work:```
sudo dpkg -i /var/cache/apt/archives/libc6_2.4-1ubuntu12.2_i386.deb 
(Database inlezen ... 162858 bestanden en mappen geïnstalleerd.)
Voorbereiden om libc6 2.4-1ubuntu12.1 te vervangen (door .../libc6_2.4-1ubuntu12.2_i386.deb) ...
Matching libraries: /usr/lib/libpthread.so.20 /lib/ld-linux.so.2

A copy of glibc was found in an unexpected directory.
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library and try again.
dpkg: fout bij afhandelen van /var/cache/apt/archives/libc6_2.4-1ubuntu12.2_i386.deb (--install):
 subproces pre-installation script gaf een foutwaarde 1 terug
Fouten gevonden tijdens behandelen van:
 /var/cache/apt/archives/libc6_2.4-1ubuntu12.2_i386.deb

```

---

### Post by Handssolow on 2007-01-23
Just posted about this on the media and video section. After today's updates I got a Real Payer update showing. Unable to update I uninstalled Real Player now I'm unable to re-install without this error.
realplay:
  Depends: libc6 (>=2.5-0ubuntu1) but 2.4-1ubuntu12.2 is to be installed

---

### Post by Ezequiel on 2007-01-23
sorry, it was /usr/lib... I corrected it

---

### Post by Frostbane on 2007-01-23
I had to shuffle around a few more libraries, but it finally worked. :D

---

### Post by Ezequiel on 2007-01-23
You should be careful about messing with these libraries... erasing something like the libc-6.so symlink can render your system unusable (And you can't execute ln to create the symlink once that happens)

If that happens the only solution I found was to restart using the Live CD, mounting the hd and restoring the erased links.

---

### Post by snowx1000 on 2007-01-23
Filed a bug on lauchpad just to make sure devs are aware. The update gave me the same issues.

---

### Post by lcohen999 on 2007-01-23
what a mess.

I ended up doing a sudo cp -i /lib /mount/lib and say no to any files that already existed.

That seemed to get my system back up, I then did a sudo dpkg -f libc6 and it seemed to clean everything up.

This is a huge bug that took down my workstation.  I hope they pull it from update manager until this is resolved, or post it somewhere very noticble

---

### Post by L0rd_D4rk on 2007-01-23
Anyone knows what exactly has caused this problem??, I suppose this is not a general bug because not all people is affected. I have been updating my computer from one version to another without reinstalling since breezy, so it's possible that the problem isn't from edgy itself but from another version that left the libraries in the wrong place...

I think that I'm going to wait a couple of days before dist-upgrading to see if the developers give us a solution...

---

### Post by LeDieu on 2007-01-23
It works perfectly many thanks :D.

---

### Post by IronMan7491 on 2007-01-23
I too am having problems with the same library. I tried downgrading the package but I seem to have made things worse.

My error message is:

libc6-dev: Depends: libc6 (=2.4-1ubuntu12.2) but 2.4-1ubuntu12 is installed and it is kept back

---

### Post by lorenco on 2007-01-24
Same problem here

Posted earlier [over here]("http://ubuntuforums.org/showthread.php?t=345318")

This is a fresh install of Edgy (a while back)
Seems like Build Essential has got something to do with this.

BTW I had to recover from Live CD (Feisty :p) after I removed the two libs....
Ouch..... Be careful.

---

### Post by cjwatson on 2007-01-24
I've asked Michael Vogt to fix the realplay package in edgy-commercial.

---

### Post by cjwatson on 2007-01-24
Several of us at the Ubuntu distro team sprint in Oslo are looking into this. We believe we understand the error that mentions libpthread, and will have a candidate fix for that soon, but this libdl error is a mystery. Could you please describe for us an exact procedure by which we can reproduce this? Describing exactly what you did with Beryl and the NVIDIA beta driver will help.

I highly recommend NOT following instructions that involve haphazardly removing libraries from /lib, /usr/lib, or whatever. Doing this may damage your system beyond all but expert repair, and will impair our ability to test whether fixes we provide are correct.

---

### Post by cjwatson on 2007-01-24
This is [http://launchpad.net/bugs/81125](http://launchpad.net/bugs/81125)

---

### Post by lorenco on 2007-01-24
Just a couple things from my side:

The only thing I installed extra is WINE from Wine HQ (as part of sources list)
my sources list:
> 
deb [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy main restricted
deb [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy universe
deb-src [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy universe
deb [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) edgy-security main restricted
#vvvv This is the WINE updates
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main



I also installed build essential that I required to get VMWare Server to work... Other than that I just updated my system as requested ...

This happened after the update from last week (?) Can't remember when this started ut it was a couple of days ago upgrading glibc....

Here is my output:

> sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6 libc6-i686
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6 libc6-i686
2 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 0B/5253kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 168137 files and directories currently installed.)
Preparing to replace libc6 2.4-1ubuntu12 (using .../libc6_2.4-1ubuntu12.2_i386.deb) ...
Matching libraries: /usr/lib/libdl.so.2 /lib/ld-linux.so.2

A copy of glibc was found in an unexpected directory.
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library and try again.
dpkg: error processing /var/cache/apt/archives/libc6_2.4-1ubuntu12.2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.4-1ubuntu12.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



---

### Post by IronMan7491 on 2007-01-24
> **cjwatson said:**
> Could you please describe for us an exact procedure by which we can reproduce this? Describing exactly what you did with Beryl and the NVIDIA beta driver will help.


I have beryl-svn and the NVIDIA driver(not beta). I installed the updates on 1/23, rebooted and got a failed Xserver. Then I tried downgrading the package as apt suggested, now I have a really broken system.

---

### Post by cjwatson on 2007-01-24
Michael has fixed realplay in edgy-commercial now. Thanks for your report.

---

### Post by mdz on 2007-01-24
> **Ezequiel said:**
> You should be careful about messing with these libraries... erasing something like the libc-6.so symlink can render your system unusable (And you can't execute ln to create the symlink once that happens)

If that happens the only solution I found was to restart using the Live CD, mounting the hd and restoring the erased links.

Yes, this is why it is dangerous to give this type of advice.  Not only can you easily make your own system unbootable, you can do the same (or worse) for thousands of other users who attempt to follow your example.

---

### Post by mdz on 2007-01-24
> **lcohen999 said:**
> what a mess.

I ended up doing a sudo cp -i /lib /mount/lib and say no to any files that already existed.

That seemed to get my system back up, I then did a sudo dpkg -f libc6 and it seemed to clean everything up.

This is a huge bug that took down my workstation.  I hope they pull it from update manager until this is resolved, or post it somewhere very noticble

The bug referenced here causes no harm to the system; it only causes the update to fail to install.  Everything should work as normal.

HOWEVER, many of the "workarounds" and "fixes" posted here will cause SERIOUS DAMAGE to your system which can be difficult or impossible for most users to correct.  Please do not attempt manual workarounds, as they can easily replace a small problem with a very serious one!

---

### Post by fog on 2007-01-24
The same problem here:
>  Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12.2_i386.deb)

---

### Post by keybuk on 2007-01-24
We are trying to understand why people have libpthread20 installed, as it's not used by anything in the Ubuntu archive...

Could people supply the output of:

    zgrep pthread /var/log/dpkg.log*

---

### Post by WhO_KnOwS on 2007-01-24
Just did a clean install at a friends house.
After the install was done I tried updating the system (that is before any package was actually installed). During the update the Libc6 packages all returned a **403: Forbidden** when apt tried to DL them. At that point I canceled the upgrade so the system remains stable.
Just thought I should let you know.

---

### Post by snowx1000 on 2007-01-25
/var/log/dpkg.log.2.gz:2006-11-19 16:48:29 install libpthread20 <none> 2.0.7-2ubuntu2
/var/log/dpkg.log.2.gz:2006-11-19 16:48:29 status half-installed libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.2.gz:2006-11-19 16:48:29 status unpacked libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.2.gz:2006-11-19 16:48:29 status unpacked libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.2.gz:2006-11-19 16:48:29 install libpthread-dev <none> 2.0.7-2ubuntu2
/var/log/dpkg.log.2.gz:2006-11-19 16:48:29 status half-installed libpthread-dev 2.0.7-2ubuntu2
/var/log/dpkg.log.2.gz:2006-11-19 16:48:29 status not-installed libpthread-dev <none>
/var/log/dpkg.log.2.gz:2006-11-19 16:48:29 status unpacked libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.2.gz:2006-11-19 16:48:29 status half-configured libpthread20 2.0.7-2ubuntu2
/var/log/dpkg.log.2.gz:2006-11-19 16:48:33 status installed libpthread20 2.0.7-2ubuntu2


> **keybuk said:**
> We are trying to understand why people have libpthread20 installed, as it's not used by anything in the Ubuntu archive...

Could people supply the output of:

    zgrep pthread /var/log/dpkg.log*

---

### Post by snowx1000 on 2007-01-25
The new libc6 package works great, thank you to everyone who helped!

---

