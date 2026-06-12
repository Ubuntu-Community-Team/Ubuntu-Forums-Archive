---
title: "Upgrade from 13.10 to 14.04 today"
date: 2016-01-29
forum: Installation &amp; Upgrades
---

### Post by banzaay on 2016-01-29
Hi all,

i have an OLD laptop with Lubuntu 13.10, I followed this guide

[https://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release](https://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release)

to upgrade using the unsupported repositories.

Now I'm trying to Upgrade to 14.04 with the following commands

sudo do-release-upgrade

and

sudo do-release-upgrade -d

both commands give a message that No New Release is available.

Anyone Can help me ??

Thanks in advice
Mirko

---

### Post by QDR06VV9 on 2016-01-29
I just noticed this "[COLOR=#000000]sudo do-release-upgrade -d"
[/COLOR]The -d switch takes you to a development release as in Xenial(16.04) not good..
By the sounds of what your post reads nothing happened..and that is a Good thing here.
But to dist-upgrade to Trusty(14.04)
In the terminal run:
```
sudo sed -i 's/saucy/trusty/g' /etc/apt/sources.list

```

Which will change your repos from Saucy to Trusty..
And then run
```
sudo apt-get update

```
to update to the new repos
```
sudo apt-get dist-upgrade

```

to pull in the new changes..
```
sudo apt-get upgrade

```
to be sure everything is current.

*****WARNING*****
If you have any proprietary drivers installed you will need to uninstall those before doing the above . (Except Intel Video Drivers no worries here)
Hope that was helpfull
Regards

---

### Post by oldos2er on 2016-01-29
> **banzaay said:**
> sudo do-release-upgrade -d

Why would you want to upgrade to 16.04? That seems like a good way to break your system.

Can you post the contents of your sources.list? ```
cat /etc/apt/sources.list
```

---

### Post by grahammechanical on 2016-01-29
> sudo do-release-upgrade -d

both commands give a message that No New Release is available.

You may already be on the next development release (xenial xerus = 16.04). The switch -d = development release. To find out what version of Ubuntu you are now on,

```
lsb_release -a
```

If you see this
> 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Xenial Xerus (development branch)
Release:    16.04
Codename:    xenial

Then, update daily or weekly or fortnightly until the end of April then you will be using 16.04 LTS.

Regards

---

### Post by banzaay on 2016-02-01
Your solution works.

Thanks for your help.

---

### Post by vasa1 on 2016-02-01
> **banzaay said:**
> Hi all,

i have an OLD laptop with Lubuntu 13.10, I followed this guide

[https://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release](https://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release)

to upgrade using the unsupported repositories.

Now I'm trying to Upgrade to **_*14.04*_** ....
How did 16.04 get into the picture?

---

### Post by grahammechanical on 2016-02-01
> Your solution works.

I did not want to say it because 16.04 has not yet reached beta software stage and there are always concerns about the stability of development software but I have been using xenial xerus (16.04) for 12 weeks. It is very stable. I am sure that the system will be fine.

16.04 comes into it with "do-release-upgrade -d." The wiki page gives complete information but in some cases complete information is a little too much information.

Regards.

---

