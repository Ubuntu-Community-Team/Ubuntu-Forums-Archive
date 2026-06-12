---
title: "making copy of my installed system"
date: 2011-01-05
forum: Installation &amp; Upgrades
---

### Post by electroken on 2011-01-05
I have a friend who has limited access to a high speed connection and I want to make him a copy of my Ubuntu installation so he will not have to go on line to download all the programs I have put on my system. I would also use this to copy my ubuntu installation to other computers i own. 
Is this possible or do I need to start at scratch for all the computers I want to put ubuntu onto? It would save me a lot of grief if I could do this. 
I would expect there might be some kind of setup files necessary for the disk to be able to be used to make an install, but I want to ask just in case this might be something which is possible to do.
I hope I have made myself clear as to what I am trying to do.........make my own ubuntu distro install disk with my own additions to it and probably use a dvd and not a cd.
Ken

---

### Post by gdonwallace on 2011-01-05
As far as just making a backup of your hard drive, I would recommend clonezilla.  It runs on a CD and will make a backup image of your existing ubuntu install.  Check that out, it will do what you want.  

Once you have the image, you can then use clonzilla to restore the image to your friends computer, and it will work just like yours does.

Not too sure on making your own distro.  Have not done that so don't really have any advice.

---

### Post by electroken on 2011-01-05
Well I guess if it is making a copy of my operating system which I can burn to a dvd later and use that dvd to put that on another computer, then it would do the job. I figured there were programs which could back-up my hard drive, but didnt know they would actually let me save a copy of my system as such. I am not sure it will all fit on a dvd, especially if it automatically will save all my data (emails etc) along with it.
But you seem to be saying it can put that system back onto another computer, so that should do it. \
I will give it a try. Thanks

---

### Post by jaythedogg on 2011-01-05
> **electroken said:**
> I have a friend who has limited access to a high speed connection and I want to make him a copy of my Ubuntu installation so he will not have to go on line to download all the programs I have put on my system. I would also use this to copy my ubuntu installation to other computers i own. 
Is this possible or do I need to start at scratch for all the computers I want to put ubuntu onto? It would save me a lot of grief if I could do this. 
I would expect there might be some kind of setup files necessary for the disk to be able to be used to make an install, but I want to ask just in case this might be something which is possible to do.
I hope I have made myself clear as to what I am trying to do.........make my own ubuntu distro install disk with my own additions to it and probably use a dvd and not a cd.
Ken

Why not try your hand at creating your own LiveCD distro?

Take a look at this guide, it will help immensely. :) (Save you the trouble of cloning your drive & all of the variables that could lead to trouble later on.)

[https://help.ubuntu.com/community/LiveCDCustomization]("https://help.ubuntu.com/community/LiveCDCustomization")

---

### Post by howefield on 2011-01-05
> **gdonwallace said:**
> Once you have the image, you can then use clonzilla to restore the image to your friends computer, and it will work just like yours does..

Clonezilla excellent tool that it is, can't clone to a destination that is smaller than the source drive/partition. May be a factor here, may not.

Remastersys may be worth a look.

[http://remastersys.sourceforge.net/](http://remastersys.sourceforge.net/)

---

### Post by Terry of Astoria on 2011-01-06
> **gdonwallace said:**
> As far as just making a backup of your hard drive, I would recommend clonezilla.  It runs on a CD and will make a backup image of your existing ubuntu install.  Check that out, it will do what you want.  

Once you have the image, you can then use clonzilla to restore the image to your friends computer, and it will work just like yours does.
   
---This might work if the computers are identical ----
But not normally a recommended procedure. 
Clonezilla is GREAT for backing up a system . . . .

---

### Post by electroken on 2011-01-15
I am making a reply to my own post here so that perhaps another new user might see what I have found out to be a great way to make a copy of my system as it is installed on my computer so that I have a dvd to use to boot up on another machine and to install the system on it if the person agrees to go ahead and install Ubuntu. 
I used a program called remastersys and it works great. I did this as a relative newcomer to Ubuntu so I dont think anyone would have a major problem doing the same thing.
I had to learn some things about making sure I had a burner program on my Ubuntu system but that is about all I had to do. I went along with the instructions and easily made an iso of my system which was then burned to a dvd (had to use a dvd to have enough room for all my installed programs). I had quite a few programs installed on my computer in order to make sure my friend or any other machine I might make the install on, would have adequate resources if it could not get on line easily.
Remastersys owner/author of the program was a lot of help. When I am able to do so, I plan to donate to his site. It is not easy lately to come up with money for these things as I am retired on ss.

---

