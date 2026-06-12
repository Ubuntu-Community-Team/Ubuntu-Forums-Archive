---
title: "General Help Please!"
date: 2005-07-18
forum: Installation &amp; Upgrades
---

### Post by GregDonohoe on 2005-07-18
I recently installed Ubuntu from CD, and have found it fairly easy to use.

But I can't seem to install anything, rather than just downloading an install file for applications as I did in windows, every install document I look at requires me to type in commands to the terminal.

I don't mind learning to use this terminal, but could someone please provide me with or link me to a tutorial which will show me how to install a program (MPlayer would be nice)

Please note that I am very new to Ubuntu/Linux, so keep it simple please.

Thanks.

---

### Post by damonw5 on 2005-07-18
[QUOTE=GregDonohoe]I recently installed Ubuntu from CD, and have found it fairly easy to use.

But I can't seem to install anything, rather than just downloading an install file for applications as I did in windows, every install document I look at requires me to type in commands to the terminal.

I don't mind learning to use this terminal, but could someone please provide me with or link me to a tutorial which will show me how to install a program (MPlayer would be nice)

Please note that I am very new to Ubuntu/Linux, so keep it simple please.

Thanks.[/QUOTE]

The key to Ubuntu is that you don't generally download software off the internet and then install it. You get big lists of software in a program called synaptic that lets you search all the software programs. It then lets you install what you want right from the same program.


 First, follow these directions for adding "repositories" (groups of software options) to Ubuntu:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Then open Synaptic, the main program for installing software. Go to System->Administration->Synaptic Package Manager. Press "reload" to update the list of "packages" (individual pieces of software). Then you can search for and install mplayer!

To play some of your favorite files, you might need to also install "codecs" as described here: 
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

---

### Post by WildTangent on 2005-07-19
welcome to the linux way of doing things. dont let it frighten you, it wont bite ;) you need to shake this windows mentality off. youll find eventually that the command line is much easier to use. for example, if you go to [http://www.ubuntuguide.org](http://www.ubuntuguide.org), and just copy the commands, and then paste them in the terminal (by right clicking and selecting paste, ctrl+v doesnt work in the terminal) you can accomplish installtion much faster than just clicking next in a windows installer :P 

please, keep an open mind.

-Wild

---

### Post by bored2k on 2005-07-19
Here's a quick little dirty rundown:

After you succesfully do step 1. [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

To search for a package:
In your upper terminal, click on System - Administration - Synaptic package manager, there you can search for any given applications.

Now for the nice little terminal way of doing things:

Package search:
apt-cache search rhythmbox OR aptitude rhythmbox (or whatever you want to search - descriptions and/or names)

Package installment:
sudo apt-get install rhythmbox (or the package name)

Uninstall a  package:
sudo apt-get remove rhythmbox

Install a .deb package downloaded through the web:
sudo dpkg -i filename.deb
-If the package sprays errors about missing dependencies, type
sudo apt-get -f install

If it still does not install, at this point, leave it.

---

### Post by GregDonohoe on 2005-07-19
Thanks guys, but the links you have provided do not work, Mozilla just times out.
Wrong URL?

---

### Post by bored2k on 2005-07-19
[QUOTE=GregDonohoe]Thanks guys, but the links you have provided do not work, Mozilla just times out.
Wrong URL?[/QUOTE]
 [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) ?
It's very working.

---

### Post by GregDonohoe on 2005-07-19
OK, thanks, ubuntuguide still isn't working for me, but I managed to get Google's text only cache.
I managed to use Synaptic Package Manager to get MPlayer, unfortunately when I open a file in MPlayer it just shows a black screen and doesn't respond, so I'll just keep trying to fix this.

---

### Post by bored2k on 2005-07-19
[QUOTE=GregDonohoe]OK, thanks, ubuntuguide still isn't working for me, but I managed to get Google's text only cache.
I managed to use Synaptic Package Manager to get MPlayer, unfortunately when I open a file in MPlayer it just shows a black screen and doesn't respond, so I'll just keep trying to fix this.[/QUOTE]
 MPlayer has its own share of problems. After installing w32codecs, gxine, xine-ui and totem-xine become _very_ powerful. On the other hand, you can try my favorite, VLC (make sure you install vlc-esd then set vlc to use ESOUND as an audio output).

---

### Post by al7kz on 2005-07-19
Hi GregDonohue,

I found the following lines work better than the ones in the guide:

##############

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

 ## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse

##Backup Ubuntu Mirrors
deb [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) hoary-updates main restricted universe multiverse
deb-src [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) hoary-updates main restricted universe multiverse

##Security Mirrors
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe

##Backup Security Mirrors
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe

#Kubuntu KDE341 Updates - uncomment if you are using Kubuntu
#deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main

##Backports
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted

## Backports (Alternate Mirror)
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted 

###################

To use, backup your /etc/apt/sources.list by

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup

then replace the lines in /etc/apt/sources.list with the ones above.

Thanks bored2k, that's a great rundown on using apt.

Ciao, al7kz

---

### Post by al7kz on 2005-07-19
Oh, I forgot, after you replace the lines run

sudo apt-get update

---

### Post by damonw5 on 2005-07-19
[QUOTE=al7kz]Oh, I forgot, after you replace the lines run

sudo apt-get update[/QUOTE]
 ...or click "update" in Synaptic :)

---

### Post by GregDonohoe on 2005-07-24
Thanks for the help.
I managed to get flash running in Mozilla (albiet without sound), and MPlayer still doesn't work, and I always get this message when I open Synaptic Package Manager : 

*Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)*

Also, I originally installed the "Wart Warthog" release, will this be a problem?

---

### Post by bored2k on 2005-07-24
[QUOTE=GregDonohoe]Thanks for the help.
I managed to get flash running in Mozilla (albiet without sound), and MPlayer still doesn't work, and I always get this message when I open Synaptic Package Manager : 

*Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)*

Also, I originally installed the "Wart Warthog" release, will this be a problem?[/QUOTE]
 Warty is the old and first Ubuntu. If you used teh Hoary (latest) repositories on it, you _will_ get problems. As long as you stick with Warty's or just, upgrade the system, it won't be a problem.

---

### Post by al7kz on 2005-07-24
I don't know how to list a quote with the neat box around it so

"Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_bi nary-i386_Packages) - stat (2 No such file or directory)"

just delete this from sources.list:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

and add the entry from your sources.list-backup file for your install cd. It should be:

deb cdrom...blah........blah..................

---

