---
title: "Ubuntu on MacBook Air 2013[6,1]"
date: 2014-01-20
forum: Installation &amp; Upgrades
---

### Post by asaddhamani on 2014-01-20
[COLOR=#333333][FONT=UbuntuRegular]I have a 2013 MacBook Air 11' with a Haswell i5 and I want to replace OS X on it with Ubuntu. I do not want to dual boot, as I only have a 128GB SSD. I've been waiting for a proper guide to do this for a long while now, as I cannot risk botching up this MacBook and losing access to it. I recently came across this guide : [http://www.sourceprojects.org/installing-ubuntu-13-10-on-a-macbook-air-6-2](http://www.sourceprojects.org/installing-ubuntu-13-10-on-a-macbook-air-6-2)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]However, from what I could tell, that guide is for dual booting with OS X, not something I want to do. I am using the specialized Mac 64bit ISO file for 13.10 from here :[http://ubuntu.excellmedia.net/releases/saucy/ubuntu-13.10-desktop-amd64+mac.iso](http://ubuntu.excellmedia.net/releases/saucy/ubuntu-13.10-desktop-amd64+mac.iso)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]But I'm not sure if after I am done installing Ubuntu on my MacBook, wireless, my webcam, audio, video, the trackpad, the keyboard backlight, sleep, all of that would work OOB.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Has anyone installed Ubuntu on their 2013 MacBook Air successfully? 13.10 specifically? Did the Mac ISO work out of the box with everything? Has anyone removed OS X completely from their MacBook?[/FONT][/COLOR]

---

### Post by k-neko on 2014-01-21
Hello Asaddhamani!
First of all, don't you care of 'botching up' your macbook. 
If you create yourself an appleid, you will be able to reinstall your OS without bootable media
Not sure if that could be done without iTunes account
If you will lose access to it, just press cmd-r while booting, and select disk utility, format your hdd, then exit to menu again and select install OS. (can confirm that this works even with zero'd drive of your machine)
That would request your password/login from apple store, and then that will download & re-install Mac OS version you had before. 

P.s.
I'd rather not use that "special iso" from unknown site, cause the only difference would be an out-of-box access to your wireless, which could be solved by just downloading drivers on secondary flash usb disk or so. 


P.s.s. 
When you'll do the installation, please share your experiences!

---

### Post by asaddhamani on 2014-01-22
> **k-neko said:**
> Hello Asaddhamani!
First of all, don't you care of 'botching up' your macbook. 
If you create yourself an appleid, you will be able to reinstall your OS without bootable media
Not sure if that could be done without iTunes account
If you will lose access to it, just press cmd-r while booting, and select disk utility, format your hdd, then exit to menu again and select install OS. (can confirm that this works even with zero'd drive of your machine)
That would request your password/login from apple store, and then that will download & re-install Mac OS version you had before. 

P.s.
I'd rather not use that "special iso" from unknown site, cause the only difference would be an out-of-box access to your wireless, which could be solved by just downloading drivers on secondary flash usb disk or so. 


P.s.s. 
When you'll do the installation, please share your experiences!

I'll be trying this soon, but I've decided to not completely get rid of Mac OS X, since I would be requiring it for presentations, as I don't think Ubuntu will support Thunderbolt. However, the Mac iso is not from an unknown site, as far as I can tell, its available in all Ubuntu ISO repos, like this one :[http://mirror.exetel.com.au/pub/ubuntu/ubuntu-releases/13.10/](http://mirror.exetel.com.au/pub/ubuntu/ubuntu-releases/13.10/)

And I found that ISO using Launchpad : [https://launchpad.net/ubuntu/+cdmirrors](https://launchpad.net/ubuntu/+cdmirrors)

I guess thats an official page.

---

