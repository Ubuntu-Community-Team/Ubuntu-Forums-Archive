---
title: "GCC: unable to install it"
date: 2005-05-07
forum: Installation &amp; Upgrades
---

### Post by nilus on 2005-05-07
It's about one hour that I try to install It but I'm not able to do.

I need c complilers in my ubuntu distro. Everything is updated. When i try, by Synaptic, to install gcc, g++ and cpp compilers he stops because of dependencies. I tryed with apt-get, the same problem. So I "googled" a lot, and I found anything useful for me.

Is there any right procedure to install correctly all c compilers?

Help me please  ](*,)

---

### Post by nemin on 2005-05-07
[QUOTE=nilus]It's about one hour that I try to install It but I'm not able to do.

I need c complilers in my ubuntu distro. Everything is updated. When i try, by Synaptic, to install gcc, g++ and cpp compilers he stops because of dependencies. I tryed with apt-get, the same problem.[/QUOTE]
Don't you get an error message with apt-get? If you do, post it:)
[QUOTE=nilus]
Is there any right procedure to install correctly all c compilers?[/QUOTE]
apt-get install <the compiler you want> should be enough..

---

### Post by bored2k on 2005-05-07
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
```
sudo apt-get install build-essential
```

---

### Post by nilus on 2005-05-07
This is the problem:

> massimo@ubuntu:~$ sudo apt-get install build-essential
Password:
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso... Fatto
Alcuni pacchetti non possono essere installati. Questo può voler
dire che è stata richiesta una situazione impossibile oppure, se
si sta usando la distribuzione "unstable", che alcuni pacchetti
richiesti non sono ancora stati creati o rimossi da incoming.

Poichè è stata richiesta solo una singola operazione è molto facile che
il pacchetto semplicemente non sia installabile, si consiglia
di inviare un "bug report" per tale pacchetto.
Le seguenti informazioni possono aiutare a risolvere la situazione:

I seguenti pacchetti hanno dipendenze non soddisfatte:
  build-essential: Dipende: gcc (>= 3:3.3) ma non sta per essere installato
                   Dipende: g++ (>= 3:3.3) ma non sta per essere installato
E: Pacchetto non integro
massimo@ubuntu:~$

I hope you can understand just a bit of italian ;)

---

### Post by bored2k on 2005-05-07
Show us your souces.list (cat /etc/apt/sources.list).
And no I barely understood a thing (and I'm hispanic :\)

---

### Post by nilus on 2005-05-07
The meaning of that screen was that gcc and g++ have no satisfied dependencies (i don't know if i translate it correctly).

> massimo@ubuntu:~$ sudo cat /etc/apt/sources.list
 ## Uncomment the following two lines to fetch updated software from the networkdeb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) hoary java
massimo@ubuntu:~$

Thank you for your help.

---

### Post by bored2k on 2005-05-07
[QUOTE=nilus]The meaning of that screen was that gcc and g++ have no satisfied dependencies (i don't know if i translate it correctly).



Thank you for your help.[/QUOTE]
 Uhm.. I'm throwing the towel here, you got everything right. I'd only suggest blocking marillat's or removing them, updating then retrying.. :roll:

---

### Post by nilus on 2005-05-07
[QUOTE=bored2k]Uhm.. I'm throwing the towel here, you got everything right. I'd only suggest blocking marillat's or removing them, updating then retrying.. :roll:[/QUOTE]
Also using synaptic I have the same problem.

Is there a fast way to configure the terminal in english so You can understand what is written there? Otherwise I'm not very good in english and i can't describe the problem very well  ](*,)

---

### Post by bored2k on 2005-05-07
[QUOTE=nilus]Also using synaptic I have the same problem.

Is there a fast way to configure the terminal in english so You can understand what is written there? Otherwise I'm not very good in english and i can't describe the problem very well  ](*,)[/QUOTE]
 You can install english localization files and xnest, then run a nested english window.
But dont worry, these are usually generic messages. 

About synaptic. Its a front end to apt, so it will display the same problems.
Could you remove all repositories, update, then copy them again from the guide and retry ? cause its really weird you cant install gcc. 

and why warty,,

---

### Post by nilus on 2005-05-07
Now there's a new problem, damn...
Trying to uninstall the last applications i get *Error 1* from post-installation script of  *libtool*  ](*,)

---

### Post by nilus on 2005-05-07
I Don't know why but now It works ;)

I used dselect (I don't know very well that I did in fact :D ) but after that i was able to install gcc and g++ . Yea!

---

### Post by cutOff on 2005-05-07
```
http://archive.ubuntu.com/ubuntu/ warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
``` 
Here's the error. It should be like that

```
deb http://archive.ubuntu.com/ubuntu/ warty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted
```

---

### Post by nilus on 2005-05-08
The other big error is that i have hoary and not warty  ](*,) 

By the way, now sources.list is correct and C/C++ compilers are correctly installed ;)

---

