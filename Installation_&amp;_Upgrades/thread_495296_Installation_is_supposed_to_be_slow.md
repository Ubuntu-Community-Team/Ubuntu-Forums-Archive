---
title: "Installation is supposed to be slow?"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by scuba_suit on 2007-07-07
i got a dell dimension 2400 2.4 Ghz P4 256MB RAM, i finally got the live cd to work on it, so now it loads up, when i click for the install everything grinds down to a snail's pace, i thought that it would load up 1-2 hours, i was up last night for 4½ hours and it was only loading up the "install" window, when i clicked for it to install it got up to step 2, then it freezes/hangs up, why is the installation so slow? do i need more memory? what is the REAL system recommendation (the recommended says 128MB of RAM, after trying to install it several times i would say "yeah right") when i do the live cd it does seem kinda sluggish but at least i can use ubuntu (eventhough i haven't tried all the applications)

---

### Post by tgm4883 on 2007-07-07
Use the alternate CD.  The live env is eating up a good portion of your RAM

---

### Post by scuba_suit on 2007-07-07
when i use the alternate cd, does my pc have to have windows so that i can open up the .iso file? i am installing it to a bare bones blank no os on the hd pc...

---

### Post by tgm4883 on 2007-07-07
> **scuba_suit said:**
> when i use the alternate cd, does my pc have to have windows so that i can open up the .iso file? i am installing it to a bare bones blank no os on the hd pc...

open up the iso file?  You have to burn it to a cd as an image.  Then pop it in like the live cd

---

### Post by scuba_suit on 2007-07-07
cool, i'm going to try it now, i'll get backwith the results....

---

### Post by Gremlinzzz on 2007-07-07
Xubuntu is a complete GNU/Linux based operating system with an Ubuntu base. It is lighter on system requirements and tends to be more efficient than Ubuntu with GNOME or KDE, since it uses the Xfce Desktop environment, which makes it ideal for old or low-end machines, thin-client networks, or for those who would like to get more performance out of their hardware.
[http://distrowatch.com/?newsid=04180](http://distrowatch.com/?newsid=04180)
click xubuntu-7.04-desktop-i386.iso

---

### Post by scuba_suit on 2007-07-07
well i tried it with the alternate disc, when the pc starts up the dell logo shows but then a message "press F1 to try and reboot, F2 for setup utility", when i burned the image, i used infrarecorder, did i do it right? i dl'ed ubuntu file so that's the file i burn to as an image right? why isn't my pc reading it like a live disc? gremlinzzz, i read up on xubuntu, i think that would be cool for my wife's computer which has a intel celeron (will it run on something that old?) i want to stick with ubuntu so i guess i gotta buy more RAM to speed things up...

---

### Post by ddrplayer512 on 2007-07-07
Describe the steps you used to burn the iso file to the cd

Also, the alternate CD uses a text installer and is the reason it is faster on slower computers. It doesn't have to load  an entire desktop.

Now, If I were you, I'd give your system some more RAM so it has 512 MB, but that is my personal opinion. Keep in mind that the Live CD is MUCH slower than what you will get if you actually install Ubuntu simply because it's loading from the very slow cd. If Ubuntu runs from the hard disk, It will be significantly faster.

---

### Post by scuba_suit on 2007-07-08
well that'x what i def will do (i'll get 1gig on top of the 256 it has) as for burning the image, i go to an option in the menu that says "Burn image..." then it opens a box to load the file i load the ubuntu file and write at 4x then burn, should i burn it a slower rate?

---

### Post by scuba_suit on 2007-07-08
what's the comparison between ubuntu v. xubuntu? i know that xubuntu is lightweight, but what does/doesn't it come with? i'm trying to find info on what systems (and how much minimum RAM) can run it without problems, anyone know?

---

### Post by Irony on 2007-07-08
Look here for a description of how to burn an iso;

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29)

Once the iso is burnt you will see it as a bunch of folders and files.

Note if you have a desktop CD that you can still choose to do a text based install by clicking install and then selecting text install, it maybe in the options part.

Xubuntu uses xfce a light alternative to gnome and kde, however stuff like open office will still run horrendously slow if you have a small amount of RAM, you might have to consider things like abiword.

---

### Post by scuba_suit on 2007-07-08
yo thanks irony, eh, i'll bite the bullet and get more RAM (and hopefully that'll work) as for the burnt cd, yeah it has all the files and folders, i burned two cd's and when i pop them in, the pc reads either as a audio cd or i get a "press F1" to reboot, i'll read that link....

---

### Post by Benjcrowe on 2007-07-10
The solution for me was to use Safe Graphics. i.e. it's the graphics that slow to a snail's pace. This worked on Dell 2350 & 2400's and the early GX series as well.

It has not worked on IBM NetVista machines. Not even VGA worked - X failed to load.

I find it strange that Ubuntu goes for the higest possible resolution and a refresh rate of 85 Hz. That's a lot to ask of a graphics card, IMHO. I dropped it from 1600x1200 to 1024x768 but could not reduce the 85Hz. You can do that before you select the Install icon, by the way.

---

### Post by scuba_suit on 2007-07-10
Benjcrowe, i think i tried loading it up with safe graphics but to the same effect, i'm lookin at that link on "how to burn images" and buying more RAM, does anyone know how high i can go with a dell dimension 2400 in RAM? this tech guy told me 2 gigs but someone else said only 1?

---

### Post by tgm4883 on 2007-07-10
2 GB
[http://www.crucial.com/store/listparts.aspx?model=Dimension+2400+Series](http://www.crucial.com/store/listparts.aspx?model=Dimension+2400+Series)

---

### Post by seaan on 2007-09-08
> **ddrplayer512 said:**
> 
Now, If I were you, I'd give your system some more RAM so it has 512 MB, but that is my personal opinion.

I have 2Gb RAM on may laptop and the installation is slow also for me. Slow is not probably the correct word: it seems stuck with the CD keeping on rolling back and forth in the meantime. It took 30 minutes to display the "install" window...

I will give a try to the text based installer but I'm wondering why the Ubuntu team does not release a GUI installer without Live CD.

Question: will the text based installer install also the graphical desktop ?

Thanks
Sergio

---

### Post by tgm4883 on 2007-09-08
> **seaan said:**
> I have 2Gb RAM on may laptop and the installation is slow also for me. Slow is not probably the correct word: it seems stuck with the CD keeping on rolling back and forth in the meantime. It toow 30 minutes to display the "install" window...

I will give a try to the text based installer but I'm wondering why the Ubuntu team does not release a GUI installer without Live CD.

Question: will the text based installer install also the graphical desktop ?

Thanks
Sergio

use the alternate cd, check the cd for defects

---

