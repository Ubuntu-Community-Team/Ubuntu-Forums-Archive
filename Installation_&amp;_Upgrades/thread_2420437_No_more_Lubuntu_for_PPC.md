---
title: "No more Lubuntu for PPC?"
date: 2019-06-05
forum: Installation &amp; Upgrades
---

### Post by kagelaris on 2019-06-05
Hi everybody,

I am relatively new to ubuntu community, so please forgive me for any mistakes.
I have an old machine, a powerbook, having a G4 processor. This is what is called (I suppose) PPC.
This little machine was long disabled, as the latest official release from it's vendor was looong time End of Life.
About one year ago, I discovered Lubuntu. I managed to install version 16.04 LTS. I worked PERFECTLY, and really made this old machine work fine.
HOWEVER, I recently was informed that 16.04 LTS reached EOL on 04/2019 for Lubuntu.
I made a small research, and found out that 16.04 LTS is the LAST Lubuntu version that supports PPC architecture.
So....16.04 LTS is no longer supported, and no other (later) version supports PPC architecture. 
Am I correct (hope not). Does this mean no more Lubuntu for this machine.
If this is the case, does anyone know if I have an alternative?

Thank you in advance,

---

### Post by crip720 on 2019-06-05
This link is old but some suggestions might still work.  [https://superuser.com/questions/250584/what-linux-distro-should-i-install-on-an-old-powerpc-mac](https://superuser.com/questions/250584/what-linux-distro-should-i-install-on-an-old-powerpc-mac) .  EOL means that you will no longer get updates for it,  it will still work, but if there are any new found security issues they won't be fixed for you.  Should be a few alternatives but will require more searching.

---

### Post by Bashing-om on 2019-06-05
kagelaris - NOoooo :)

Release 16.04 is (L)ong (T)erm (S)upport, The kernel will be supported until 2021 ( 5 years from 2016), while the desktop ( non critical) does loose the community support it has enjoyed. The community moves on to support the 2 other current releases ( and develop 19.10) as there  is not the manpower to cover all for the 5 year support term.

Not having community updates has little effect on what is maintained in "main". If there is a serious security issue it is covered.
You do have some breathing room for that old hardware -

See the output from terminal command:
```

ubuntu-support-status

```
As confirmation of what I say :)
[INDENT][INDENT]Just keep on keeping on
[/INDENT][/INDENT]

---

### Post by crip720 on 2019-06-05
Thanks for explaining and fixing my answer.

---

### Post by Bashing-om on 2019-06-05
crip720; Hey :)

> **crip720 said:**
> Thanks for explaining and fixing my answer.

We are all in this together - but 
strive for excellence

---

### Post by kagelaris on 2019-06-07
That was exactly my next quistion- if ubuntu updates apply also to me.
So, just to be sure, this is the output of the command:

andreas@PowerBook:~$  ubuntu-support-status
Support status summary of 'PowerBook':


You have 0 packages (0.0%) that can not/no-longer be downloaded
You have 1306 packages (100.0%) that are unsupported

Run with --show-unsupported, --show-supported or --show-all to see more details
andreas@PowerBook:~$ 


so....am I ok?

thank you


> **Bashing-om said:**
> kagelaris - NOoooo :)

Release 16.04 is (L)ong (T)erm (S)upport, The kernel will be supported until 2021 ( 5 years from 2016), while the desktop ( non critical) does loose the community support it has enjoyed. The community moves on to support the 2 other current releases ( and develop 19.10) as there  is not the manpower to cover all for the 5 year support term.

Not having community updates has little effect on what is maintained in "main". If there is a serious security issue it is covered.
You do have some breathing room for that old hardware -

See the output from terminal command:
```

ubuntu-support-status

```
As confirmation of what I say :)[INDENT][INDENT]Just keep on keeping on
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2019-06-07
kagelaris; Ouch !

Nope - thus far does not compute:
> 
You have 0 packages (0.0%) that can not/no-longer be downloaded
You have 1306 packages (100.0%) that are unsupported


post back:
```

uname -r
lsb_release -a
cat /etc/*-release
echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP
sudo apt update

```

And we see what we can finger out-

---

### Post by kagelaris on 2019-06-09
ok

andreas@PowerBook:~$ uname -r
4.4.0-150-powerpc-smp

andreas@PowerBook:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.6 LTS
Release:    16.04
Codename:    xenial

andreas@PowerBook:~$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.6 LTS"
NAME="Ubuntu"
VERSION="16.04.6 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04.6 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
VERSION_CODENAME=xenial
UBUNTU_CODENAME=xenial
andreas@PowerBook:~$ 

andreas@PowerBook:~$ echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP
Lubuntu   LXDE

