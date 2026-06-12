---
title: "Update 12.04 problems"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by whynot on 2012-05-06
Hi Everyone

Today i was very happy to update my Ubuntu x64 Natty Narwhal(11.04) to 12.04 but in the beginning it has given "gnome desktop" package error. But i decided to continue.It has to download over 1060 files and i start to wait after a while i check to see whats going on in my computer.I realized that My computer stuck so i have to reboot i rebooted and with ```
dhclient eth0
``` ethernet connection established and then somethin like ```
dpkg --configure -a
```  then ```
sudo apt-get update
``` and ```
sudo apt-get dist-upgrade
``` i complete the process with checking ```
update-manager -d
```.All the packages were installed
But i try to login into Unity desktop there were no top and left bars. Is there any way to reinstall or do this update from the beginning ?

thanks.

---

### Post by whynot on 2012-05-17
Ok
Is there anyway to clean reinstall all packages with out of losing personal Data.
I have still internet connection and working apt-get.
I would appreciated of any help.

---

### Post by whynot on 2012-05-17
This is my source file.
```
# cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted

```

---

### Post by elspru on 2012-05-17
I have a serious 12.04 problem

international fonts just don't work.
I've installed all the font packages,
and did the [B][B][B]sudo fc-cache -f -v 
[/B][/B][/B]To update the font cache.


No Chinese or Japanese is working :-(,
though arabic, hindi and hebrew is.

---

### Post by elspru on 2012-05-17
Hey Whynot   I found your problem, you did a dist-upgrade  which doesn't actually work..   only fresh installs of 12.04 work.   dist-upgrade shall be enabled for 12.04.1

If you'd like to save personal data,  then back it up on either a seperate hard-drive,  ubuntu one,  or a partition you  are very careful with during install.

---

### Post by whynot on 2012-05-17
> **elspru said:**
> Hey Whynot   I found your problem, you did a dist-upgrade  which doesn't actually work..   only fresh installs of 12.04 work.   dist-upgrade shall be enabled for 12.04.1

If you'd like to save personal data,  then back it up on either a seperate hard-drive,  ubuntu one,  or a partition you  are very careful with during install.

Yes, as u said. It could be the problem dist-upgrade. But i found someway out. I dont want to lose my datas so first i found this amazing website [http://repogen.simplylinux.ch/]("http://repogen.simplylinux.ch/") i add my new repositories for 12.04 and then i run 
```
sudo apt-get update 
```
```
sudo apt-get install xubuntu 
```
in login menu i selected xubuntu and xfc desktop is working for me excellent. im going to wait for now updates maybe it works some day.
Thanks.

---

### Post by whynot on 2012-05-17
never mind

---

### Post by jadtech on 2012-05-17
ok well the codes you should have typed to atempt to resume if at all possible were as follows ..

```
 sudo apt-get update

sudo apt-get upgrade -f


```

the -f would build a dependency list Tree,  and would have to attempted to  down load any packages incomplete or missing  and then finished installing them

other command if needed would be install -f this would help things depackage in an order as not to create more dependences issues if possible and stopped giving you a list of thing  you need to  install before it could continue ..

that is how I understand it to be done any how 

in the end configure -a will configure programs  that are opened  and installed not configured before getting  stopped or interupted ..

---

### Post by whynot on 2012-05-17
> **jadtech said:**
> ok well the codes you should have typed to atempt to resume if at all possible were as follows ..

```
 sudo apt-get update

sudo apt-get upgrade -f


```

the -f would build a dependency list Tree,  and would have to attempted to  down load any packages incomplete or missing  and then finished installing them

other command if needed would be install -f this would help things depackage in an order as not to create more dependences issues if possible and stopped giving you a list of thing  you need to  install before it could continue ..

that is how I understand it to be done any how 

in the end configure -a will configure programs  that are opened  and installed not configured before getting  stopped or interupted ..

it works like charm. It has to repair or reinstall two files one of them update-manager and something else.
Now ,Im using my Unity desktop.

Thanks a lot.

---

### Post by jadtech on 2012-05-17
glad it worked good luck Enjoy

---

