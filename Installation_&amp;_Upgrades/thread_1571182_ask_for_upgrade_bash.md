---
title: "ask for upgrade bash"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by zhengkarl on 2010-09-09
hi,everyone!
I use Ubuntu9.04,the bash in it is bash3.02;
I like the bash4.1 very much;but because I use Ubuntu for android develope,
Ubuntu10.1 is not the optimization version for it;
so I want upgrade bash only;but bash 4.1 can't been install by use "apt-get install bash" command.

Can anyone kindly told me how to install bash 4.1 by apt-get command? Thank you very much!

---

### Post by tyblogger5 on 2010-09-09
I'm not positive, but I think you can use:

**[COLOR="Red"]EDIT: Incorrect Command, see below[/COLOR]**

```
sudo apt-get update bash
```

---

### Post by slakkie on 2010-09-09
> **tyblogger5 said:**
> I'm not positive, but I think you can use:

```
sudo apt-get update bash
```

apt-get update will update the package list found on the server. It will never update/upgrade a package. Upgrading a package is the same as installing one, eg. apt-get install bash. Provided the package is found on a repository.

---

### Post by tyblogger5 on 2010-09-09
> **slakkie said:**
> apt-get update will update the package list found on the server. It will never update/upgrade a package. Upgrading a package is the same as installing one, eg. apt-get install bash. Provided the package is found on a repository.

I always forget that, I keep on thinking you can put update.  I guess the best thing to do is to upgrade the system?

```
sudo apt-get upgrade
```

---

### Post by slakkie on 2010-09-09
Mmmm, I backported bash4.1 from Lucid to Karmic, but that is 9.10 and you run Jaunty (9.04).. I'll see if backporting bash to jaunty works. For those who are interested, this is the PPA: [https://launchpad.net/~wesleys/+archive/ppa/+packages](https://launchpad.net/~wesleys/+archive/ppa/+packages)

---

### Post by zhengkarl on 2010-09-09
> **slakkie said:**
> Mmmm, I backported bash4.1 from Lucid to Karmic, but that is 9.10 and you run Jaunty (9.04).. I'll see if backporting bash to jaunty works. For those who are interested, this is the PPA: [https://launchpad.net/~wesleys/+archive/ppa/+packages](https://launchpad.net/~wesleys/+archive/ppa/+packages)
 
I'm newly to package manage. can you kindly told me how to use it?

---

### Post by tyblogger5 on 2010-09-09
Here is a good link for the Synaptic front-end for dpkg (the Ubuntu package manager)

