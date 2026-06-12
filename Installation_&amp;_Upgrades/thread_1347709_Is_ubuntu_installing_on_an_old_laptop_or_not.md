---
title: "Is ubuntu installing on an old laptop or not?"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by trampintransit2 on 2009-12-06
i tried a full install of 9.04 from a known good disc, onto a TINY A440 pentium 111 based laptop ( rebadged FIC notebook). the ubuntu symbol flashed up, there is much noise and gnashing of teeth, the progress bar under the ubuntu symbol moves to the far right, there is lots of harddisc noise for about 10mins accompanied by a black screen, the silence, black screen and the laptop appears to go into sleep mode or something. 
At this point, pressing the release button on the cd tray will not release the cd, the power light is on but nothing else ids happening. press the power switch twice, the cd releaes and it gives the option of starting windows or ubuntu. opt to open ubuntu, much noise, black screen nothing else. Opt to open windows and it opens and there on the disc is a folder called ubuntu (711mb)
Having deleted the folder called ubuntu from windows, and restarting the 'puter still gives me an option to start windows or ubuntu. If i start windows and reinsert the cd and go for the install without altering your computer option it starts to 'extract files from D:\' (only after ' uninstalling ubuntu' from the control panel in windows.
it then extracts, or appears to extract fully. The 'installing CD boot helper' window runs to end, spits out the disc, asks to reboot. hit reboot, windows shuts down. New boot screen, choose ubuntu, the ubuntu symbol appears for a few minutes then black screen and silence!

I feel like its installing but just got no graphics, as if its there but i just cant see it?

---

### Post by whoop on 2009-12-06
How much memory does the laptop have?

---

### Post by darkod on 2009-12-06
Did you try running it from the cd by booting the cd and selecting Try Ubuntu option? It might have problems with video driver or something. If it runs fine with Try ubuntu most probably it will run fine after it's installed.
And also what you are talking about is wubi installation from within windows. Not ubuntu side-by-side install. It makes a difference. If the laptop is old it might not be able to install wubi like that inside windows. A side-by-side install might work.
Also ubuntu has a derivative called Xubuntu for older computer with less cpu power and ram.
Consider the options and you need to make a choice how and what to install.

---

### Post by deathbyswiftwind on 2009-12-06
Id recommend Xubuntu for that laptop. It cuts out alot of the extra bs and provides a nice lightweight os. Not as pretty but still as good. And as someone stated I wouldnt use wubi to try and install it due to lack of resouces. With the ubuntu installer these days its just as easy a windows install.

---

### Post by wilee-nilee on 2009-12-06
Your description is rather confusing. It appears that your trying to install 9.10 inside of a Windows setup with a wubi install. This computer has a 1 gig chip and 256 ram stock is this correct?

So if any of this is true tell us the Windows distribution to start with and confirm the computer specs, also how old is the hard drive.

---

### Post by trampintransit2 on 2009-12-06
ITs a pentium 111 800mhz with only 128 ram ( more in the post) running a stripped down xp reasonably happily
I tried installing from within windows.....looked like it installed. looked completely happy then just died. tried install from cd, just got loads of cd / hdd noise, and a black screen. Tried 'try ubuntu without changing you computer' option....same result as the full install option.....feels like its installing but just not loading a graphics driver??

---

### Post by trampintransit2 on 2009-12-06
BTW..i'm afraid ive no idea what is meant by wubi. sorry

---

### Post by trampintransit2 on 2009-12-06
the demo option inside windows does the same thing

just tried Xubuntu.....same results!!!!!

---

### Post by darkod on 2009-12-06
With that low spec I think you might be better off trying Xubuntu:
[http://cdimage.ubuntu.com/xubuntu/releases/9.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/9.10/release/)

The options are the same, you have option first to Try it and you better do that first and see if it runs OK.

Wubi is the wubi.exe file used to install ubuntu inside windows. The one that you double click to start the install in windows. But there will be difference in the installed system compared to the other type of install. Otherwise the install should be booting from the cd and selecting Install Ubuntu.

---

### Post by trampintransit2 on 2009-12-06
just tried xubuntu...behaves in exactly the same way!!!! I am at a loss!!!!

BTW ..it loads Puppy ok...but i cant deal with puppy..i'm not smart enough for it.... i just dont understand how to use it really

---

### Post by wilee-nilee on 2009-12-06
There are a bunch of versions of puppy some are more user friendly then others.
[http://puppylinux.org/wikka/Puplets?show_comments=1](http://puppylinux.org/wikka/Puplets?show_comments=1)

---

### Post by audiomick on 2009-12-06
I think 128MB of RAM is way under what you need for Ubuntu.

---

### Post by trampintransit2 on 2009-12-08
bump

---

### Post by trampintransit2 on 2009-12-08
i agree audiomick...i've got another 256 in the post. Thing is that isn't an explanation as to why it just wont install properly...damn it, even XP is working on this machine. I think ubuntu is the right OS for this laptop once i've got more ram in it....if only i can get it to install....if feel like nobody has an idea about why it's not installing..or at least not APPEARING to install!! If you guys don't know, i'm WAY too dim to figure it out!!!

---

### Post by MelDJ on 2009-12-08
see this: [http://www.delilinux.de/](http://www.delilinux.de/)
hope it helps

---

### Post by NCLI on 2009-12-08
I think you need the [Alternate Install CD]("ftp://ftp.klid.dk/ubuntu-cd/karmic/ubuntu-9.10-alternate-i386.iso"). It uses a text-based installer to minimize the otherwise high RAM requirements for the installation.

---

### Post by trampintransit2 on 2009-12-12
installed more ram....now has 640mb....tried ubuntu again and xubuntu....same result.....this is mad!!
what can be happening??

---

### Post by trampintransit2 on 2009-12-16
I,ve now tried ubuntu 9.04, 8.10, alternate text based install and xubuntu, but still only XP or Puppy will stick on the computer.....what about the 'no graphics driver to match the hardware ' theory??

---

