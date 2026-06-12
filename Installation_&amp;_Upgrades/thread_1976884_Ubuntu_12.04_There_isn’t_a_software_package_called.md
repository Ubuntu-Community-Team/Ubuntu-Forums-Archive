---
title: "Ubuntu 12.04 There isn’t a software package called “qgis” in your current software so"
date: 2012-05-09
forum: Installation &amp; Upgrades
---

### Post by baditaflorin on 2012-05-09
I don`t ask how i can install,  for sure that i will find on qgis.org a precompiled pack for ubuntu 11.10 and it will run, i hope. 

I ask what can i do to make the package exists for ubuntu 12.04 ? 

Where can i read more about the process of a package being introduced into Ubuntu Software Center, so that i find a broken or not compiled package, to know what to do :)

---

### Post by Daniel Wing on 2012-07-25
> **baditaflorin said:**
> I don`t ask how i can install,  for sure that i will find on qgis.org a precompiled pack for ubuntu 11.10 and it will run, i hope. 

I ask what can i do to make the package exists for ubuntu 12.04 ? 

Where can i read more about the process of a package being introduced into Ubuntu Software Center, so that i find a broken or not compiled package, to know what to do :)

Well I know you were very clear on what you're asking and what you're not, but in order to answer your question I may have to address both.

The QGIS repositorios are not included in the 12.04 versión of Ubuntu. Don't ask me why because I have no idea. But there is a way to add them and install QGIS. In regars of where to find info of software introduction to Ubuntu Software Center I'm not really helpfull.

This is how I installed QGIS step by step. Here you will find how to make it available for yourself. I'm trying to keep this as easier  as possible for newbies so you might gonna find many annoying comments  or lines that could sound obvious for some expertise levels.

All keys and repositories are the QGIS official ones. You can corroborate here: [http://hub.qgis.org/projects/quantum...ownload#Master]("http://hub.qgis.org/projects/quantum-gis/wiki/Download#Master")

1. Open "Synaptic Package manager" or "Ubuntu Software Center" and add the repositories as follows:

In "Synaptic Package manager" the path is: Settings-Repositories-Other Software-Add.
In "Ubuntu Software Center" the path is: Edit-Software sources-Other Software-Add.

Once there, enter each one of the lines below at a time.

deb [http://qgis.org/ubuntugis-nightly](http://qgis.org/ubuntugis-nightly) precise main
deb-src [http://qgis.org/ubuntugis-nightly](http://qgis.org/ubuntugis-nightly) precise main
deb [http://ppa.launchpad.net/ubuntugis/u...nstable/ubuntu]("http://ppa.launchpad.net/ubuntugis/ubuntugis-unstable/ubuntu") precise main

2. Now we need to add the public keys of QGIS as follow:

Open a terminal and type:

gpg --keyserver keyserver.ubuntu.com --recv 1F9ADD375CA44993 089EBE08314DF160
Hit enter or return (wherever you call it, for me is the same). It may  ask for your password, just type it in and hit enter again. Now add the  next line.
gpg --export --armor 1F9ADD375CA44993 089EBE08314DF160 | sudo apt-key add -
Once again hit enter. Now type:
sudo get-apt update
Hit enter for the last time and close the terminal.

Now go the Ubuntu Software center or Synaptic Package Manager and  install as usual. I would recomend to use Synaptic since it has been  more realiable in my experience. Not only for QGIS but any software  related issue.

Notes:

A) By doing it this way you will use the nightly build but you can as well use the regular package. The repositories would be:

deb     [http://qgis.org/debian](http://qgis.org/debian) precise main
deb-src [http://qgis.org/debian](http://qgis.org/debian) precise main 

B) This is for the Precise distro. If you're running a differente one, just check the web page for the right repositorie (or just change "Precise" for whatever you distro is).

Regards.

---

### Post by roneyrod on 2012-10-04
Dear Daniel,

Thanks for your suggestions.

I followed all the steps (except that I entered the repositories from Note A instead of the ones listed in Step 1) but things didn't work as expected.  When I typed sudo get-apt update I got a message "sudo: get-apt: command not found".

I tried to reload (which could another way to do the "update") Synaptic but it gave the following error message: W: GPG error: [http://qgis.org](http://qgis.org) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EBB1B7ED997D3880

Do you have any idea why I couldn't finish the installation?  Did I do something wrong?

Thanks in advance for your (or anyone else's) attention.
[]("http://ubuntuforums.org/member.php?u=1712625")

---

### Post by oldos2er on 2012-10-04
The correct command is **apt-get**, not the other way round.

You can install the public key with ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EBB1B7ED997D3880
```

---

### Post by Daniel Wing on 2012-10-09
> **roneyrod said:**
> Dear Daniel,

Thanks for your suggestions.

I followed all the steps (except that I entered the repositories from Note A instead of the ones listed in Step 1) but things didn't work as expected.  When I typed sudo get-apt update I got a message "sudo: get-apt: command not found".

I tried to reload (which could another way to do the "update") Synaptic but it gave the following error message: W: GPG error: [http://qgis.org](http://qgis.org) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EBB1B7ED997D3880

Do you have any idea why I couldn't finish the installation?  Did I do something wrong?

Thanks in advance for your (or anyone else's) attention.


Well oldos2er already answer but in the QGIS web page you can find any aditional info. Regarding the key error just do what oldos2r suggested or type the following sentences on terminal to add the qgis repository public key to your at keyring:



   gpg --keyserver keyserver.ubuntu.com --recv 997D3880
gpg --export --armor 997D3880 | sudo apt-key add 

It shuld be working just fine. If something comes up I'll try to reply faster.

---

