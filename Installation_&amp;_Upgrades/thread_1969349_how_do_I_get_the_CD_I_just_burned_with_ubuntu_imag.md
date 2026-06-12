---
title: "how do I get the CD I just burned with ubuntu image"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by jadtech on 2012-04-29
i out the cd in the drive  boot I can here the drive run  and spin on boot and  it still bots directly to windows..

if I put the cd in while windows is running I get the option to install wubi , looking on the dvd I see all the files and folder  .. 

the lap top hp g6 quad core only been out of the box about 30 hours
trying to  use the live cd and see if I can get that going beforeI install here ..

---

### Post by josephmills on 2012-04-30
> **jadtech said:**
> i out the cd in the drive  boot I can here the drive run  and spin on boot and  it still bots directly to windows..

if I put the cd in while windows is running I get the option to install wubi , looking on the dvd I see all the files and folder  .. 

the lap top hp g6 quad core only been out of the box about 30 hours
trying to  use the live cd and see if I can get that going beforeI install here ..

Hey Jadtech 

have you gone into the bios of that computer and made sure that the computer is booting from cd ? also have you checked the md5sum of the iso ? 

thanks

---

### Post by jadtech on 2012-04-30
> **josephmills said:**
> Hey Jadtech 

have you gone into the bios of that computer and made sure that the computer is booting from cd ? also have you checked the md5sum of the iso ? 

thanks

well I havent gone in the bio's how ever I have ben to the hp sote  and it states that  the boot order by default goes floppy,  cd/dvd hard drive,  usb and net work adapter ..

how ever  there was a notice nearly as soon as I got things started from hp  there was a bio update I went and installed  today not sure if this changed anything..

  the other odd thing I find is HP seems completely unsure  what F key to use to get to bio's badcially  in a round about way says spam them all till one works  :)

---

### Post by josephmills on 2012-04-30
try   
f1
f2
delete
f10
f12

It will be one of them wait this is not a mac is it :)

---

### Post by jadtech on 2012-04-30
> **josephmills said:**
> try   
f1
f2
delete
f10
f12

It will be one of them wait this is not a mac is it :)

the check matches 

I will attempt to make sure the bio'are  set right :)

ok at this point I can tell you  geting in the bio's  is not done with f1 though this does bring up a list of computer specs its not f2 ,f6 ,f10  (delet)e does bring up a boot menu  to choose an operating system or mem diagnostics ..

what ever happen to the simple days  :) 

there is a notice I see on boot that say press esc now though  I remember from the past that is  the brings up recovery options not sure if that includes the bio's or not  shrug 

nope not a mac its an HP pavillion g6 notrbook

---

### Post by josephmills on 2012-04-30
Here you go jadtech

[http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&dlc=en&docname=c00364979&lc=en&man_lang=fr&product=5068623&query=G6-1051ex&tool=](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&dlc=en&docname=c00364979&lc=en&man_lang=fr&product=5068623&query=G6-1051ex&tool=)

---

### Post by jadtech on 2012-04-30
> **josephmills said:**
> Here you go jadtech

[http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&dlc=en&docname=c00364979&lc=en&man_lang=fr&product=5068623&query=G6-1051ex&tool=](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&dlc=en&docname=c00364979&lc=en&man_lang=fr&product=5068623&query=G6-1051ex&tool=)

wow ok thrid times a charm I must have been maybe nhitting the f10 button  at the wrong moment because finally bio's greet4ed me  whenI checked harddrive was first and the cd second I switched them so CD/dvd is on top, not sure just yet if this helped  but its all changed..

thanks for the link I was already at that page had it book marked but it leads tto the confusion since all it says is all there computer are different  and pretty much tells you  the only way is f key roulette :)

if the disk dont work this time guess I will find out how to slow the windows burner down or get another program and make it again, Im thinking im hopeing this sticking point is the issue and i am able to boot live cd  no peoblem hehe ..

thanks for the help

---

### Post by jadtech on 2012-04-30
wow my lucky day changed the bio setting so cd/dvd was at the top of the list on this new HP  I put the unbuntu 12.04 64bit live cd in the drive  booted first try   I am posting from it now , I will say booting  ubuntu from this dvd is a bit slow  well ok a bit like wrapping  ones lower lip around your head and  attempting swallowing your self each step took a bit  but im here  no special boot changes nothing..  

i guess this is a good sign for an install on this machine  it could use the drivers for the video card installed but looks and runs great off the dvd :) 

thank for  the bios suggestion one would think one a new computer just out of the box  bio's would have at least cd/dvd set to boot first not HDD ..

---

### Post by grahammechanical on 2012-04-30
The reason why the live CD/DVD loads slowly is because it is assessing the hardware. Now, when you select install, the hardware checks are already done.

Also you will find that while you are filling in your user details and your location, etc., files are loading in the background. This is an improvement from earlier days when things were done one at a time.

It makes the install seems faster.

Regards.

---

