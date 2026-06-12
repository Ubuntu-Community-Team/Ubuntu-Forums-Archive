---
title: "Can't wireless, can I download drivers from a different computer?"
date: 2014-12-01
forum: Installation &amp; Upgrades
---

### Post by RabbitWho on 2014-12-01
Oh hi

I am guessing from reading this thread: [http://ubuntuforums.org/showthread.php?t=2188265](http://ubuntuforums.org/showthread.php?t=2188265) That **I need a drive**r. Also i seem to be getting some kind of a message on start up saying i need drivers and to go to a website,  but it starts up so quickly I don't have time to read what it says. 

**I don't** **have an ethernet cable.** We have a wireless router. I  have no way of borrowing someone else's internet or anything. Telling me to buy a cable, as 3 people have, is not helpful because it is not possible. 

**Is it possible to download the drivers I need from a different computer and install them using a USB? **
I've a dell inspiron 1545

If not I guess I'll have to make a bootable ubuntu usb and replace lubuntu with that, then install lubuntu over it. Internet always worked with Ubuntu.

Thanks for any help you can give.


Edit: more info.
following instructions from here: [http://ubuntuforums.org/showthread.php?t=1061710](http://ubuntuforums.org/showthread.php?t=1061710)

**my network controller **(hand typed, hopefully no herrors) **is**: 
Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

---

### Post by RabbitWho on 2014-12-01
I think I'm a little closer with the help of someone on IRC.. I'm still lost though. 

<c> you'll need an ubuntu usb or iso 
<c> \
<c> ok --- you have 14.04 right?
<n> yeah, lubuntu, the most recent LTS
<n> if that's 14.4
<c> nice.   OK , you need 2 .debs; dkms and bcmwl-kernel


<c> sudo dpkg -i these two packages in sequence;
<c> /etc/pool/main/d/dkms/dkmsFOO         etc/pool/restricted/b/bcmwl/bcmwl-kernel-sourceFOO
<c> as the bcmwl package processes, you should see your wifi light up - no reboot required.


<n> hmm. it says there's "no such file or directory" for the first one
[...]


<n> dkms.deb and bcmwl-kernel.deb... i have to download them and then.. where do I put them? sorry, I should have warned you I'm a total noob
<c> I gave you a bad address: no /etc
<c> open your usb; /pool/ etc etc etcc
<n> i can't get the packages to install
<c> sudo dpkg -i foo.deb           should do it.
<n> i'm not sure i am saving them right
<c>  saving them?  I NEVER said anything about saving them!
<n> but how do i get them to the USB then?
<c> those files are on your ubuntu USB --- which I thought you said you had.
<n> you're sure they're already on it?

<c> and what version of ubuntu is on the usb?
<n> lubuntu 14.04
<c> they are not on the lubuntu iso --- wait 1
<c> open this link and save:   [http://archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3.orig.tar.gz)
<c> and this one:  [http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl_6.30.223.141+bdcom.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl_6.30.223.141+bdcom.orig.tar.gz)


<c>** then boot ubuntu.  extract those two package in your file manager and dpkg them **
<c> get the files.  install the files.  use wifi

File manager? Where in the file manager?


Edit:

I got both these as debs, but both of them say i am missing dependencies, and i don't know what dependencies. 

It  says to run apt-get install -f..

ran that, now it is telling me what dependencies i need.. trying to find them.. gcc is the first one

edit:

downloaded gcc, but it said "dependency is not satisfiable" needed gcc base, got that.. it says i need something else, got that, which said i need something else.. is there anyway to get all the packages related to gcc in one go? all the packages related to the other things i need, in one go?

---

### Post by RabbitWho on 2014-12-01
Got it working thanks to this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Switching_between_drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Switching_between_drivers) 

Thank you to everyone on IRC who tried to help, and Unit193, who finally managed to. 

Also, to everyone who was sarcastic and nasty and mean to me, i hope you get fleas. 

I think i'll stick to the forums next time, even if it takes much longer to get a response, at least you know the mods will stop people from flaming you.

---

