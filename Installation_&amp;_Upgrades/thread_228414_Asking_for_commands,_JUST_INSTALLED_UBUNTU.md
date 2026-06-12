---
title: "Asking for commands, JUST INSTALLED UBUNTU"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by naomiangela on 2006-08-03
I've just finished installing Ubunto, and I've gotten to the part where the cd ejects and it reboots..Except it gave me a black screen asking for sudo commands?? No idea, but I can't turn off my computer and I dont know how to get outt've it. Please help:-k

---

### Post by ciscosurfer on 2006-08-03
Can you be more specific?  If the screen is just black (blank), try hitting Enter to see what happens.

---

### Post by naomiangela on 2006-08-03
No, its not plain black. i'm getting little white words, saying things like "root@dunno:~$" and when i press enter the same thing comes up.

---

### Post by kriding on 2006-08-03
> **naomiangela said:**
> No, its not plain black. i'm getting little white words, saying things like "root@dunno:~$" and when i press enter the same thing comes up.

it sounds like you have installed the server version. try this:

```
sudo aptitude update
sudo aptitude gnome-desktop
```


you can substitue gnome-desktop with kde-desktop if you prefere

---

### Post by naomiangela on 2006-08-03
i installed the server version? ah no, does this mean ive gotta re-install all this all over again? im new to linux, and it took me a bit to figure out how to burn the thing to a disk and whatnot. anyway, ive typed in the commands u told me, and a bunch of writing comes up, the end of one says 'this apitude does not have super cow powers" i'd laugh at that if this wasnt all being frusturating.

---

### Post by naomiangela on 2006-08-03
ive got another question here tho, im gonna download the desktop version instead of the server one, so after i put it on a cd and everything and try n get it to boot off my comp, how do i get rid of the black screen thingy so i can re-install, seeing as its not letting me shutdown.

---

### Post by beniwtv on 2006-08-03
> **naomiangela said:**
> ive got another question here tho, im gonna download the desktop version instead of the server one, so after i put it on a cd and everything and try n get it to boot off my comp, how do i get rid of the black screen thingy so i can re-install, seeing as its not letting me shutdown.

If you install the Desktop version, you don't get a blank screen. You get the desktop. Only in remote cases this fails. But there would be a solution, too.

So try the Desktop version, it should come up with the desktop. :wink:

---

### Post by naomiangela on 2006-08-03
yeah i just wished i realized that a couple of hours ago before i was gettin myself into this mess, lol. but id rather go thru all this then cough up the hundred bucks to install xp.

---

### Post by cantormath on 2006-08-03
> **naomiangela said:**
> ive got another question here tho, im gonna download the desktop version instead of the server one, so after i put it on a cd and everything and try n get it to boot off my comp, how do i get rid of the black screen thingy so i can re-install, seeing as its not letting me shutdown.

ah, you should just be able to open the cd drive, put the desktop cd in then hold down the power button until the machine turns off.  Then, when you are ready to install again, with the DESKTOP CD you can just turn the machine on again install ubuntu.  

if you dont want to reinstall just turn on machine
and type this here.
root@dunno:~$ sudo apt update
root@dunno:~$ sudo apt gnome-desktop

If you have trouble after that, let us know, or install Desktop CD ;)

---

### Post by naomiangela on 2006-08-03
yeah ill def do the 1st thing u said in the 3 hrs from now when i get to that point. ahahaa good thing i have nothing impt to do tommorow, seeing as ill prob be up all nite working this thing out.

---

### Post by Viruk on 2006-08-03
I had the same problem (I definately installed from the alternate desktop version) but just ended up going to a "command type" logon (appologies if thats not the correct terminology).

One thing I think is worth mentioning is that when I installed it went into a low memory mode, so I dont know if that had anything to do with it. 

I overcame this by logging in and using aptitude to add packages. A friend pointed me in this direction and installed a couple of packages, although Gnome didn't seem to install on the first attempt. I managed to use aptitude again afterwards and install Gnome and now it appears to be working. 

naomiangela - it might be worth checking which packages you have installed before doing a complete reinstall. 

I can point you in the right direction, log in to the terminal/command prompt (someone correct me on the terminology please!) then type aptitude. Use the on-screen help (it tells you what keys to hit for certain actions) and make sure you have the Gnome package installed. Check the packages not installed list and select it from there.

Maybe someone can give some more detailed or decent instructions on doing this as I am a noob myself and just bumbled my way through this, so I'm probably not the best person to direct you on this.

---

### Post by FenrisAbraxas on 2006-08-03
> **cantormath said:**
> ah, you should just be able to open the cd drive, put the desktop cd in then hold down the power button until the machine turns off.  Then, when you are ready to install again, with the DESKTOP CD you can just turn the machine on again install ubuntu.  

if you dont want to reinstall just turn on machine
and type this here.
root@dunno:~$ sudo apt update
root@dunno:~$ sudo apt gnome-desktop

If you have trouble after that, let us know, or install Desktop CD ;)

Just a little question.... if you are root why do you have to type sudo? isn't useless? :S i guess you guys are sudo addicts :S

Also the proper way of doing that is:

```

root@dunno:~$ apt-get update
root@dunno:~$ apt-get install gnome-desktop

```

---

### Post by FenrisAbraxas on 2006-08-03
> **Viruk said:**
> 
Maybe someone can give some more detailed or decent instructions on doing this as I am a noob myself and just bumbled my way through this, so I'm probably not the best person to direct you on this.

It's just a matter of typing:
```

root@localhost# aptitude update
root@localhost# aptitude install gnome-desktop 

```

---

### Post by kriding on 2006-08-03
> **FenrisAbraxas said:**
> Just a little question.... if you are root why do you have to type sudo? isn't useless? :S i guess you guys are sudo addicts :S


Force of habit I guess:D

---

### Post by FenrisAbraxas on 2006-08-04
> **kriding said:**
> Force of habit I guess:D

Hahahaha ok :P it's probably I'm a root addict and always use sudo -s -H :P instead of sudo command :P

(BTW im going to stop posting this things in this tread it'll probably just confuse the guy who started it :))

---

