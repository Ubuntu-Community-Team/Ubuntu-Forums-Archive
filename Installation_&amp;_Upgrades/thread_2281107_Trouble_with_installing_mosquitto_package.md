---
title: "Trouble with installing mosquitto package"
date: 2015-06-04
forum: Installation &amp; Upgrades
---

### Post by discosrule on 2015-06-04
Trying to install latest mosquitto on my Ubuntu 12.04.5 LTS using the Ubuntu [PPA]("http://mosquitto.org/download/")

but keep getting this error; 
[B]mosquitto : Depends: lsb-base (>= 4.1+Debian3) but 4.0-0ubuntu20.3 is to be installed
[/B]

```
sudo apt-get install mosquitto -f

Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mosquitto : Depends: lsb-base (>= 4.1+Debian3) but 4.0-0ubuntu20.3 is to be installed
E: Unable to correct problems, you have held broken packages.
```

Any help would be appreciated.

Thx.

---

### Post by gordintoronto on 2015-06-04
Google this: ubuntu broken packages

---

### Post by ian-weisser on 2015-06-04
> **discosrule said:**
> mosquitto : Depends: lsb-base (>= 4.1+Debian3) but 4.0-0ubuntu20.3 is to be installed

You have indeed requested an impossible situation, just as the package manager tried to warn you.
Your non-Ubuntu version of mosquitto has a dependency.
That dependency has a *version conflict*.
That's why the system has held broken packages.

Version conflicts  cannot be *forced* (-f). They must be *resolved* by you...the human who gave the system two incompatible instructions.
1) "Install Ubuntu"
2) "Install a version of mosquitto that conflicts with Ubuntu"

Is the version of mosquitto in the Ubuntu repositories inadequate?

---

### Post by matt_symes on 2015-06-04
Hi

It's in the repositories.

```

matthew-laptop:/home/matthew/bin:3 % acse mosquitto
libmosquitto0 - MQTT version 3.1 client library
libmosquitto0-dev - MQTT version 3.1 client library, development files
libmosquittopp0 - MQTT version 3.1 client C++ library
libmosquittopp0-dev - MQTT version 3.1 client C++ library, development files
mosquitto - MQTT version 3.1 compatible message broker
mosquitto-clients - Mosquitto command line MQTT clients
python-mosquitto - MQTT version 3.1 client library, python bindings
matthew-laptop:/home/matthew/bin:3 %
```

 Any reason you are trying to use a PPA ?

Kind regards

---

### Post by discosrule on 2015-06-05
> **matt_symes said:**
> Hi



 Any reason you are trying to use a PPA ?



The Ubuntu one is a Very old version.... PPA is the latest. 


Haven't had a problem in the past doing it this way.

---

### Post by matt_symes on 2015-06-05
Hi

> **discosrule said:**
> Very old version.

Haven't had a problem in the past doing it this way.

Are you using this PPA ?

[https://launchpad.net/~mosquitto-dev/+archive/ubuntu/mosquitto-ppa](https://launchpad.net/~mosquitto-dev/+archive/ubuntu/mosquitto-ppa)

as recommended.

> If you are on an earlier version of Ubuntu or want a more recent version of mosquitto, add the [mosquitto-dev PPA]("http://launchpad.net/%7Emosquitto-dev/+archive/mosquitto-ppa/") to your repositories list

Can you post the output of

```
grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
```

It will show us all the repositories you have so we can check.

Kind regards

---

### Post by discosrule on 2015-06-05
Yep, using correct ppa I believe. 

```
 grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
/etc/apt/sources.list:9:deb http://au.archive.ubuntu.com/ubuntu/ precise main restricted
/etc/apt/sources.list:10:deb-src http://au.archive.ubuntu.com/ubuntu/ precise main restricted
/etc/apt/sources.list:14:deb http://au.archive.ubuntu.com/ubuntu/ precise-updates main restricted
/etc/apt/sources.list:15:deb-src http://au.archive.ubuntu.com/ubuntu/ precise-updates main restricted
/etc/apt/sources.list:20:deb http://au.archive.ubuntu.com/ubuntu/ precise universe
/etc/apt/sources.list:21:deb-src http://au.archive.ubuntu.com/ubuntu/ precise universe
/etc/apt/sources.list:22:deb http://au.archive.ubuntu.com/ubuntu/ precise-updates universe
/etc/apt/sources.list:23:deb-src http://au.archive.ubuntu.com/ubuntu/ precise-updates universe
/etc/apt/sources.list:30:deb http://au.archive.ubuntu.com/ubuntu/ precise multiverse
/etc/apt/sources.list:31:deb-src http://au.archive.ubuntu.com/ubuntu/ precise multiverse
/etc/apt/sources.list:32:deb http://au.archive.ubuntu.com/ubuntu/ precise-updates multiverse
/etc/apt/sources.list:33:deb-src http://au.archive.ubuntu.com/ubuntu/ precise-updates multiverse
/etc/apt/sources.list:40:deb http://au.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
/etc/apt/sources.list:41:deb-src http://au.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
/etc/apt/sources.list:43:deb http://security.ubuntu.com/ubuntu precise-security main restricted
/etc/apt/sources.list:44:deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
/etc/apt/sources.list:45:deb http://security.ubuntu.com/ubuntu precise-security universe
/etc/apt/sources.list:46:deb-src http://security.ubuntu.com/ubuntu precise-security universe
/etc/apt/sources.list:47:deb http://security.ubuntu.com/ubuntu precise-security multiverse
/etc/apt/sources.list:48:deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
/etc/apt/sources.list:63:deb http://nginx.org/packages/mainline/ubuntu/ precise nginx
/etc/apt/sources.list:64:deb-src http://nginx.org/packages/mainline/ubuntu/ precise nginx
/etc/apt/sources.list.d/mosquitto-dev-mosquitto-ppa-precise.list:1:deb http://ppa.launchpad.net/mosquitto-dev/mosquitto-ppa/ubuntu precise main
/etc/apt/sources.list.d/mosquitto-dev-mosquitto-ppa-precise.list:2:deb-src http://ppa.launchpad.net/mosquitto-dev/mosquitto-ppa/ubuntu precise main
```

---

### Post by matt_symes on 2015-06-05
Hi

That's the correct PPA alright.

> Haven't had a problem in the past doing it this way.

Have you installed it specifically on 12.04**.5** from the PPA before? 
On that specific hardware enablement stack ?
 Or on a previous hardware enablement stack ?

I'm trying to understand how you have installed it before.

Kind regards

---

### Post by discosrule on 2015-06-05
> **matt_symes said:**
> Hi

That's the correct PPA alright.



Have you installed it specifically on 12.04**.5** from the PPA before? 
On that specific hardware enablement stack ?
 Or on a previous hardware enablement stack ?

Kind regards

Not sure. Just haven't had any problems with Ubuntu and mosquitto in the past.

---

### Post by matt_symes on 2015-06-05
Hi

> **discosrule said:**
> Not sure. Just haven't had any problems with Ubuntu and mosquitto in the past.

Have you installed it on 12.04 before ?

Kind regards

---

### Post by discosrule on 2015-06-05
Gave up, just brought up another vm with 14.04 and it all works fine. Thx for the help guys.

---

### Post by matt_symes on 2015-06-06
Hi

I'm glad you got a fix even if we didn't get to the root cause of the problem.

14.04 is a better choice anyway and will be supported for much longer.

Kind regards

---

