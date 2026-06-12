---
title: "secondlife , install and remove , corrupted package !"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by hamzamusa on 2008-02-14
Hi , 

I Install the Second-life from [http://www.getdeb.net/](http://www.getdeb.net/) , and it was unsuccessful tryout , freezing soon as the character starts moving .

so i tried to removed the installed package , from Synaptic , and sometimes later i can't install any other package and the synaptic as well as the update manager is stuck , with error dialog that concern the game :

```
A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package secondlife-install needs to be reinstalled, but I can't find an archive for it.'
``` 

so i ran :

```
sudo dpkg --configure -a
```

but the problem wont fix , yet .

also i tried to re-install the package , but it says "
> The Package might be corrupted or you are not allowed to open the file . check the permissions of the file "

any suggestions ?

---

### Post by hamzamusa on 2008-02-14
Solved :

> 1. sudo gedit /var/lib/dpkg/status
2. Delete the section for libavahi-core5.
3. sudo mv /var/lib/dpkg/info /var/lib/dpkg/info_old
4. sudo mkdir /var/lib/dpkg/info
5. sudo apt-get update
6. sudo apt-get -f install


[http://ubuntuforums.org/showthread.php?t=654692](http://ubuntuforums.org/showthread.php?t=654692)

and Thanks

---

### Post by jdunn on 2008-02-16
Is there any advantage to installing SL from the repositories or as deb packages?  When downloading the game from secondlife.com you don't even need to do a build to install the game.  Simply unzip the game to the folder of your choice and execute.  I had to get some additional packages from the repositories to play streaming video...even so, I can only play some videos.

---

### Post by hamzamusa on 2008-02-16
Yes , I know , but it still crashes , as well , as well as i decided to try the packaged one to see it it'll not crash as the official one .

may i know what addional packages ?

---

### Post by jdunn on 2008-02-16
> **hamzamusa said:**
> Yes , I know , but it still crashes , as well , as well as i decided to try the packaged one to see it it'll not crash as the official one .

may i know what addional packages ?

check here  [http://ubuntuforums.org/showthread.php?t=685881&highlight=secondlife]("http://ubuntuforums.org/showthread.php?t=685881&highlight=secondlife")

---

