---
title: "dpkg error - New Mail"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by nixfreak on 2007-03-02
I have Ubuntu server installed on my server with VHCS

Im really new at linux, its only been a day since i started using ubuntu on my server, im trying to install Kubuntu on it, but while installing i get this error and installation stops:

```
E: Sub-process /usr/bin/dpkg returned an error code (1)
You have new mail in /var/mail/nemesyz
```

plz tell me how to get rid of this problem and how to continue installation from where it stopped

10x in advance

Freak

---

### Post by nixfreak on 2007-03-02
I have Ubuntu server installed on my server with VHCS

Im really new at linux, its only been a day since i started using ubuntu on my server, im trying to install Kubuntu on it, but while installing i get this error and installation stops:

```
E: Sub-process /usr/bin/dpkg returned an error code (1)
You have new mail in /var/mail/nemesyz
```

plz tell me how to get rid of this problem and how to continue installation from where it stopped

10x in advance

Freak

---

### Post by taurus on 2007-03-02
What are the outputs when you run these two commands at a prompt?

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by invalid on 2007-03-02
What does it say leading up to the error?
You can check your mail by typing```
mail
```

---

### Post by nixfreak on 2007-03-02
> **invalid said:**
> What does it say leading up to the error?
You can check your mail by typing```
mail
```

10x for the reply  

Ok used mail, showed me the new mails, now how do i continue the installation?







> **taurus said:**
> What are the outputs when you run these two commands at a prompt?

```
sudo aptitude update
sudo aptitude upgrade
```


i already did    sudo apt-get update

i did sudo aptitude update anyway...it just updated it again

when i use sudo aptitude upgrade...it started installing somthing and then gave me this option...idont know what to choose and dont wanna mess up :( ....plz help me configure it proerly




```
Configuration file `/etc/issue'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** issue (Y/I/N/O/D/Z) [default=N] ?
```

I mean what would it install if i say yes? i want to continue with Kubuntu setup, its not gonna messup kubuntu setup would it?


10x alot

Freak

---

### Post by taurus on 2007-03-02
Hit **Y** for the answer to that question.

---

### Post by nixfreak on 2007-03-02
ok i did, this is what i get



```
Setting up base-files (3.1.9ubuntu7.1) ...

Configuration file `/etc/issue'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** issue (Y/I/N/O/D/Z) [default=N] ? y
Installing new version of config file /etc/issue ...

Configuration file `/etc/issue.net'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** issue.net (Y/I/N/O/D/Z) [default=N] ? y
Installing new version of config file /etc/issue.net ...
Installing new version of config file /etc/lsb-release ...

Setting up libc6-i686 (2.3.6-0ubuntu20.4) ...

Setting up kubuntu-artwork-usplash (6.06-22) ...
Cannot find /lib/modules/2.6.15-23-server
dpkg: error processing kubuntu-artwork-usplash (--configure):
 subprocess post-installation script returned error exit status 1
Setting up usplash (0.2-4) ...
Cannot find /lib/modules/2.6.15-23-server
dpkg: error processing usplash (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of kubuntu-desktop:
 kubuntu-desktop depends on kubuntu-artwork-usplash; however:
  Package kubuntu-artwork-usplash is not configured yet.
 kubuntu-desktop depends on usplash; however:
  Package usplash is not configured yet.
dpkg: error processing kubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kubuntu-artwork-usplash
 usplash
 kubuntu-desktop

```

---

### Post by taurus on 2007-03-02
How did you install KDE before?

Try something like

```
sudo aptitude -f install
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by nixfreak on 2007-03-02
> **taurus said:**
> How did you install KDE before?

Try something like

```
sudo aptitude -f install
sudo aptitude update
sudo aptitude install kubuntu-desktop
```


i used sudo apt-get install kubuntu-desktop


i just tried sudo aptitude -f install, gives me the same error :(


If i use sudo aptitude install kubuntu-desktop , wouldnt it start the setup all over again?

---

### Post by nixfreak on 2007-03-02
plz anyone?

---

### Post by nixfreak on 2007-03-03
ok i noticed when i try to do upgrade or try installing again the error it gives  has this in it:

```
dpkg: error processing usplash (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of kubuntu-desktop:
 kubuntu-desktop depends on kubuntu-artwork-usplash; however:
  Package kubuntu-artwork-usplash is not configured yet.
 kubuntu-desktop depends on usplash; however:
  Package usplash is not configured yet.

```


so how do i configure  kubuntu-artwork-usplash

10x in advace

Freak

---

