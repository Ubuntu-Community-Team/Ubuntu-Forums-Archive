---
title: "Dell Optiplex GX270"
date: 2014-03-31
forum: Installation &amp; Upgrades
---

### Post by Matthew_H. on 2014-03-31
Hello all,

I'm trying to breath some life back into an old Dell Optiplex GX270. Since this thing is so old it only has a CD-ROM drive, I used the 13.10 mini CD to install. The install completed, and brought me to a command prompt. I attempted "startx" but that errored out.  I found via google that the GUI was apparently missing, so I installed it using:

```
sudo apt-get install ubuntu-desktop
```

That did it's thing, and afterwards spat me back out to the command prompt. I issued "startx" again, and the GUI started... sortof.  I now have a pretty wallpaper and a mouse arrow, but nothing else.  No icons, no menus, nothing.

Any suggestions?

Thank you!

---

### Post by 23dornot23d on 2014-03-31
How much space do you have to install things to ( DF ) lowercase in a terminal should show that ......

df

 .... and if you try to update and add LXDE - can you get a graphical user interface ...... lightdm is the login manager
which will make it simple to choose a desktop environment to work from .........

```


sudo apt-get update
sudo apt-get install aptitude
sudo aptitude update
sudo aptitude install lxde
sudo aptitude install lightdm


```

The first thing I do is when messing with different systems is to have a light desktop to fall back to
also the light ones tend to work best when everything else stops. ( the others I use are E17 and awesome )

But LXDE should give you a easy start point to work from with a gui - that will make things easier to report back
what is happening .........

---

### Post by sudodus on 2014-03-31
The computer is old and has probably not enough horsepower and or memory (RAM) for standard Ubuntu. But if you install ***xubuntu-desktop*** which is medium-light or ***lubuntu-desktop*** which is ultra-light, you will probably have better luck. You can install several desktops into the same installed system (just for testing), and select what to use at the login screen. Click on the round symbol according to the attached picture.

If there is old Intel graphics you might also need UXA acceleration, which is described in the following link (in the first post)

[Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

-o-

After you find which desktop environment that works best for you, reinstall the system and only that particular desktop, for example

```
sudo apt-get install lubuntu-desktop
```

---

### Post by Matthew_H. on 2014-03-31
Thank you for the quick responses.  I'll give your suggestions a try.  

It is an old system.  It's running a 2Ghz Pentium 4 with 512M of RAM.  40GB hard drive.  It was running WinXP Pro, but with support dropping and it not being economically viable to upgrade hardware to support Win7 I was hoping to get some more utility from it with Ubuntu.  The ultimate goal is to re-purpose it to be an OpenFire server for my wife's office (about 8 users).

---

### Post by sudodus on 2014-03-31
I can say directly, that you should go for*** Lubuntu 13.10*** with those computer specs, or possibly a server running in ***text mode or with a very light window manager***, for example fluxbox (instead of a full desktop environment) so that there will be more horsepower and memory for the services.

---

### Post by 23dornot23d on 2014-03-31
I agree ...... something light - lubuntu is good ...... and setting up servers is not my thing - so will leave this for now ..... best of luck

* ( By the way this does not mean I am not watching the thread - so if you do get any problems with the commands I have already supplied 
     I will still be around to sort out any problems with them ........ not abanodoning this - but am leaving it in the hands of people that deal more
     used to the issues you want to adress )

I did also have a hunt around too on You-tube for servers and Lubuntu ..... some interesting step by steps but in an older version of lubuntu and in 
virtual box ( might be of interest ) ....... [http://youtu.be/Lenp_T_tbOI](http://youtu.be/Lenp_T_tbOI)

---

### Post by Matthew_H. on 2014-03-31
Alright, here's an update. I'm posting from the old dino now.  I downloaded the 32bit lubuntu 13.10 CD image and started over with that. So now I have a working system and it's running much better than it did with WinXP.

Now, onto figuring out how to setup remote desktop and configuring OpenFire.

Thank you for your assitance.  It's been a while since I did anything with Linux (my wife is too used to Windows to change).  You guys have reminded me how great the Linux community is.  Thank you!

---

### Post by 23dornot23d on 2014-04-01
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

Networks ..... etc ...... 

or

Servers ......

[http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339)

______________________________

You may be better posting in the section above for things that are related to networks or servers as the people who deal with them all the time

will be scouring them rather than here to give answers ........

Each question then will get addressed better if it has its own thread ...... one problem at a time is the way this thing tends to work best

for both the user and the people trying to solve the problems ....... 

( but I have given one link I found below - not that it is the best answer you will get - but it may lead to searching for other things or giving a
 
start point on a paper trail - best of luck )

_____________

I had a search around for answers - this is one I found on remote desktops ....... as someone did find a bug in it ..... 

but also posted their own solution to it.

[http://www.techzim.co.zw/2013/12/solving-ubuntu-13-10s-remote-desktop-windows-bug/](http://www.techzim.co.zw/2013/12/solving-ubuntu-13-10s-remote-desktop-windows-bug/)

---