[https://help.ubuntu.com/community/SynapticHowto]("https://help.ubuntu.com/community/SynapticHowto")

---

### Post by slakkie on 2010-09-09
Well, tbh, Jaunty becomes EOL after October 2010. So, if you upgrade to 9.10 Karmic you can make use of my PPA. 

Backporting bash 4.1 to jaunty is a little problematic, I think I need to backport multiple packages before it can work (xz-utils for example).  Since I'm a busy man atm, I don't think I will have enough time to do it. 

Upgrade to Karmic and you can make use of my PPA, add the following line to your sources.list:

```

sudo nano /etc/apt/sources.list

```

Add this at the bottom of the file:
```
deb http://ppa.launchpad.net/wesleys/ppa/ubuntu karmic main
```

Save/Exit the file.

MAke sure you don't upgrade any other package from a PPA:

```

sudo nano /etc/apt/preferences

```

```

Package: *
Pin: origin ppa.launchpad.net
Pin-Priority: 300

```

Save/Exit the file

```

aptitude update && aptitude install bash=4.1-2ubuntu3.1-wgs-bpo01

```

Done.

---

### Post by zhengkarl on 2010-09-10
> **slakkie said:**
> Well, tbh, Jaunty becomes EOL after October 2010. So, if you upgrade to 9.10 Karmic you can make use of my PPA. 

Backporting bash 4.1 to jaunty is a little problematic, I think I need to backport multiple packages before it can work (xz-utils for example).  Since I'm a busy man atm, I don't think I will have enough time to do it. 

Upgrade to Karmic and you can make use of my PPA, add the following line to your sources.list:

```

sudo nano /etc/apt/sources.list

```Add this at the bottom of the file:
```
deb http://ppa.launchpad.net/wesleys/ppa/ubuntu karmic main
```Save/Exit the file.

MAke sure you don't upgrade any other package from a PPA:

```

sudo nano /etc/apt/preferences

``````

Package: *
Pin: origin ppa.launchpad.net
Pin-Priority: 300

```Save/Exit the file

```

aptitude update && aptitude install bash=4.1-2ubuntu3.1-wgs-bpo01

```Done.

Thank you for your kind reply. 
I can't run "aptitude update" success.

It sasys, "GPG....error;... NO_PUBKEY D3980885DB72184B"

How can I resolve it?

---

### Post by slakkie on 2010-09-10
sudo apt-key adv --keyserver KEYSERVER --recv-keys D3980885DB72184B

replace KEYSERVER with keyserver.ubuntu.com or wwwkeys.eu.pgp.net

---

### Post by zhengkarl on 2010-09-11
> **slakkie said:**
> sudo apt-key adv --keyserver KEYSERVER --recv-keys D3980885DB72184B
 
replace KEYSERVER with keyserver.ubuntu.com or wwwkeys.eu.pgp.net
 
this step is done. but can't find the   "bash=4.1-2ubuntu3.1-wgs-bpo01" package.....

---

### Post by slakkie on 2010-09-12
> **zhengkarl said:**
> this step is done. but can't find the   "bash=4.1-2ubuntu3.1-wgs-bpo01" package.....

That package took over 2 days to build (it was rescheduled I suppose). See [https://launchpad.net/~wesleys/+archive/ppa/+builds?build_text=&build_state=all](https://launchpad.net/~wesleys/+archive/ppa/+builds?build_text=&build_state=all)

---

### Post by zhengkarl on 2010-09-12
> **slakkie said:**
> That package took over 2 days to build (it was rescheduled I suppose). See [https://launchpad.net/~wesleys/+archive/ppa/+builds?build_text=&build_state=all](https://launchpad.net/~wesleys/+archive/ppa/+builds?build_text=&build_state=all)
 
It seems  is current building...
When it would be ready? or can I use a minor one?-- I just want the menu-complete-backward function; I think it alse can be found in bash4.0...

---

### Post by wojox on 2010-09-12
> **zhengkarl said:**
> It seems  is current building...
When it would be ready? or can I use a minor one?-- I just want the menu-complete-backward function; I think it alse can be found in bash4.0...

Why don't you just upgrade to 10.04? That will give you GNU bash, version 4.1.5

---

### Post by slakkie on 2010-09-12
It keeps building and building. Mailed the launchpad people, but for now, you have to wait. Although I'm able to build it via pdebuilder on my own box.

---

### Post by zhengkarl on 2010-09-12
> **wojox said:**
> Why don't you just upgrade to 10.04? That will give you GNU bash, version 4.1.5

android compile tools is not running well on 10.04 ....

---

### Post by slakkie on 2010-09-13
Hi,

you can download the packages from:

[http://opperschaap.net/~wesleys/ubuntu/bash/](http://opperschaap.net/~wesleys/ubuntu/bash/)

Launchpad is having some troubles with the package, looking into it.

---

### Post by zhengkarl on 2010-09-14
> **slakkie said:**
> Hi,

you can download the packages from:

[http://opperschaap.net/~wesleys/ubuntu/bash/]("http://opperschaap.net/%7Ewesleys/ubuntu/bash/")

Launchpad is having some troubles with the package, looking into it.

Thank you very much!

I installed your package. and whatever command I type in bash shell, it have no prompt error.....

see the attached image for detail pls.

in the picture, Some charater prompt when use bash3.2 is Chinese, it says "can't find the command".....

---

### Post by zhengkarl on 2010-09-15
> **slakkie said:**
> Hi,

you can download the packages from:

[http://opperschaap.net/~wesleys/ubuntu/bash/]("http://opperschaap.net/%7Ewesleys/ubuntu/bash/")

Launchpad is having some troubles with the package, looking into it.

it seems strange... how can I enter debug mode?
set -v 
has no use...

---

### Post by zhengkarl on 2010-09-15
> **slakkie said:**
> Hi,

you can download the packages from:

[http://opperschaap.net/~wesleys/ubuntu/bash/]("http://opperschaap.net/%7Ewesleys/ubuntu/bash/")

Launchpad is having some troubles with the package, looking into it.

I have installed your package. and whatever command I type in bash shell, it have no prompt error.....

---

### Post by slakkie on 2010-09-15
I dunno, bash uses some command-not-found tool for commands it cannot find. Perhaps that requires backporting as well? I don't have a Karmic box, so cannot test it for you. Sorry!

A friend of mine with Karmic has tested the package (somewhat at least) and it works for him...

---

### Post by zhengkarl on 2010-09-21
hi,slakkie.
Now I have another the problem to ask for you:I want to upgrade the gimp from 2.6.8 to 2.6.10. but the package can't be found in the repository.
the official site:
[http://www.gimp.org/downloads/](http://www.gimp.org/downloads/)
only said:
Ubuntu or Debian users can simply run apt-get install gimp to get the latest stable release of GIMP.

so, how can I do to upgrade the gimp?

---

