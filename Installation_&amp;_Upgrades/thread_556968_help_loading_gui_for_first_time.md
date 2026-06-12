---
title: "help loading gui for first time"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by lonelyxpeople on 2007-09-22
i'm trying to get ubuntu fiesty fawn running on a dell inspiron 6400.
its running an ATI Radeon x1300 at 128mb of ram,
1gb of ram,
an 80gb Hitachi Travelmate Hard Drive,
and an Intel Core Duo 1.6 ghz processor.


the problem is that the xserver fails because "no devices were found" when referring to screens.


help?

---

### Post by leo_rockway on 2007-09-22
same question was asked in this post
[http://ubuntuforums.org/showthread.php?t=518469](http://ubuntuforums.org/showthread.php?t=518469)


the answer is here...
[http://ubuntuforums.org/showpost.php?p=3129695&postcount=4](http://ubuntuforums.org/showpost.php?p=3129695&postcount=4)

next time search before asking. thank you.

---

### Post by lonelyxpeople on 2007-09-22
tried that. problem is, it tells me it "couldnt find package xorg-driver-fglrx"

---

### Post by Soarer on 2007-09-22
Best install it then.

System>Administration>Synaptic Package Manager (put in your password)

Search for xorg-driver-fglrx, mark for install.

Then see if you get any other errors.

---

### Post by lonelyxpeople on 2007-09-22
alright. will do.

also, i installed ubuntu onto my laptop hard drive with another computer, a desktop actually.




would it help me in any way to load the linux driver for my ati radeon onto the hard drive from the desktop and then put the hard drive back into my notebook with the driver for the graphics card on it?

---

### Post by leo_rockway on 2007-09-22
still same thread... why didn't you read that whole thread?
[http://ubuntuforums.org/showthread.php?t=518469](http://ubuntuforums.org/showthread.php?t=518469)

particularly this two posts:
[http://ubuntuforums.org/showpost.php?p=3142268&postcount=22](http://ubuntuforums.org/showpost.php?p=3142268&postcount=22)
[http://ubuntuforums.org/showpost.php?p=3142374&postcount=23](http://ubuntuforums.org/showpost.php?p=3142374&postcount=23)

i did this a long time ago so i don't remember, i was online when i did it but i'm not sure if that was necessary or not (i think it was necessary).

you may want to read  this post as well:
[http://ubuntuforums.org/showpost.php?p=3147447&postcount=25](http://ubuntuforums.org/showpost.php?p=3147447&postcount=25)

---

### Post by leo_rockway on 2007-09-22
> **Soarer said:**
> Best install it then.

System>Administration>Synaptic Package Manager (put in your password)

Search for xorg-driver-fglrx, mark for install.

Then see if you get any other errors.
he can't load X, therefore he can't access synaptic.

---

### Post by lonelyxpeople on 2007-09-22
theres the thing,
im not connected to the internet on the notebook,


so to answer my question, could it help me to just load the ati driver onto the hard drive?

---

### Post by leo_rockway on 2007-09-22
> **lonelyxpeople said:**
> 
so to answer my question, could it help me to just load the ati driver onto the hard drive?

if you mean the ati driver from ati.com, then no, it won't help. the ati drivers from ati.com have a graphical installation. 

if you have another linux machine you can download the package i told you to get (w/o installing) copy it to that other hard drive you have and then install it in your laptop.

---

### Post by lonelyxpeople on 2007-09-22
where do i find those packages?

im new to linux and thus need a bit of a help with a lot of stuff.

---

### Post by leo_rockway on 2007-09-22
google is your friend.

[http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/xorg-driver-fglrx_7.1.0-8.34.8+2.6.20.5-16.29_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/xorg-driver-fglrx_7.1.0-8.34.8+2.6.20.5-16.29_i386.deb)

you may need more packages if dependencies are not met. you may want to read this as well: [http://packages.ubuntu.com/feisty/misc/xorg-driver-fglrx](http://packages.ubuntu.com/feisty/misc/xorg-driver-fglrx)

search the web to see how to install deb packages.

---

### Post by lonelyxpeople on 2007-09-22
alright, so i somehow connect to the internet and download those files then install them without the gui?

---

### Post by leo_rockway on 2007-09-22
Exactly.

EDIT:What do  you mean "somehow connect"? You said you could download from another comp (the one you're using to post would help)

You could also try:
```
sudo apt-get update
```
before trying 
```
sudo apt-get install xorg-driver-fglrx
```

then you may not even need internet, you just install from the Live CD.

---

### Post by lonelyxpeople on 2007-09-22
alright. ill try that.


so do i boot from the live cd or just have it in the drive?



and as a side note,
the desktop doesnt have internet as i get wifi from a neighbor that i split the bill with, and the computers adapter isnt strong enough.

we're changing the router soon.

**edit:**
okay, i was running on too little sleep last night.
i reinstalled a fresh copy of ubuntu, mainly because im not sure of what changes i really did, and im going to install those .deb packages now.
i am assuming that those would fix my problem, correct?

---

### Post by leo_rockway on 2007-09-22
installing xorg-driver-fglrx and modifying xorg.conf as explained before will solve your gui problem.

---

### Post by lonelyxpeople on 2007-09-22
alright, i installed the packages and modified the file you told me to.

i ran into another problem, idk if its a noob error, but when entering in "sudo aticonfig --initial" and "sudo aticonfig --overlay-type=Xv", i get an error message saying "Parse error on line 145 of section ServerFlags in file /etc/X11/xorg.conf "off"" is not a valid keyword in this section"





ive checked and checked and checked again to ensure i've done everything right, but when "off" is added to the xorg.conf, is it supposed to be "Off"(i know linux is case sensitive)?

if not, what do i do?

**edit:**haha i was wrong, i forgot one set of quotation marks. my bad.

my gui is now running. thanks a million man. now, can you help me get wifi and whatnot loaded, or links to where i can get it working?

**edit *again:*** sorry, forgot to check before i spoke. :p im running ubuntu fine, am i missing any codecs, drivers, etc that i'll have to download?

---

### Post by leo_rockway on 2007-09-23
you're missing propietary codecs. if you want/need them, just do  a websearch.
java, mp3, dvd, w32 formats, etc, are not included by default because they are not free (as in freedom). they are free of charge to use, tho and installing them is really easy. automatix and easyubuntu are available for all that but i don't recommend using them (some people had great results with them, some others had serious problems. if you one of them and have a problem, it is usually very hard to solve them)

if you want, you can also get the latest graphic drivers from ati.com.

open another thread if you need to ask another question, and mark this one as solved.

---