andreas@PowerBook:~$  sudo apt update
[sudo] password for andreas: 
Hit:1 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial InRelease
Hit:2 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-security InRelease
Hit:3 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates InRelease
Reading package lists... Done                     
Building dependency tree       
Reading state information... Done
All packages are up to date.
andreas@PowerBook:~$ 

That's all
really really thank you all
:)




> **Bashing-om said:**
> kagelaris; Ouch !

Nope - thus far does not compute:


post back:
```

uname -r
lsb_release -a
cat /etc/*-release
echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP
sudo apt update

```

And we see what we can finger out-

---

### Post by Bashing-om on 2019-06-10
kagelaris ; Hummm ..

After much thought - I can not explain why there shows 100% packages that can not be upgraded,
Tell you what - I do have a 16.04 (x)ubuntu install. later I will boot to it and see what my package status results show there.

gots to be a reason-

---

### Post by Bashing-om on 2019-06-10
kagelaris; Ok -
My results:
```

sysop@x1604:~/Desktop$ ubuntu-support-status
Support status summary of 'x1604':

You have 1328 packages (84.3%) supported until April 2021 (Canonical - 5y)
You have 46 packages (2.9%) supported until April 2021 (Community - 5y)

You have 0 packages (0.0%) that can not/no-longer be downloaded
You have 201 packages (12.8%) that are unsupported

Run with --show-unsupported, --show-supported or --show-all to see more details
sysop@x1604:~/Desktop$

```

which in my mind point to your status hosed up somewhere. I have never encountered such before, and honestly I have no clue to a path of a possible  solution.

I am open to learning.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by kagelaris on 2019-06-11
oooooooooooook,

so ....now what?
Note: Today, I got a message from "Software Updater".
So, I suppose I receive some updates.

the output of sudo apt update is:

andreas@PowerBook:~$ sudo apt update
[sudo] password for andreas: 
Sorry, try again.
[sudo] password for andreas: 
Hit:1 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial InRelease
Get:2 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-security InRelease [109 kB]
Get:3 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates InRelease [109 kB]
Get:4 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main powerpc Packages [729 kB]                                    
Get:5 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/universe powerpc Packages [623 kB]                                
Fetched 1570 kB in 20s (77,3 kB/s)                                                                                          
Reading package lists... Done
Building dependency tree       
Reading state information... Done
7 packages can be upgraded. Run 'apt list --upgradable' to see them.
andreas@PowerBook:~$ apt list --upgradable
Listing... Done
libcups2/xenial-updates 2.1.3-4ubuntu0.9 powerpc [upgradable from: 2.1.3-4ubuntu0.8]
libcupsimage2/xenial-updates 2.1.3-4ubuntu0.9 powerpc [upgradable from: 2.1.3-4ubuntu0.8]
libelf1/xenial-security,xenial-updates 0.165-3ubuntu1.2 powerpc [upgradable from: 0.165-3ubuntu1.1]
libglib2.0-0/xenial-security,xenial-updates 2.48.2-0ubuntu4.2 powerpc [upgradable from: 2.48.2-0ubuntu4.1]
libglib2.0-bin/xenial-security,xenial-updates 2.48.2-0ubuntu4.2 powerpc [upgradable from: 2.48.2-0ubuntu4.1]
libglib2.0-data/xenial-security,xenial-updates 2.48.2-0ubuntu4.2 all [upgradable from: 2.48.2-0ubuntu4.1]
libsndfile1/xenial-security,xenial-updates 1.0.25-10ubuntu0.16.04.2 powerpc [upgradable from: 1.0.25-10ubuntu0.16.04.1]
andreas@PowerBook:~$ 


so......?????

---

### Post by oldrocker99 on 2019-06-11
There are other lightweight desktops which will not be nearing EOL.

    Mate Desktop.
    Budgie Desktop.
    Xfce Desktop.
    Xubuntu Desktop.
    
Any of these are nice and lightweight, and will be around for a while. I personally love Ubuntu MATE, which uses less than 500MB at bootup.

---

### Post by Impavidus on 2019-06-11
My guess (but not much more than a guess): The PPC build of the packages has different support than the amd64 build. Maybe the PPC build is only part of Lubuntu and has 3 years of support, even for the packages that are in common with Ubuntu and get 5 years of support for the amd64 build. Which opens up another can of worms for the architecture-independent packages, but I saw from your apt update output that it uses a separate set of repositories.

It appears that unsupported doesn't mean it's guaranteed to get no updates, but I wouldn't assume you get all updates for packages still supported on Ubuntu 16.04 LTS amd64.

---

### Post by kagelaris on 2019-06-12
I am not really interested in LXDE support. I am mostly concerned about security updates (which if I understood correct are from ubuntu?)
So, I am sorry but this is not clear to me. Do I have the ubuntu support? (I cannot understand)

thank you

---

