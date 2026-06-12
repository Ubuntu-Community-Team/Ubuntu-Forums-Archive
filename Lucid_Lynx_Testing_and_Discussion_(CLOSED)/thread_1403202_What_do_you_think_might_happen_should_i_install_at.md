---
title: "What do you think might happen should i install ati driver?"
date: 2010-02-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-02-10
ati have this driver for my screen card:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

i didn't have much luck with it when i used 8.10 but how about now?

without a driver for my card i can do much here not even view movies in my tv and compiz doesn't fully work and etc.

thanks in advance.

---

### Post by RAOF on 2010-02-10
It will fail to work.  There are currently no fglrx drivers that support Lucid's X server.

---

### Post by aviramof on 2010-02-10
thank you very much i'm hopping that your working on it because at the moment i can't even use ubuntu to see movies and etc in my tv for some reason the option via display make my screen looks pink and shut down process make her green maybe it becase she's pal not ntsc who knows it toshiba lcd 720p he recognize it as toshiba america info system  inc 95 also i have several more problems like numbers pad don't work maybe because my keyboard is right to left hebrew.

and one small thing something strange has happen to my bottom panel he no longer display minimize windows i think it also had something to do with locilization problem because 
the minimize windows were on the left not the right but i'm fine using alt tab any way.

and by the way have you ever consider adding basic auto arrange option to ubuntu?

just to sort out the icons in the desktop and folders nothing major.

---

### Post by vade on 2010-02-10
> **aviramof said:**
> thank you very much i'm hopping that your working on it
Only ati can work on their closed source.

---

### Post by aviramof on 2010-02-10
maybe but they do work with the ubuntu community a quoate from an email they sent me:
 
> Although we have driver for Linux posted on the AMD website, we do not troubleshoot driver or multimedia issues in Linux directly. We work closely with the Linux community to provide support options. On our website we do have link to several Linux support sites that may help you. I have included the link below to this website. 
All Linux help is self help online.
 
which mean that someone must have any idea as to the existent of a driver or a work in progress on one.

---

### Post by [h2o] on 2010-02-10
> **aviramof said:**
> maybe but they do work with the ubuntu community a quoate from an email they sent me:
 

 
which mean that someone must have any idea as to the existent of a driver or a work in progress on one.

If ATI does not compile their proprietary binary only driver for the specific X-server in Lucid, then it won't work. I doubt ATI will release one until there are (more) distributions using the new X-server.  Current stable Ubuntu (9.10) has a working binary ATI driver.

You can't demand that a development version of Ubuntu should run proprietary software developed by others.

And I believe the open source ATI driver should be good enough for Compiz now anyway.

---

### Post by Seren on 2010-02-10
> **aviramof said:**
> ati have this driver for my screen card:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

i didn't have much luck with it when i used 8.10 but how about now?

without a driver for my card i can do much here not even view movies in my tv and compiz doesn't fully work and etc.

thanks in advance.

[http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)

This is basically the status of the radeon driver in Lucid.

I don't know what kind of card you have but you only need the closed source driver for the following reasons :
1. you are a gamer and you need the best possible framerate
2. you have a card from the 5xxx Generation (aka Evergreen) which is not yet supported by the open source driver 


There might be some other cases that I am not thinking of (power management, 3D modeling or other 3D demanding applications), but as said earlier, the open source ati driver should be sufficient for 2D and compositing, and some light 3D use like Google Earth.

---

### Post by aviramof on 2010-02-10
and does this ati open source come with the systyem or that i need to install it manually because my problem is that i don't have proper dual view what i mean is that i can see my screen in the tv but it's pink and if i shutdown the computer while the tv is on and dual view is active then the screen goes 
green with ubuntu in the middle and that is why i need this driver not for games just to be able to watch
movies and to have to switch to seven to do that all the time.

---

### Post by aviramof on 2010-02-10
what is the command to install it i checkd with 
lspci -nn | grep VGA

and got this:
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV635 PRO AGP [Radeon HD 3650] [1002:9596]

so it should be ok but i have problems with synaptic now

[http://ubuntuforums.org/showthread.php?t=1403554](http://ubuntuforums.org/showthread.php?t=1403554)

---

### Post by zika on 2010-02-11
Did You try: [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") ?
I'm using LL with xorg-edgers on ATI Radeon HD 3650 512M...For several days I was driving it with out-of-the-box LL drivers and everything worked...
OK, I have problems with freezes when using KMS, but that is another subject, covered with separate thread...

---

### Post by aviramof on 2010-02-11
what exceclly do i need to download and install from this site?


as far as i can see in symantic i already have 2.4.17 intel1,nouveau1,radeon1,libdrm1 installed and and basicly everything is fine but i can't see the tv screen properly 
it show me the desktop background as pink the  shut down process as green screen and i can't use all of compiz options.

thanks in advance.

---

### Post by zika on 2010-02-11
> **aviramof said:**
> what exceclly do i need to download and install from this site?


as far as i can see in symantic i already have 2.4.17 intel1,nouveau1,radeon1,libdrm1 installed and and basicly everything is fine but i can't see the tv screen properly 
it show me the desktop background as pink the  shut down process as green screen and i can't use all of compiz options.

thanks in advance.Just if You're sure You want to use that ppa, add that ppa to Your Soruces list and update/upgrade...
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo aptitude update
sudo aptitude upgrade
```That's it...
If You choose to revert to a state before that ppa was introduced to Your system, just use ppa-purge script on their page...
```
ppa-purge xorg-edgers/ppa
```

---

### Post by cariboo on 2010-02-11
@aviramof, Please stop creating threads asking the same questions several times. Remember everyone here is a volunteer, If you don't get an answer to your question right away, please give it time. The person that may be able to answer your question may not have seen it yet.

---

### Post by VMC on 2010-02-11
> **cariboo907 said:**
> @aviramof, Please stop creating threads asking the same questions several times. Remember everyone here is a volunteer, If you don't get an answer to your question right away, please give it time. The person that may be able to answer your question may not have seen it yet.

I stopped trying to help him for this very fact. Who knows what and if an answer was supplied to him in another one of his topics. 

Someone tries to help and he replies never mind, I re-installed. [Case in point]("http://ubuntuforums.org/showthread.php?t=1404010").

---

### Post by aviramof on 2010-02-12
trust me bro i know excelly what is going on in any of my thread and i would not have open a new thread about something that i already got an answear to.

you can check and see press search then advance search then search Search by User Name and enter aviramof.

and you would also see that i didn't get a lot of replies even in old threads.

@[zika]("http://ubuntuforums.org/member.php?u=690937") thank you very much for your help it might have helped compiz and etc but i still see the tv screen in pink or solorize if you want to call it like this and it's very strange problem.

---

