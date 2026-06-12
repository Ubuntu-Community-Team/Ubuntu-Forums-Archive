---
title: "how do I install software on live cd"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by nalinib on 2008-06-06
I have been running ubuntu 8.04 live cd.

I came across pendrivelinux.com and tried to install ubuntu on my usb stick (4 gb) using method described on the site.  But 5-6 attempts failed so I gave up.

Then I came across this site

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I downloaded the windows programme from the site and installed ubuntu on my 4 gb usb stick.  The installation was successful.

I thought I have got full installation.  But that is not the case.  What I got is "live usb stick" just like live cd.  This took just 715 mb of space.  So the remaining space is empty.

Then I tried to install the softwares from the live cd/usb stick using the synaptic package manager as described below.

I clicked "origin" tab in synaptic package manager.  I presume I got list of those softwares that are available on live cd.  I clicked one software and used menu command "mark for installation" and then "apply" command.

And now ubuntu tried to download the software from net and as pc was not connected to net the installation failed.

I noticed that some softwares have filled box before their names and some have empty boxes.  I tried to install both types of softwares but result the same "failure".  The filled box softwares have menu command "reinstall".

I guess the software installation is not possible because ubuntu is not fully installed on usb stick.

Am I right ?

Is it necessary to fully install ubuntu on hdd to install extra softwares from cd ?

Thanks

---

### Post by timcredible on 2008-06-06
yes, you have to install ubuntu to add extra software.  you can do that on a usb drive though.  4gb might be a very tight squeeze, but i think you can do it with that much storage.  follow the how-to on ubuntukids.org, i got it working easily on a 20gb usb-attached drive, would be same process for usb flashdrive.  i would make the swap space about 256mb in your case.

---

### Post by nalinib on 2008-06-08
Thanks Timcredible

Unfortunately ubuntukids.org o longer contains how-tos.

However I installed ubuntu on 4 gb flash drive but can't boot into it.

The error message received is "unable to mount partition"

I repartitioned the usb flash drive and again installed ubuntu on it but result is the same "unable to mount partition"

Then I istalld ubuntu on usb hdd (10 gb partition).  And it is working fine.

But using usb hdd is bit irritating as it needs seperate power supply.  I would have really loved using flash drive.  But it seems to be not possible.

I will use usb hdd for some days and then install ubuntu on internal hdd of my vista laptop (making it dual boot)

Thanks

---

