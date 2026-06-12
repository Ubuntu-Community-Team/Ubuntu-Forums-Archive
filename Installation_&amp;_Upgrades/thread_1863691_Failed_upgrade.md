---
title: "Failed upgrade"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by EddieGal on 2011-10-18
Hi

Let me see if I can explain myself right.

I was doing the upgrade from 11.04 to 11.10, and info, install-info and ubuntu-standard failed, I tried to re-install through synaptic but this failed.

Then I restarted the system, and I get to login screen right, but when I type the password I get 'failed to load session "UBUNTU"'

Don't know where to go from this.

---

### Post by 23dornot23d on 2011-10-18
Can you press Ctrl+Alt+F1

To get to a shell terminal and login using your username and password

then type

sudo apt-get update

**sudo apt-get install ubuntu-desktop**

let me know what the output is please to the last command

then press ctrl+alt+F7

and try lo go in again

---

### Post by EddieGal on 2011-10-18
Getting this after downloading a few packages

Configuring install-info (4.13.dfsg.1-8ubuntu1 ...
etc/enviroment: line 3: UNITY_FORCE_START=1: order not found
dpkg: error while processing install-info (--configure)
the installed sub-process the script post-installation returned the exit error code 127
Errors were found while processing:
install-info
E: sub-process /usr/bin/dpkg returned an error code (1)


I had to translate from spanish so some words might not be exact.

---

### Post by EddieGal on 2011-10-18
Anyone can help with that ?

---

### Post by flangemonkey on 2011-10-18
try

```

sudo dpkg --configure -a
```

si no funciona

```

sudo su
apt-get clean
apt-get update
apt-get upgrade
logout
```

and if still fails, tell us the output of

```

df -Th
ifconfig | grep inet
```

---

### Post by EddieGal on 2011-10-18
Gracias :p

I'll keep writing in English so more people can help ;)

After doing the first two steps I get this:

```

Configurando install-info (4.13a.dfsg.1-8ubuntu1) ...
/etc/environment: línea 3: UNITY_FORCE_START=1: orden no encontrada
dpkg: error al procesar install-info (--configure):
 el subproceso instalado el script post-installation devolvió el código de salida de error 127
Se encontraron errores al procesar:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

df -Th output

```

/dev/sda5     ext3     11G  6,3G  3,7G  64% /
udev      devtmpfs   1000M  4,0K 1000M   1% /dev
tmpfs        tmpfs    403M  864K  402M   1% /run
none         tmpfs    5,0M     0  5,0M   0% /run/lock
none         tmpfs   1007M  104K 1007M   1% /run/shm
/dev/sda6     ext3     55G   34G   19G  65% /home
/dev/sda1  fuseblk    7,0G  5,9G  1,2G  84% /media/Recovery Partition
/dev/sda4  fuseblk     13G  2,8G  9,5G  23% /media/ampliacion
/dev/sda2  fuseblk     63G   31G   33G  49% /media/VAIO
/dev/sdb1     vfat    3,6G  703M  3,0G  20% /media/KINGSTON

```


ifcongig | grep inet

```

Direc. inet:192.168.1.36  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::213:a9ff:fe0a:99fe/64 Alcance:Enlace
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
```

---

### Post by flangemonkey on 2011-10-18
hmm

[http://kubuntuforums.net/forums/index.php?topic=3114385.0]("http://kubuntuforums.net/forums/index.php?topic=3114385.0") suggests

```

sudo apt-get dist-upgrade -f

```

otherwise there are more complicated solutions in

[http://ubuntuforums.org/showthread.php?t=1346497]("http://ubuntuforums.org/showthread.php?t=1346497")
 and
[http://ubuntuforums.org/showthread.php?t=541998]("http://ubuntuforums.org/showthread.php?t=541998")

if you need help, or it all works let us know :)

---

### Post by EddieGal on 2011-10-18
Gracias again :D

A bit of update, got to get into the Ubuntu session by removing quotation marks from UNITY_FORCE_START=1 on environment as that was edited from 11.04

Now that I got into Ubuntu, don't have the windows decorations working properly.

Will try that step again.

---

### Post by EddieGal on 2011-10-18
Yay, that worked for the update :D


Now to resolve the other problems :) Like Unity not working etc,

---

### Post by 23dornot23d on 2011-10-18
Have a look in the link below for other [COLOR=Red]SOLVED[/COLOR] threads on UNITY ......

You have marked this thread as solved too ..... so people may not realise that you have 
other issues ...... 

I have marked it on my list .... as needing more help - 

But if you have new problems then it may be worth opening a thread for them seperate
one that is not marked [COLOR=Red]SOLVED[/COLOR]

---

### Post by EddieGal on 2011-10-18
Yeah, this was marked as SOLVED because it was about the upgrading process and its errors.

UNITY is a different issua as I think the problem is the graphics card itself, it's a Nvidia 7400Go, and that wasn't supported in 11.04.

Good thing to put in the title "now other problems" or leave as it is right now ?

---

### Post by 23dornot23d on 2011-10-18
I would probably put it out again in a clean thread as 

Nvidia 7400Go and UNITY problem .....

otherwise it may get overlooked ...

---

### Post by EddieGal on 2011-10-18
Thank you. :)

---

