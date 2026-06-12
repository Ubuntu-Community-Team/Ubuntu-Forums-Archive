---
title: "DO NOT upgrade plymouth yet.."
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Vanishing on 2010-03-12
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538292](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538292)

unfortunately i did...and before rebooting, got alerted by AlanBell in irc..
thanks..lol

edit:
if you did...like me, don't reboot yet.."an upload of plymouth to add Breaks is already in the queue - but couldn't be built at once due to build-depends issues" - quote from Scott James Remnant

---

### Post by shafin on 2010-03-12
Thanks for the heads up. What's the version of plymouth thats having these problems? My current version is 0.8.0-~12. Should I check for updates or wait out a day or two?

---

### Post by brucemartin on 2010-03-12
i just did an upgrade and after restart i get a black screen, nothing more. anything i could do?

---

### Post by Dr. Dexter on 2010-03-12
hi bruce,

if it is possible for you start your machine with a live-cd.

then link:

```
sudo ln -s /lib/libply-boot-client.so.2.0.0 /lib/libplybootclient.so.2
```

now, you should be able to boot again.

Continue with removing the link and getting the new upgrade (apt) for mountall and gdm.

---

### Post by ankspo71 on 2010-03-12
I can see the update after running an update check

packages:
libplymouth2  from 0.8.0~-12 to 0.8.0~-13
plymouth  from 0.8.0~-12 to 0.8.0~-13
plymouth-x11  from 0.8.0~-12 to 0.8.0~-13
(these were marked as available to download)

What's missing? 
Thanks for the warning! I think I'll wait a few days.

---

### Post by Vanishing on 2010-03-12
> **shafin said:**
> Thanks for the heads up. What's the version of plymouth thats having these problems? My current version is 0.8.0-~12. Should I check for updates or wait out a day or two?

"not really fixed until -14 has hit the archive" - quote from Steve Langasek..
so..

---

### Post by ankspo71 on 2010-03-12
ahh, okay,  thanks :D

---

### Post by k3lt01 on 2010-03-12
It must be my lucky day, I updated this morning and for the first time Plymouth is working as it should, go figure huh.

---

### Post by Vanishing on 2010-03-12
I think its safe to upgrade now..

---

