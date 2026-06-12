---
title: "Installing Drivers"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by Mike1056 on 2010-03-28
I recently built a new machine and am having some driver issues.  The DVD that the motherboard came with has Linux Drivers on it (which is nice), but I'm not sure how to install them.  Since I'm very much a newbie, If it would be easier to help me through Instant Messenger, my Yahoo is KatieKelly10562008 and my MSN is KatieKelly1056.  Otherwise, I can always check this forum!  Please help!
 
Here are my spcs.
 
Asus M4A77D Motherboard
AMD Phenom x4 9750 (2.4 Quad Core) Processor
8GB 800Mhz DDR2 RAM
XFX Radeon HD 4350 1GB Video Card
Ubuntu 9.10 64-bit
 
I didn't skimp on this at all!
 
Thanks in advance for your help!

---

### Post by munchen800 on 2010-03-28
Need a little more info, if the disk has a blablabla.sh file then you would browse to the disk in a terminal and type sudo ./blablabla.sh and it would compile and run. Just as a question though do you need the drivers?? if you are OCing or something like that then just grab GKrellM from the package manager. It will sown usage and Temps.

---

### Post by Mike1056 on 2010-03-28
Well, the audio is very weak on it despite having a 2.1 stereo speaker system with a bass.  I have to crank it just to hear out of it.  Also, the graphics seem choppy at places.  The drivers disc has audio drivers and it's installer is install.sh  I double clicked on it and ran it in terminal, it asked me if I wanted to proceed, I said yes, and then I never heard or saw anything after that and my sound isn't any better.  :(  Thanks for the quick repy!

---

### Post by munchen800 on 2010-03-28
Try opening a terminal and browsing to it like

cd /media/disk If you use your file browser to look in the disk it will give you the path at the top

then 

sudo ./install.sh

it didn't work cause you didn't run as root 

and I think ALSA is just crappy these days lol the audio on my lappy isnt what it was in Windows, but I'll never go back :)

---

### Post by Mike1056 on 2010-03-28
Dumb question...lol  when I get in terminal, how do I access the CD?  Sorry...I really am a noobie!

---

### Post by munchen800 on 2010-03-28
open the cd in your file browser and you should get some tabs at the top, that will be the path, then open terminal and do

cd /media/(name of mounted disk here)

thats it 

I'm not sure what it is mounting your cd as but it will be one of those tabs at the top but Ubuntu always automounts to the /media folder

---

### Post by Mike1056 on 2010-03-28
okay..new question...the disc is labeled MB SUPPORT CD and when I put the spaces in, it doesn't see anything past the first space.

---

### Post by munchen800 on 2010-03-28
Yeah it wont 

Are you sure its not mounted to something like disk0

You want the folder it is mounted to not the disk label 

and for future reference it you would type in like 

some\ arbitrary\ file\ name\ with\ spaces\ like\ this

---

### Post by Mike1056 on 2010-03-28
Finally found something that might be helpful.  Opened System Monitor and under the file systems tab, I found two devices...the hard drive and the rom drive.
The hard drive is /dev/sda1/ and the rom drive is /dev/sr0/media/cdrom0  but it's still not letting me do it when I try cd/media/cdrom0.  I tried copying the files to a folder on the hard drive and running from there but that didn't work, either. :(

---

### Post by munchen800 on 2010-03-28
to use cd you need a space

cd /media

open the terminal run 

cd ~/Desktop/the name of the folder here

if you put the folder on the desktop of course

or you can

cd /media

then type

ls -l

it will list the contents of the media folder and show you the size in bites then

cd into the largest one with no slash

---

### Post by Mike1056 on 2010-03-28
Got that part!  FINALLY!!  lol..now it checks to see if I'm using the root account (I am) and then it checks to see if I have installed the kernel source (which it says I haven't).  I really do appreciate all the help, by the way!

---

### Post by munchen800 on 2010-03-28
in your terminal run
sudo apt-get install build-essential

once all that installs run your ./install.sh

and you should be good
If you want a reference or a nice long read lol

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

but you should be ok with the build essentials

and its not a problem ;)

---

### Post by Mike1056 on 2010-03-28
Yep!!!  Finally got the sound running right on my machine!!  Thank you so much!!  This forum is one of the things that makes Ubuntu so awesome!  That plus the steadiness and reliability!!  Oh and the price and...lol  Thanks again!

---

### Post by munchen800 on 2010-03-28
Not a problem enjoy !!

---

