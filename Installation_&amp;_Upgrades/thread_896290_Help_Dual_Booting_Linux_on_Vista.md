---
title: "Help Dual Booting Linux on Vista"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by morana on 2008-08-21
Alright, I have a tablet laptop with Vista already installed and I've read almost literally *tons* of documentation of how to dual boot. Unfortunately they don't mention what to do with my certain problem.

I partitioned by hard drive and followed all of the instructions. I click on the "Install Ubuntu" and then it seems to work, the bar goes all the way to orange. And then suddenly it it reverses and at the bottom it says to remove the CD and then to press enter. And everything turns off! I've seen screenshots and that was supposed to happen at the end when everything installed.

Can someone please help me? I've been using Ubuntu on my desktop computer and I've fallen in love and never want to have to use windows ever again. Someone please reply ASAP!

---

### Post by Chronix33 on 2008-08-21
If you don't want to use windows anymore, as in, not even have it on the computer, just download and burn the image to a disc, insert, boot from disc, and when you go to install, it will give you the option to completely erase the HDD and just put your distro of choice on there. Dual booting is more complicated, so please clarify and we will get it done.
Chronix

---

### Post by morana on 2008-08-21
That's my problem--it won't install. 
I enter the "Install Linux" and then the orange bar starts to fill up and then reverses and then it says "Please remove the CD, close the tray and press enter" and it shuts down.

My laptop is new and is a HP Pavilion tx2510us PC and I checked if the CD was faulty and it wasn't.

---

### Post by caljohnsmith on 2008-08-21
Since the Live CD isn't working well with your setup, you could try the [Hardy alternative CD]("http://releases.ubuntu.com/8.04/") and see if that is successful installing to your system.

---

### Post by falcon61102 on 2008-08-21
With the CD you have, try running the Check CD command from the Boot menu.  This will check the cd for any errors that may have occurred either in download or burn.  Furthermore, if and when you burn a new cd, try to burn it below 4x as that will have the least likely chance of having any burn errors.

---

### Post by morana on 2008-08-21
Okay, I checked the CD and it was fine. 

I tried what caljohnsmith said and this time when I enter install, this time it just shuts down, apparently its overheating and forces it to turn off.

Could the problem possibly be my hardware?

---

### Post by morana on 2008-08-21
Also, when I boot up my laptop it asks which OS I want to use/display.

I pick Ubuntu but then afterwards everything turns off, but if I pick Vista it works fine. :(

---

### Post by Sef on 2008-08-22
Did you partition Vista with its own partitioner?  If not, that is likely the source of the problem.

---

### Post by falcon61102 on 2008-08-22
The reason that you are getting errors if you select Ubuntu is because from the sounds of it, you haven't had a successful install yet so there really isn't a Ubuntu OS to go to yet.

Also did you receive an error or something stating that the system was shutting down to overheating?

---

### Post by morana on 2008-08-22
Yes, I did partition Vista with its own partitioner.

And yes, I received an error that the system was shutting down due to overheating. 67-69 degrees C!

---

### Post by gali98 on 2008-08-22
Guys this is a simple fix.

Morana if you want an easy step by step guide to your lappy, go here:

[http://ubuntuforums.org/showthread.php?t=873188](http://ubuntuforums.org/showthread.php?t=873188)

I know that will help a lot (it has helped a lot of people..)

Kory

---

### Post by morana on 2008-08-22
ZOMG! I did just as gali98 said and it installed!
Thank you, thank you, thank you!

I despise Vista, but I know that my tablet isn't completely supported yet. And my dad doesn't fully trust Linux, strangely.

Thank you again, gali98!

---

### Post by gali98 on 2008-08-24
Well as far as the guide goes, don't thank me, thank thegnark... he's the one that wrote it.

As far as the tablet part goes, I wrote this guide that gets it fully working!

it may look a little long and hard, but just follow the instructions and it will work. 

[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)

if you have any problems with the wacom stuff (tablet part) then please post there...
Enjoy Ubuntu!
Kory

---