### Post by MacUntu on 2010-03-12
Damn, I missed it. Or can I still get the breakage feeling (even if this isn't something too tragic).

---

### Post by yoasif on 2010-03-12
Hilarious, first really annoying bug this cycle.

---

### Post by MacUntu on 2010-03-12
And it stayed way too short (read: it's kinda fixed now). :D

In addition I now know what was meant by: [http://twitter.com/keybuk/status/10284098563](http://twitter.com/keybuk/status/10284098563)

Urgs.

---

### Post by keybuk on 2010-03-12
Sorry about that "minor" bump, folks.

As regular followers may know, we're starting to have a few issues due to the complicated intertwining dependencies of our core system where things have to be built in a certain order.

In this case, the problem was we had to build the new plymouth (with the new library name) to build the new mountall.  But needed the new mountall to build plymouth with the right "Breaks" fields.

This is because building plymouth directly would have resulted in the buildds committing suicide part way through.  This happened to us about this point in the cycle last release, we at least avoided that this time.

The problem is that it meant for a short period, there was a pair of plymouth and mountall packages in the archive that did not work together.

If you see an upgrade to *both* (mountall should be 2.8, plymouth should be 0.8.0~-13 or -14) then you're good to go with the upgrade.

---

### Post by executorvs on 2010-03-12
if you already updated how might you get booting again. the method mentioned above was a no go for me.

---

### Post by keybuk on 2010-03-12
> **executorvs said:**
> if you already updated how might you get booting again. the method mentioned above was a no go for me.

Copying one name to the other should be enough I think; only the name changed, not the contents.

make /lib/libplybootclient.so.2 a symlink to or copy of /lib/libply-boot-client.so.2

---

### Post by Vanishing on 2010-03-12
> **executorvs said:**
> if you already updated how might you get booting again. the method mentioned above was a no go for me.

read this page..
[http://ubuntuforums.org/showthread.php?t=1428365&page=2](http://ubuntuforums.org/showthread.php?t=1428365&page=2)

---

### Post by Vanishing on 2010-03-12
> **keybuk said:**
> Copying one name to the other should be enough I think; only the name changed, not the contents.

make /lib/libplybootclient.so.2 a symlink to or copy of /lib/libply-boot-client.so.2

lol..im following you on twitter from now on

---

### Post by executorvs on 2010-03-12
> **Dr. Dexter said:**
> hi bruce,

if it is possible for you start your machine with a live-cd.

then link:

```
sudo ln -s /lib/libply-boot-client.so.2.0.0 /lib/libplybootclient.so.2
```

now, you should be able to boot again.

Continue with removing the link and getting the new upgrade (apt) for mountall and gdm.

this did not work for me :-( any other ideas?? I can reinstall if I have to but with my live disc being over a week old that's a lot of updates to get going quickly :-( not the quickest connection here..

---

### Post by Vanishing on 2010-03-12
> **executorvs said:**
> this did not work for me :-( any other ideas?? I can reinstall if I have to but with my live disc being over a week old that's a lot of updates to get going quickly :-( not the quickest connection here..

i replied to you above..

---

### Post by ElSlunko on 2010-03-12
> **executorvs said:**
> this did not work for me :-( any other ideas?? I can reinstall if I have to but with my live disc being over a week old that's a lot of updates to get going quickly :-( not the quickest connection here..

try this :

[http://ubuntuforums.org/showpost.php?p=8957706&postcount=19](http://ubuntuforums.org/showpost.php?p=8957706&postcount=19)

---

### Post by tekstr1der on 2010-03-12
> **k3lt01 said:**
> It must be my lucky day, I updated this morning and for the first time Plymouth is working as it should, go figure huh.

Haha. I've been among the lucky few for whom plymouth has been displaying nicely ever since around alpha 3. As of now, with new mountall and plymouth just black screen at boot and/or dumps me to tty1. My luck has run out.

---

### Post by shafin on 2010-03-12
[https://launchpad.net/ubuntu/+source/plymouth/0.8.0~-14]("https://launchpad.net/ubuntu/+source/plymouth/0.8.0%7E-14")

Right now, i386 build is ready there, if you've resisted rebooting up to now, you can grab the package from here, install and reboot:
[https://launchpad.net/ubuntu/+source/plymouth/0.8.0~-14/+build/1559374]("https://launchpad.net/ubuntu/+source/plymouth/0.8.0%7E-14/+build/1559374")

x64 is still building.

BTW, this is an interesting page, it shows all the builder pc's on launchpad, and true to ubuntu fashion, they all have funky names:
[https://launchpad.net/builders](https://launchpad.net/builders)

---

### Post by executorvs on 2010-03-12
> **Vanishing said:**
> read this page..
[http://ubuntuforums.org/showthread.php?t=1428365&page=2](http://ubuntuforums.org/showthread.php?t=1428365&page=2)

this worked. thank you.

---

### Post by jfernyhough on 2010-03-12
For stuff like this:
[http://identi.ca/ubuntustatus](http://identi.ca/ubuntustatus)

I think there's a Twitter one too.

---

### Post by sports fan Matt on 2010-03-12
I'm gonna wait a bit because i'm not exactly sure how to install it by tar.gz

---

### Post by Owen.C93 on 2010-03-12
I just updated mine fine just now. Although I'm not sure how to restore the splash screen.

---

### Post by sports fan Matt on 2010-03-12
I'm gonna hold off until i hear a defniate yes from anyone who has intel drivers..the upgrade is available though

---

### Post by sports fan Matt on 2010-03-12
Changes for the versions:
0.8.0~-12
0.8.0~-13

The list of changes is not available yet.

Since it's not .14 I'll wait.

---

### Post by sparker256 on 2010-03-12
> **sox fan Matt said:**
> Changes for the versions:
0.8.0~-12
0.8.0~-13

The list of changes is not available yet.

Since it's not .14 I'll wait.

from [http://identi.ca/ubuntustatus](http://identi.ca/ubuntustatus)

Don't reboot with libplymouth2 0.8.0~-13 without mountall 2.8!

I am good to go now.

Bill

---

### Post by VMC on 2010-03-12
> **tekstr1der said:**
> Haha. I've been among the lucky few for whom plymouth has been displaying nicely ever since around alpha 3. As of now, with new mountall and plymouth just black screen at boot and/or dumps me to tty1. My luck has run out.

Same with me. But is I remove splash from boot string then I get booted ok. Otherwise I get dumped to vtty. Once in a while I boot ok leaving splash in, but when I see the ubuntu logo flash then it dumps me to vtty. I just updated to the lastest. So something else is the matter:

```
$ aptitude show plymouth
Package: **plymouth**
State: installed
Automatically installed: no
**Version: 0.8.0~-13**

...
$ aptitude show mountall
Package: **mountall**
State: installed
Automatically installed: no
**Version: 2.8**
...

```

Ah, does that mean I need ~14 for plymouth to work correctly?

---

### Post by sports fan Matt on 2010-03-12
I beleive I have mountall 2.8

Changes for the versions:
2.7
2.8

The list of changes is not available yet.

Please use [http://launchpad.net/ubuntu/+source/mountall/2.8/+changelog](http://launchpad.net/ubuntu/+source/mountall/2.8/+changelog)
until the changes become available or try again later.

---

### Post by sparker256 on 2010-03-12
> **sox fan Matt said:**
> I beleive I have mountall 2.8

Changes for the versions:
2.7
2.8

The list of changes is not available yet.

Please use [http://launchpad.net/ubuntu/+source/mountall/2.8/+changelog](http://launchpad.net/ubuntu/+source/mountall/2.8/+changelog)
until the changes become available or try again later.

```

bill@game-1004:~$ mountall --version
mountall 2.8
Copyright (C) 2010 Canonical Ltd.

This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

Bill

---

### Post by garvinrick4 on 2010-03-12
Did not upgrade today but had to try. #4 in this post reconciled after failed boot. Have yet to ever boot with plymouth installed. Been a good Alpha stage for me first time would not boot after update && upgrade. Still do not have latest version mountall and my mirror says
up to date. Must not be quite as up to date as it says. Anyway had to break and fix to feel good today. Getting sicker by the day with bug testing. Should be listed as a desease so could go to 10 step program on insurance pocketbook.

---

### Post by sports fan Matt on 2010-03-12
I grabbed the deb.   mountall --version
mountall 2.8

---

### Post by tekstr1der on 2010-03-12
> **VMC said:**
> Same with me. But is I remove splash from boot string then I get booted ok. Otherwise I get dumped to vtty. Once in a while I boot ok leaving splash in, but when I see the ubuntu logo flash then it dumps me to vtty. I just updated to the lastest. So something else is the matter:

```
$ aptitude show plymouth
Package: **plymouth**
State: installed
Automatically installed: no
**Version: 0.8.0~-13**

...
$ aptitude show mountall
Package: **mountall**
State: installed
Automatically installed: no
**Version: 2.8**
...

```

Ah, does that mean I need ~14 for plymouth to work correctly?

I'm in the same boat as you, but I believe the ~14 version is only to prevent breakage if you have the older mountall.

```
plymouth (0.8.0~-14) lucid; urgency=low

  * Add Breaks: against old versions of mountall and casper, due to the soname
    changes in ~-13.

```

AFAICT, this great new update broke our otherwise functioning plymouth with splash boot. I'm going to wait for things to settle before I start submitting bugs. Oh yeah, I have to because apport's busted:
[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/538097](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/538097)

---

### Post by autocrosser on 2010-03-12
I just downloaded the -14, updated mountall (reinstalled to be sure) & rebooted---all went smooth here & for the first time Plymouth worked as it should on my system......

---

### Post by VMC on 2010-03-12
> **tekstr1der said:**
> I'm in the same boat as you, but I believe the ~14 version is only to prevent breakage if you have the older mountall.

```
plymouth (0.8.0~-14) lucid; urgency=low

  * Add Breaks: against old versions of mountall and casper, due to the soname
    changes in ~-13.

```

AFAICT, this great new update broke our otherwise functioning plymouth with splash boot. I'm going to wait for things to settle before I start submitting bugs. Oh yeah, I have to because apport's busted:
[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/538097](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/538097)
Yes, I was looking at launchpad to decide if any bugs fit our criteria, but none did. 

I also found that I'm dropped to VTTY1, but the boot up was taking place at VTTY7, unbenounced to me. 
So I did a Alt+F7 I was presented with a desktop. Weird.

@tekstr1der, Once you get to the login at VTTY1, try VTTY7 and see if you too have a completed desktop.

---

### Post by tekstr1der on 2010-03-12
> **VMC said:**
> @tekstr1der, Once you get to the login at VTTY1, try VTTY7 and see if you too have a completed desktop.

Oh, sorry, I should have mentioned that! It was the first thing I tried after saying, "WTF am I doing in tty1?"

---

### Post by kyleabaker on 2010-03-12
> **autocrosser said:**
> I just downloaded the -14, updated mountall (reinstalled to be sure) & rebooted---all went smooth here & for the first time Plymouth worked as it should on my system......
I just updated to both as well. I'm hoping I finally get the same results that you did.

---

### Post by keybuk on 2010-03-12
> **VMC said:**
> Same with me. But is I remove splash from boot string then I get booted ok. Otherwise I get dumped to vtty. Once in a while I boot ok leaving splash in, but when I see the ubuntu logo flash then it dumps me to vtty. I just updated to the lastest.

Do you see a graphical splash screen followed by the boring text "login:" screen?

---

### Post by keybuk on 2010-03-12
> **VMC said:**
> Yes, I was looking at launchpad to decide if any bugs fit our criteria, but none did.

"Booting with the framebuffer renderer leaves the system at textual "login:" screen" ?  

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538214](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538214)

(which is mentioned in the changelog specifically)

---

### Post by VMC on 2010-03-12
> **keybuk said:**
> Do you see a graphical splash screen followed by the boring text "login:" screen?

What I see when I'm dropped to VTTY1 is a quick flash of the ubuntu logo and then the login screen.

What clued me into trying VTTY7, was when I issued 'startx' it said its already running.

So Alt+F7 brought me to my already booted desktop.

BTW- I remember Steve Langasek mentioning in a previous bug I had about GDM and plymouth were "fighting" for which one got which VTTY.
 Especially if I removed splash from the boot string. 
If I do that now I get no logo and get to my dekstop. Realizing I'm missing out on advancing my boot, like you mentioned about fsck, I now leave it in, but get dropped to VTTY1 first. I have to manually do Alt+F7.

---

### Post by sports fan Matt on 2010-03-12
I had to update mountall then install things and all worked fine.

---

### Post by VMC on 2010-03-12
> **keybuk said:**
> "Booting with the framebuffer renderer leaves the system at textual "login:" screen" ?  

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538214](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538214)

(which is mentioned in the changelog specifically)

I read the changelog but didn't have that issue until today, so I guess I just discarded it - unless the changlog has recently changed.

Thanks for the bug report. I'll go there now.

---

### Post by ranch hand on 2010-03-12
I am on a 64 system and updated all my installs and upgraded the throw aways and, of coarse screwed them.  Popped over to my 8.04 to 10.04 test drive and did it there and everything was fine.

Came back here and saw this thread and checked and sure enough there were new updates so I redid the throw aways and rebooted to them just fine.  Reupdated my other installs and upgraded them.

This one I left alone as it, and it alone seems to want to remove casper.  Just went to synaptic and upgraded the other stuff.

---

### Post by brucemartin on 2010-03-13
> **keybuk said:**
> Copying one name to the other should be enough I think; only the name changed, not the contents.

make /lib/libplybootclient.so.2 a symlink to or copy of /lib/libply-boot-client.so.2

i tried creating a symbolic link but it said /lib/libplybootclient.so.2 already exists. i then deleted /lib/libplybootclient.so.2 and create a symbolic link of /lib/libply-boot-client.so.2 to point to /lib/libplybootclient.so.2 but it doesn't work, i still get a black screen.

now what? any ideas?

please note that i'm getting absolutely no error, just a black screen.

---

### Post by ElSlunko on 2010-03-13
If you can chroot into your partition from the live CD you can run sudo apt-get upgrade.

---

### Post by rooijan on 2010-03-13
As previous posts show chroot and update will work.  There is a link to fixing a 32bit system.  Here is what I did for 64bit 10.04 if you are unfamiliar with chroot:

Boot livecd with correct architecture.  I booted 9.10 amd64.
Use fdisk -l to see what your linux main partition is. 

[COLOR="Gray"]root@ubuntu:~# mkdir /media/l
root@ubuntu:~# mount /dev/sda1 /media/l
root@ubuntu:~# mount -o bind /proc /media/l/proc
root@ubuntu:~# mount -o bind /dev /media/l/dev
root@ubuntu:~# mount -o bind /dev/pts /media/l/dev/pts
root@ubuntu:~# mount -o bind /sys /media/l/sys
root@ubuntu:~# chroot /media/l /bin/bash
root@ubuntu:/# sudo dhclient eth0[/COLOR]   [COLOR="Red"](could also be wireless wlan0) [/COLOR]

I did install the package manually but an apt-get update ; apt-get upgrade would have caught it anyhow.

root@ubuntu:/# wget [http://us.archive.ubuntu.com/ubuntu/pool/main/m/mountall/mountall_2.8_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/m/mountall/mountall_2.8_amd64.deb)
root@ubuntu:/# dpkg -i mountall_2.8_amd64.deb

root@ubuntu:/# apt-get update ; apt-get upgrade

---

### Post by ranch hand on 2010-03-13
I love these "don't eat the yellow snow" threads.  They sure do keep you from making big mistakes.

There must be something wrong with 10.04.  We had  a lot more of this kind of FUN in 9.10-testing.

---

### Post by Half-Left on 2010-03-13
Yep, I dived in and did the update and of course it wouldn't boot. It seems crazy that this would stop the boot process. If it doesn't find the lib, it should drop back to the normal kernel framebuffer and boot text, not leave the system unable to boot.

I fixed it anyway, thanks to the commands. All good alpha fun.

---

### Post by ElSlunko on 2010-03-13
> **ranch hand said:**
> I love these "don't eat the yellow snow" threads.  They sure do keep you from making big mistakes.

There must be something wrong with 10.04.  We had  a lot more of this kind of FUN in 9.10-testing.

LOL! I remember that nightmare. I think it's funny that testers are getting upset & usability issues (which lets face it has run it's course of discussion) & Karmic testers were dealing with bootability issues! ;P

---

### Post by brucemartin on 2010-03-13
> **rooijan said:**
> As previous posts show chroot and update will work.  There is a link to fixing a 32bit system.  Here is what I did for 64bit 10.04 if you are unfamiliar with chroot:

Boot livecd with correct architecture.  I booted 9.10 amd64.
Use fdisk -l to see what your linux main partition is. 

[COLOR=Gray]root@ubuntu:~# mkdir /media/l
root@ubuntu:~# mount /dev/sda1 /media/l
root@ubuntu:~# mount -o bind /proc /media/l/proc
root@ubuntu:~# mount -o bind /dev /media/l/dev
root@ubuntu:~# mount -o bind /dev/pts /media/l/dev/pts
root@ubuntu:~# mount -o bind /sys /media/l/sys
root@ubuntu:~# chroot /media/l /bin/bash
root@ubuntu:/# sudo dhclient eth0[/COLOR]   [COLOR=Red](could also be wireless wlan0) [/COLOR]

I did install the package manually but an apt-get update ; apt-get upgrade would have caught it anyhow.

root@ubuntu:/# wget [http://us.archive.ubuntu.com/ubuntu/pool/main/m/mountall/mountall_2.8_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/m/mountall/mountall_2.8_amd64.deb)
root@ubuntu:/# dpkg -i mountall_2.8_amd64.deb

root@ubuntu:/# apt-get update ; apt-get upgrade

too late for me, i ended up reinstalling. but it should help others having the same issue...

---

### Post by ubuntubrian on 2010-03-15
Any help as how to fix this with Lucid running in VBox?

---

### Post by teh603 on 2010-03-15
For those of us not subscribed to [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538214](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538214) , the dev working on it has asked people to submit syslogs. Instructions can be found within the bug comments.

---

### Post by maestrobwh1 on 2010-03-25
> **ubuntubrian said:**
> Any help as how to fix this with Lucid running in VBox?

Um, can't you boot from the iso image and then chroot into your "system" as advised by brucemartin?

---

### Post by godslam on 2010-03-25
I did an update and my system still started up afterwards, but my keyboard won't work because it's bluetooth. It worked perfectly beforehand though. When I restart/shutdown, I see something about Plymouth. Is Plymouth my problem or is it something else?

---

