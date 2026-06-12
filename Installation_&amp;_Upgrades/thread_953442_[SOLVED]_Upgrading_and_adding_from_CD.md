---
title: "[SOLVED] Upgrading and adding from CD"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by oygle on 2008-10-20
At present 2 computers, both with 8.04.1, one 32 bit, the other 64 bit.

I only have dilaup at present, so doing updates via the internet is out of the question. I have tried to at least update important security updates though.

On those 2 computers, I need to:

(a) Perform all the updates from CD
(b) Add various apps from CD (Openoffice, KMyMoney, Firefox, simple backup, etc,etc)

I do have the ISO on CD, for both the 32 bit and 64 bit, but many of the apps I want to install aren't even on those CD's.

Can someone please inform me if all the updates since 8.04.1 are availabel on CD, for 32 and 64 bit, and if there are CD's that contain ALL the current apps for Ubuntu 8.04.1, including all updates for those apps.

Then I would need to know how to install from CD please.

I have tried changing the 'sources' in admin just to install a small app called "setserial"  by doing

sudo apt-get install source=/media/cdrom0

but that didn't work, and eventually found a right click on the file setserial_2.17-44_i386.deb , and then open with 'GDebi package installer' and then install package seemed to go okay.

But what about dependencies ?

Would appreciate your help please.  :)

Oygle

---

### Post by oygle on 2008-10-20
Surely someone knows the answer to this, please ?

With dialup, I can't do updates any more. I can possibly go to an internet cafe, and download files to a USB stick, but which files ??

---

### Post by Partyboi2 on 2008-10-20
Give [[COLOR=Blue]Keryx[/COLOR]]("http://keryx.betaserver.org/") ago. Once you have downloaded it right click on it and extract it.. Then open up the keryx-0.12/doc/README file and read how to use it.

---

### Post by robert shearer on 2008-10-20
> **oygle said:**
> Surely someone knows the answer to this, please ?

With dialup, I can't do updates any more. I can possibly go to an internet cafe, and download files to a USB stick, but which files ??

The 'aptoncd' package allows you to download updates/apps to one machine, make a cd of them and take it to the machine that is not able to download them.(or at least not download quickly)

You either need to know someone running the same o/s with a fast connection and have them install aptoncd and make regular cds for you

 OR use update manager on your machine to CHECK for updates but not install them.

Then write down all the packages that it idenitfies and go to a machine with fast internet(library/internet cafe?) and download these from the Ubuntu packages site then take them to your pc and manually load them.

Same for apps but using synaptic and stopping short of installing then writing down packages etc etc.

The friend with the same o/s option would be way easier!!:)

aptoncd is in the repositories.Find it with Synaptic.

Let us know if you want more info:)

---

### Post by oygle on 2008-10-29
> **robert shearer said:**
> The 'aptoncd' package allows you to download updates/apps to one machine, make a cd of them and take it to the machine that is not able to download them.(or at least not download quickly)

You either need to know someone running the same o/s with a fast connection and have them install aptoncd and make regular cds for you


Have installed 'aptoncd' , but it only creates a CD/DVD or restores the package contents to cache. I also noticed that it only gets a list of the packages, and has left out the apps ?

> **robert shearer said:**
> 
 OR use update manager on your machine to CHECK for updates but not install them.

Then write down all the packages that it idenitfies and go to a machine with fast internet(library/internet cafe?) and download these from the Ubuntu packages site then take them to your pc and manually load them.

Same for apps but using synaptic and stopping short of installing then writing down packages etc etc.


What would be the command line/s to do this please ?

A friend told me to do the following ..

# apt-get update

# apt-get upgrade -V

but it only contained a list of package names. I would need to have a list of all the URL's where to download the latest updates, and then if I can put them on a USB stick (fast connection somewhere), then need to know how to install them from the USB stick please.

Also, I understand there is a new version of Ubuntu soon. if I got to a fast connection, then maybe I can d/load the new ISO. BUT, then how do I install/update from the ISO ?

Oygle

---

### Post by oygle on 2008-10-31
I will be able to grab 8.10 next week hopefully, on a computer with a fast internet connection.

AptonCD relies on both computers running Ubuntu, which was going to be difficult. Someone has kindly shown me a script to generate all the URL's, so the files (.DEB) can be downloaded offline somewhere, so that solves the dialup problem for now. The instructions for doing that are [at this thread]("http://ubuntuforums.org/showthread.php?t=963344")

For now, I'll consider this thread as 'solved', it seems just grabbing the .DEB files from another media, be it, USB or CD/DVD , will be do-able.

---

