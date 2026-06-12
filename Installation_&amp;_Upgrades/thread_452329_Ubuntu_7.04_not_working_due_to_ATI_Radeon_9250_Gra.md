---
title: "Ubuntu 7.04 not working due to ATI Radeon 9250 Graphics Card"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by meegs on 2007-05-23
Hi,

I am a total noob to Linux, however I decided to give it a go and install Ubuntu Feisty.

I could not get the LIveCD to work....it would just hang on the orange bar and then print out some errors.

So I went for the Alternative installer.....it worked, but then X wouldn't load and the whole thing crashed.

So I tried using my onboard graphics card (by taking out ATI card) to boot into Ubuntu, this worked.

I then spent about a week trying to search forums for how I can fix the problem with my ATI card....to no avail....and I think this is mostly because I cannot even load Ubuntu when the ATI card is in my machine it doesn't make it past the "Loading Hardware Drivers Required for Boot" and then prints out errors....

I have tried quite a few things from different posts to try and rectify this error. This mostly was to do with booting using my onboard card and then going in and manually trying to change Xorg.conf file following different posts, stickies and how to's.....

None of these things worked...and the errors have not changed when I try and boot with the graphics card in.

I guess the feeling that I get is that Ubuntu is crashing at boot before anything is happening with X and there is in fact something happening with the basic driver for my card or y'know that ubuntu isn't recognising it at all! 

The card works fine in Windows XP.......and Ubuntu works fine without my ATI card in it.....

Does anyone have any suggestions on what I can try to fix this????

I'm at giving up point right now....I've tried for a week to get this thing to work but I'd really hope that its not all for nothing!

Please help!!!

Meegs

PC Specs:
HPd220 Intel Pentium 4 2.4GHz
512MB of RAM
15" Compaq LCD Monitor
PCI ATI Radeon 9250 Graphics Card
On-board card:
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

---

### Post by hessiess on 2007-05-23
ati cards are alwase problamatic. you need to find a driver for it

---

### Post by meegs on 2007-05-23
I understand that ati drivers are problematic.....have noticed that in all the posts on the forums....

And yeah, I can see that I need to get a driver for it....but like....how? If I can't even get Ubuntu to load....how am I to get a driver going?

Actually....how do you install a driver without using X?

---

### Post by hessiess on 2007-05-23
with nvidia you do sudo sh *************************.run  
were********************* is the name of the file
ive never used ati cards in linux being new to linux.

try google,in for "make of your card+ linux driver"

---

### Post by Voland on 2007-05-23
Maybe you should try this manual - [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

---

### Post by Ub1476 on 2007-05-23
Not to be rude, the guide above works, but the drivers suck:p (knows by personal experience)

Here's a workaround, no need to download any drivers during install:

[Linky to guide]("http://ubuntuforums.org/showthread.php?t=448809&highlight=Feisty+Fawn")

It's confirmed severalt times that this workaround works properly.

Please leave a comment in the thread to bump it, others might need help:)

Hope it works

Ub

---

