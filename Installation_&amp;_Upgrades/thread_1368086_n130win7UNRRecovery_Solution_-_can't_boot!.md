---
title: "n130/win7/UNR/Recovery Solution - can't boot!"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by markb63 on 2009-12-30
Hello,

I got a Samsung N130 netbook with win7(starter) starter on it. I decided to keep win7 and go dual boot with UNR. All worked well until I used the Recovery Solution to back up my win7 partition. So here's what I did to get to this point:

- Ran the initialization of the machine right out of the box, during which I split the disk in half (planning to use the second partition for UNR) and the recovery solution did its bit to grab a snapshot.

- Installed a few windows apps and got everything how I wanted it there.

- Built a USB stick with UNR and installed that, setting up a swap and / area using what was drive D: from above. All went well there too. Grub start up gave me:
    UNR
   Vista (? thought this was interesting - more on this later)
   Windows 7

   and I could boot Ubuntu or win7

- boot to Linux and installed a bunch of good stuff there :-)

- so now I think I might try the Samsung Recovery Solution to back up my win7 stuff. It says there is no recovery data and won't run. OK, so maybe i will have to just make an image another way - not so bad.

- a little later I decide to see what the Vista boot option from the Grub menu does! Well it boots and goes right to the Samsung Recovery Solution console - cool :-) So I go ahead and attach a USB disk and ask it to do a full image backup of C:. Seems to go fine - and needs to reboot.

I get "Grub loading" - no boot menu and the machine in an endless loop of restarting! What in the world did going to the Recovery Solution and just backing up do to screw up the booting?

I have booted with pmagic and all the partitions appear to be there (I have mounted them and browsed the files).  I just don't know how to get grub to pick up the menu.

Here is a screen shot from GParted - hoping someone can help me get restarted without having to do the whole thing over.



Thanks in advance...
MarkB

---

### Post by MarkSp on 2009-12-30
The same thing has just happened to me. I haven't got a clue how to get out of the loop. Help please!

MarkSp

---

### Post by MarkSp on 2009-12-30
This just worked for me

[http://gadgetmix.com/index/how-to-restrore-grub-bootloader-in-ubuntu-9-10-standard-and-netbook-remix/](http://gadgetmix.com/index/how-to-restrore-grub-bootloader-in-ubuntu-9-10-standard-and-netbook-remix/)

---

### Post by markb63 on 2009-12-30
Oh Great :-)

So after following that solution, did it change the Grub boot menu? I mean did the menu still have your win7 and linux selections as you had originally or did it set them up differently? 

you can boot ubuntu and win7 now - you didn't have to reinstall the OS did you?

I am curious to know if you ran Recovery Solution like I did that caused this to happen?

Thanks for you help...

Mark B

---

### Post by MarkSp on 2009-12-30
Yes... I ran the backup and that's exactly what happened. I was on XP. I follwed the instructions as written down and everything returned just as it was before. Just make sure you get the right disk number. Mine was sda5 which was the Linux partition. Good luck.

---

### Post by markb63 on 2009-12-30
MarkSp,

It worked a treat :-) - every things back to the way it was - thanks for the tip.

I will have to try to figure out why using the Recovery Solution does this, I would quite like to use it for my win7 backups.

I need to gen up on the whole booting process, I would like to understand what is actually happening. anyone have any good pointers to a good ground up coverage and in the context of the this version of GRUB we are using with UNR?

cheers, Mark B

---

### Post by Eemeez on 2010-02-15
I had the same problem, and also the solution mentioned above worked. Thanks :KS

---

### Post by jackhadrill on 2010-07-24
First post - 
Hi, sorry that you had this problem. I had the same problem about half a year ago and it was a nightmare trying to fix it. Basically it erases you mbr partition leaving no bootloader.

Two possible ways of fixing this are:
1. Reinstall Both OS's

2. Google how to restore GRUB from Ubuntu Live CD.

:D

Hope this helps others!:p

---

