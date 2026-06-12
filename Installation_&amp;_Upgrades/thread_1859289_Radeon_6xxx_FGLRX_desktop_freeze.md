---
title: "Radeon 6xxx FGLRX desktop freeze"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by BartBlackMagic on 2011-10-13
Hardware specs:
ATI HD6970m
Intel 310SSD
Core I7

After several clean installs of Kubuntu 11.10 I had to downgrade to 11.04 because eventually my whole pc freezes! I tried using the proprietary drivers downloaded from the ATI/AMD site as well as with the FGLRX drivers from the repositories offered by Jockey.  Disabling compositing via OpenGL to XRender made the system more stable (30 minutes stable vs 2 minutes).
Please let me know if you've got a solution.  I use this machine for professional use, so I have to admit it was not very smart to upgrade to a stable release on the first day.

_**EDIT:**_
Phoronix made a post on their website about this flaw: **[click]("http://www.phoronix.com/scan.php?page=news_item&px=MTAwMDc")!**

---

### Post by apostra on 2011-10-13
Same issue here! 5hours and I have no OS on pc atm!tried several times for kubuntu same drivers,6xxxx.nothing that used t work on previous releases made an effort! I tried t install 11.04 but the downloading is approx 192 hours,a little bit more and we might get the next 12.04!

Looking forward for solution,on graphics at least,servers make sence t be full at this time!


P.S.Very disappointing release "date" this one. Hope fast recover.

---

### Post by khatat on 2011-10-14
hello
i have the same problem
i have a hp Pavilion dv7-6105sd with amd radeon hd 6755g2 i could try niether kubuntu or ubuntu live cd cause i will get a black screen and i can not see any thing. i tried kubuntu with nomodeset option i could see the windows with choosing install kubuntu or try it when i click try button after a while laptop freezes and if i install it and boot with nomodeset after installation again i will face with a freeze screen before loading X but i can go to the recovery mode so i installed the graphic driver with the original amd driver but after installation when i ran aticonfig --initial i got an error that there is a problem with a shared library!! what should i do before installing driver??
please help me i can not get both ubuntu or kubuntu desktop but with 11.04 i did not have any problem with graphic driver.
thanks for your help

---

### Post by apostra on 2011-10-14
Hey guys,

I put the cd on and let it install during the night and finally worked out.

I logged in and enabled the drivers, not the "post release", had an error and couldnt installed.

I update/upgraded and work as should be, no longs downloading. 45 mins on the run and still no freze, i hope would be ok.

---

### Post by collisionystm on 2011-10-14
I had problems with this last night. Not the same, but ATi driver problems none-the-less.

I installed 11.10 with alternative install. Live CD would result in black screen.
Had to boot to command shell
Removed xorg ati drivers
Finally able to boot to GUI
Installed ATI Catalyst drivers from website
Install finished, Ran ATICONFIG for single head mode. 
Rebooted... 
Ubuntu would not boot past the splash logo. System would freeze. 

Booted into system rescue, hit the normal boot, held the shift key to boot it into safe mode. Once again back at prompt.

sudo apt-get purge fglrx
Could not purge everything
Looked at the log file, said I had to run a script manually to delete everything. 
did this
Re-Installed FGLRX.
sudo apt-get install fglrx
rebooted.
worked.

Im not sure what order you did things in, but if it was anything like what I did... maybe this will help?

---

### Post by apostra on 2011-10-14
Last night i tried these commands when i was trying to install the ati drivers:

sudo sh /usr/share/ati/fglrx-unistall.sh

  if that gives you errors:
           sudo apt-get remover --purge fglrx fglrx_*fglrx-amdcccle*fglrx-dev*xorg-driver-fglrx

then sudo -s ./ati......

I found them on a web, didnt keep the link sorry, but worked for me, 

All these to pass the black screen/loggin bug ...BUT... I had my screen "moved" right by half.

Then I just enabled the driver, reboot and all was fine.

Again all what I did, check these out before doing it, im not that expert.

Hope it helps.

Apo

---

### Post by khatat on 2011-10-14
hi
how did you guys installed fglrx did you get it from internet?
i am in a consol mode and i can not connect to internet i dont know how?
when i ran this command sudo apt-get install fglrx he said:
Package fglrx is not available but is referred to by another package. This may mean that the package is missing, has been obsoleted or is only available from another source.
E: Package 'fglrx' has no installation candidate

plz help me ;)
tnks

---

### Post by collisionystm on 2011-10-14
> **khatat said:**
> hi
how did you guys installed fglrx did you get it from internet?
i am in a consol mode and i can not connect to internet i dont know how?
when i ran this command sudo apt-get install fglrx he said:
Package fglrx is not available but is referred to by another package. This may mean that the package is missing, has been obsoleted or is only available from another source.
E: Package 'fglrx' has no installation candidate

plz help me ;)
tnks

At the command line, type

nano /etc/apt/sources.list

Go to the bottom 

look for 

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
**deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner**
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
[B]deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main[/B]

remove the # from these lines I have put in bold

CTRL+X then Y to save

sudo apt-get update
sudo apt-get install fglrx

---

### Post by khatat on 2011-10-14
> **collisionystm said:**
> At the command line, type

nano /etc/apt/sources.list

Go to the bottom 

look for 

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
**deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner**
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
[B]deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main[/B]

remove the # from these lines I have put in bold

CTRL+X then Y to save

sudo apt-get update
sudo apt-get install fglrx

thanks for your answer but that file is empty and my problem is that i can not connect to internet from command line (my network hardware led is on)

---

