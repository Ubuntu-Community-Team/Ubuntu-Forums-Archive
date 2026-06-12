---
title: "Kill prelink ? during upgrade."
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by Dutch on 2006-06-03
Hi upgrading on the P IV 3 Ghz went ok !
Upgrading on the Celeron 500Mhz went also ok till he began with running prelink.

He is already busy with running prelink from 11:00 hrs this morning till now ( 20:00).
The processor use is constantly 100% ( 9 hours already)
Is it possible to stop this (with an other terminal) ore have I just sit it out ?

---

### Post by paul cooke on 2006-06-03
[QUOTE=Dutch]Hi upgrading on the P IV 3 Ghz went ok !
Upgrading on the Celeron 500Mhz went also ok till he began with running prelink.

He is already busy with running prelink from 11:00 hrs this morning till now ( 20:00).
The processor use is constantly 100% ( 9 hours already)
Is it possible to stop this (with an other terminal) ore have I just sit it out ?[/QUOTE]

READ MY CAVEAT BELOW FIRST before doing this>>>

CAVEAT>>>>>

I'm not sure if killing prelink will cause any harm. I forgot about prelink myself, although, with my 3 Gig box, the prelink only lasted for 3 hours before the install carried on. You should be close to the end anyway by now... ;)

I'd leave prelink running as I think there may be problems if you don't let it finish.

Perhaps someone with more knowledge of prelink could help here as to whether you'd have problems if you killed prelink.

end of CAVEAT>>>

open another terminal

launch the command line program top as root by doing

sudo top

and enter your password at the prompt

(you need to be root as prelink was called by apt-get running as root)

find the process for prelink and "kill" it using the k command in top. You will be prompted for the process id number of the process to kill. Give it the one for the prelink program and then type a return at the next prompt... that should kill the prelink process and allow you to carry on with the upgrade.

---

### Post by ubuntu_demon on 2006-06-03
$ps aux | grep prelink
gives you a number of the process prelink. Let's call it pid.
$sudo kill *pid* 

if it doesn't want to stop use the -9 switch :
$sudo kill *pid* -9

do a reboot :
$sudo reboot 

start prelink again and hope that it will take less time :
$sudo /etc/cron.daily/prelink

If not you should search the forums for the prelink howto you followed. There's probably instructions on how to disable it.

good luck :)

---

### Post by Dutch on 2006-06-03
[QUOTE=ubuntu_demon]$ps aux | grep prelink
gives you a number of the process prelink. Let's call it pid.
$sudo kill *pid* 

if it doesn't want to stop use the -9 switch :
$sudo kill *pid* -9

do a reboot :
$sudo reboot 

start prelink again and hope that it will take less time :
$sudo /etc/cron.daily/prelink

If not you should search the forums for the prelink howto you followed. There's probably instructions on how to disable it.

good luck :)[/QUOTE]


This HowTo does not exist UD.
We dit this with an MSN sesion some time ago.

First I'll try ure suggestions.
But I'm afraid that I lose data.

Can that hapen ?

---

### Post by ubuntu_demon on 2006-06-03
I told you the information based on a howto. Here it is :

[http://www.ubuntuforums.org/showthread.php?t=74197](http://www.ubuntuforums.org/showthread.php?t=74197)

It has also information about how to unde prelink if necessary.

In practice the worst what could happen is that you can't start some program anymore. If you can't start some application anymore you should reinstall it's corresponding package :

$sudo apt-get install packagename --reinstall 

If necessary (though it very likely won't be necessary) use the -f switch :
$sudo apt-get install packagename --reinstall -f

---

### Post by Dutch on 2006-06-03
Ok thanks UD.
I'll wait till tomorrow.

With the 3Ghz it took 3 hours (see above)
Mine is 500 Mhz so its gone take like 18 hours.

I've had already 11 hours I hade enough.
I'll try and let u now what went good !

Maybe something to point out with the upgrading stuf ? >>> shut down prelink ?

Thanks,

Paul.

---

### Post by ubuntu_demon on 2006-06-03
Don't run your processor for 100% for 18 hours. You **may damage it**. Especially if your cooling is inadequate and your pc becomes too hot.

---

### Post by Dutch on 2006-06-03
[QUOTE=ubuntu_demon]Don't run your processor for 100% for 18 hours. You **may damage it**. Especially if your cooling is inadequate and your pc becomes too hot.[/QUOTE]

Thanks UD
That exactly what I felt.
Also I had enough of it.

I tried ure suggestion but got stuk with the nr. of proces to kill.
Then I just did schift+ctr+c aand stoped the prelink.

Tried to fix broken packages but he did not find anything.

Rebooted went ok, and shut down prelink (filed NO in .conf file)
Now I miss the half of my menu settings but never mind.
I'v got my old mails and I believe also the 1G aan .doc files >> move them to my new PC and then maybe make a server off the good old Celeron !

Thanks !

---

### Post by ubuntu_demon on 2006-06-03
Take a look at this guide to make sure everything is installed allright and there are no dependencies issues :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

especially this part :
> 
Let's run this command again to make sure it has removed everything that's problematic :
$ sudo apt-get -f remove

Let's now configure all packages that are still unconfigured :
$ sudo dpkg --configure -a

Now there are no more broken dependencies and all packages are configured. Let's install everything :

$ sudo apt-get install ubuntu-minimal
$ sudo apt-get install ubuntu-base
$ sudo apt-get install ubuntu-desktop
(or kubuntu / edubuntu / xubuntu)

And make sure everything is upgraded :
$ sudo apt-get update
$ sudo apt-get dist-upgrade

If everything went well your broken dependencies problem is fixed.

Now do a reboot :
$ sudo reboot


---