### Post by meegs on 2007-05-23
Ok so as far as the linux drivers for my card go.....I have found them on the ATI site and downloaded them....but I'm not sure what to do with them....especially seeing as I can't start X and if I can't start X then I can't follow the installer instructions on the ATI site.
> 
Maybe you should try this manual - [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

I have tried this by using my onboard card and booting in to command line and it hasn't done anything more for me.

So, as for the comment from Ub1476....if I try that I might be able to get into X? I guess that's one thing, and then I would have to install the drivers for my ati card? I will give it a go tonight and see what I can see....

I mean when I boot with the ATI card I can't even get past the basic booting functions let alone even be close to making it into X....

But of course....I will try

---

### Post by digitalpure on 2007-05-27
The alertnative method works great for me.  I am using a hp nx940 laptop, with the X1600 and I get good frame rates and such now.  I could not even get X to work at all, it would crash everytime I tried to load it.

---

### Post by meegs on 2007-05-28
Ok so,

tried the method suggested by Ub1476 and it definitely doesn't work in my case.

I am pretty sure it isn't something to do with Xorg....it may even be some sort of random hardware conflict....

Thanks everyone for your help....but there shall be no Feisty Fawn for me :(

I am gonna give Edgy a go...y'know just for kicks....but I don't really have any hopes...

it just sux...I really wanted to move off Windows...but it would seem I don't really have a say in the matter

Peace out

Megs

---

### Post by hessiess on 2007-05-28
mabie try to find a cheep nividia card from somewere

---

### Post by meegs on 2007-05-28
well, it's actually really difficult to find a video card for my computer because it only takes old school PCI cards....so y'know nothin is cheap and its all out dated!

anyways, Edgy didn't work, had the extact same error as Feisty so I'm guessing its just that there is some crazy hardware conflict that's not gonna work for any kind of ubuntu.

perhaps one day when I get a new computer I will try

thanks again for peopleses helpses

peace

megs

---

### Post by handydan918 on 2007-05-29
From the "can't-hurt-might-help" department:
Open a terminal and type:
sudo dpkg-reconfigure xserver-xorg

and give the prompts that follow your best guess.

---

### Post by nowhereman1970 on 2007-05-30
do not give upso fast.

I have a pci radeon 9250 card also. And installed Ubuntu with not problem. 

This I would do:
(ati card not installed)
1.- boot Ubuntu from LiveCD.
2.- Mount the Ubuntu installed partition.
3.-  cd /munted/ubuntu-partition/etc/init.d
4.- sudo chmod -x gdm or move it to /home/usrname/
5.- poweroff
(install ati card)
6.- boot and enter BIOS SETUP (F10 or DELETE or F2,etc)
7.- Disable the onboard video card in BIOS. 
8.- Enable the PCI display in BIOS.
9.- save and boot Ubuntu installed
10. - You will not have graphic screen instead a console login prompt, if Ubuntu booted. 
11.-  if did not boot let me know 
12.- if booted then:
option 1
13.-  X --configure
14.- follow instructions
15.- start X with the new generated xorg.conf.new file. If something goes wrong. Please post the file xorg.conf.new that should be in your home directory.

hope it helps.

nowhereman1970

---

### Post by stchman on 2007-05-30
> **meegs said:**
> Hi,

I am a total noob to Linux, however I decided to give it a go and install Ubuntu Feisty.

I could not get the LIveCD to work....it would just hang on the orange bar and then print out some errors.

So I went for the Alternative installer.....it worked, but then X wouldn't load and the whole thing crashed.

So I tried using my onboard graphics card (by taking out ATI card) to boot into Ubuntu, this worked.

I then spent about a week trying to search forums for how I can fix the problem with my ATI card....to no avail....and I think this is mostly because I cannot even load Ubuntu when the ATI card is in my machine it doesn't make it past the "Loading Hardware Drivers Required for Boot" and then prints out errors....

I have tried quite a few things from different posts to try and rectify this error. This mostly was to do with booting using my onboard card and then going in and manually trying to change Xorg.conf file following different posts, stickies and how to's.....

None of these things worked...and the errors have not changed when I try and boot with the graphics card in.

I guess the feeling that I get is that Ubuntu is crashing at boot before anything is happening with X and there is in fact something happening with the basic driver for my card or y'know that ubuntu isn't recognising it at all! 

The card works fine in Windows XP.......and Ubuntu works fine without my ATI card in it.....

Does anyone have any suggestions on what I can try to fix this????

I'm at giving up point right now....I've tried for a week to get this thing to work but I'd really hope that its not all for nothing!

Please help!!!

Meegs

PC Specs:
HPd220 Intel Pentium 4 2.4GHz
512MB of RAM
15" Compaq LCD Monitor
PCI ATI Radeon 9250 Graphics Card
On-board card:
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

If you did install Feisty then the Restricted driver manager will have an ATI driver that you can use.  Enable it.  I have a laptop with an ATI card and the Restricted driver worked.

No problem.

---

### Post by handydan918 on 2007-06-02
I second the suggestion. nvidia cards are MUCH better supported. I use them in all my machines except this lappy, and it's the only one I can't run the 3D desktop on.

---

