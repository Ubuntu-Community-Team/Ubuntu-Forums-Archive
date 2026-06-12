---
title: "Weird instalation problem.. help needed."
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by jonnywombat on 2007-09-15
I was given a dead e machines pc, which was minus a few components, from a friend. I have installed the missing bits and pieces and pulled out my trusty 7.04 feisty live cd.

It boots fine off the live cd and all seems ok until I hit the install icon.

When the first language window appears it is very large and cannot be resized smaller... this is not to bad coz I can double click on english just fine..but in the next stage, the picture of the globe, It displays in the same way and although I can select my location I cannot proceed because the buttons are off the bottom of the screen.

As I said these windows will not resize (although application windows resize just fine), and I cannot change the screen resolution from 640xwhatever.

The graphics chip is onboard and is an intel chipset...

I find this all very bizarre and any help would be gratefully recieved. 

BTW my live cd is quite old now, if I burn a new one will it contain any updates that may help?

Thanks in advance

Jonny

---

### Post by Pumalite on 2007-09-15
Use the Alternate CD. Post your specs.

---

### Post by jonnywombat on 2007-09-15
Sorry for being dense..alternate cd??

specs are
CPU 	Intel® Celeron® 2.3 GHz 
Memory 	768 MB DDR RAM - PC2100 
Motherboard 	TriGem IM845GL (Imperial) 
Hard Drive 	40 GB samsung
CD / DVD Drive 	16 x Samsung SD-616T DVD-ROM 
CD / DVD Drive 	Samsung 48x24x48 CD-R/RW SW 248F 
Video / Graphics Card 	Intel 845G integrated graphics 
Floppy Drive 	Floppy disk drive 
Sound Card 	Avance AC'97 SoundMax 
Network Card 	Realtek 8139 / 810X (Onboard) 


Hope that helps

Jonny

---

### Post by logos34 on 2007-09-15
Reboot and try 'Safe graphics' mode on the menu screen.  Or open a terminal on the desktop and run the interactive graphics configuration:

**sudo dpkg-reconfigure xserver-xorg**

try the 'vesa' driver.

You can pretty much accept the defaults on the rest.

---

### Post by Pumalite on 2007-09-15
This is your problem:Video / Graphics Card Intel 845G integrated graphics 
So, you have to use Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below green sign 'Start Download'
Good luck. (cross your fingers)

---

### Post by jonnywombat on 2007-09-15
It's the oddest thing...

I had tried several reboots, both hot and cold, and also safe graphics mode etc.. all to no avail.. 

Just started to download alternate cd, and left machine to boot as I wanted to try the suggestion of reconfiguring..

When it rebooted this time.. then I had three resolutions available upto 1280x1024..which it was displaying at, and all has gone ok in the instal process..

I have not done anything and it seems to me to be most odd, but there you go..

Thanks for your help anyway

jonny

---

### Post by jonnywombat on 2007-09-16
Ok.. all was well with my install until I run the update tool and when it restarted I was back to low resolution only..

I have looked at** sudo dpkg-reconfigure xserver-xorg** but without any success..

I also looked at** install xserver- xorg- intel**  but this made no difference also...

In the long term I am looking for a small nvidia pci graphics card, but until "the bay" comes through with a suitable card  i would appreciate any further help to get it running properly as is.

Thanks again

Jonny

---

### Post by Pumalite on 2007-09-16
This continues to be your problem: Video / Graphics Card Intel 845G integrated graphics . I guess 'vesa' is your only chance at the moment.

---

