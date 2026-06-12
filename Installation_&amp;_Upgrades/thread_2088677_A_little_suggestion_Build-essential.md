---
title: "A little suggestion Build-essential"
date: 2012-11-27
forum: Installation &amp; Upgrades
---

### Post by David Singer on 2012-11-27
I am not new to computing but I am new to ubuntu Linux.

For many days I have been wrestling with upgrading my ASUS 901 from Win XP to Ubuntu 12.10.

Its not been easy, I need to install driver for my Turkcell VINN Modem to be able to get the thing on-line.

read lots of threads and tried lots of suggestions but the VINN remains out of the loop, driver is loaded says the OS but its not talking to the modem . . . . 

I need Build-Essentials (I think) to enable me to do this or at least run WINE so I can access the VINN and run the window driver - maybe.  BUT build-essentials might as well be on another planet, this key item is missing.

Wouldn't it be nice if Build essential was loaded by default when installing the OS?

As it is I have a bootable USB of the 12.10 operating system but no sign of build-essentials.

Yes I downloaded the WINE 1.5.11 .bz2 file but I cant use it, a serious omission in my opinion.

does anyone have a solution?:)

---

### Post by mlentink on 2012-11-27
Go to Ubuntu Software Center, type "wine" in the searchbox, click on it and have fun

You can also type 'build-essentials' in that same searchbox.

---

### Post by David Singer on 2012-11-27
> **mlentink said:**
> Go to Ubuntu Software Center, type "wine" in the searchbox, click on it and have fun

You can also type 'build-essentials' in that same searchbox.

Yes did that 

in both cases the system reports "no items match"

---

### Post by QIII on 2012-11-27
It's 
```
build-essential
```
not```
build-essentials
```

In the terminal, do

```
sudo apt-get install build-essential
```

It is not included by default because it is not something most people need by default.

---

### Post by David Singer on 2012-11-27
yes its Build-essential I did notice that - see thread title

sudo apt-get install build-essential

reports errors: invalid operation

yes I am running it from root, in fact I've run it from everywhere I can get.

The search in The Software Centre finds anything that starts with a letter, so  shows 1415 items, Build or build shows 27 technical items, build- shows none as does build-e and build e so I conclude build essential or build-essential isn't there.

ALSO in the software centre there are lots of apps that are green ticked and reported as installed, for example FreeCell Solitare thinks it was installed on 17-10-2012 over a month before I loaded the OS, so, if its installed it should show up as a short-cut on the left hand side of the screen? Yes or No?? - its not there along with all the other apps that are green ticked.  So how do I find these missing installed apps? 

SO do I have a totally screwed up installation -  I used this from the UBUNTU website:

ubuntu-12.10-desktop-i386.iso

---

### Post by oldos2er on 2012-11-27
Windows drivers won't run in Wine. 

Maybe something here will help? [http://forum.ubuntu-tr.net/index.php?topic=31806.0](http://forum.ubuntu-tr.net/index.php?topic=31806.0)

---

### Post by David Singer on 2012-11-27
> **oldos2er said:**
> Windows drivers won't run in Wine. 

Maybe something here will help? [http://forum.ubuntu-tr.net/index.php?topic=31806.0](http://forum.ubuntu-tr.net/index.php?topic=31806.0)

Many thanks for that I will use it, but I am now of the opinion that my 12.10 system is missing the installer I have just reinstalled it AGAIN and this time it gives an error - apt package not found and installer third party software failed to install, it asks me to report a bug, then says don't - I'm confused.  I am on a boat in Turkey with very little in the way of infrastructure, a couple of old pcs and an even older brain.  I will wait until I return to the UK and have another go with a better broadband connection.  I have to say this reminds me of the early days of Dr Dos BASIC and NT4, we often couldn't make it work and didn't know if there was a fault with the hardware, software or the user, that's about where I am with UBUNTU Linux, this is the first implementation I have seen, I have no way of knowing if its OK. . .

A gin and tonic beckons

happy days

EDIT Just tried to download 11.10 dialogue says 3 DAYS!!! for 695MB I'll have another G & T

---

### Post by Sunon on 2012-11-27
Even booting off of the live disto (DVD, USB, etc) you can install packages from the terminal and run what you need.

---

### Post by oldos2er on 2012-11-27
> **David Singer said:**
> I have just reinstalled it AGAIN and this time it gives an error - apt package not found and installer third party software failed to install, it asks me to report a bug, then says don't - I'm confused. 

We'd need to see the terminal output and/or exact error message to give you a good answer.

---

### Post by David Singer on 2012-11-28
> **Sunon said:**
> Even booting off of the live disto (DVD, USB, etc) you can install packages from the terminal and run what you need.

Really? with no installer?  Please tell me how

---

