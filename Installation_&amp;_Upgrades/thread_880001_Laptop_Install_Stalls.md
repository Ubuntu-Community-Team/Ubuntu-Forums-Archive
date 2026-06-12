---
title: "Laptop Install Stalls"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by yme on 2008-08-04
I have an Acer laptop on which I have had Ubuntu for a year or so. Recently it was getting so slow working with OpenOffice and the PDF viewer I decided to go for a complete install on a clean HD. 

I have done this a couple of times before and it always seems to get the speed up dramatically. Problem was this time it just won't run install.

I have burned a fresh Hoary CD but whatever option I choose on the menu it gets to installing the desktop and stalls (I see the heronand nothing else), I have checked and it says the CD is burned OK.

I am now running the memory test option but it has been running since Saturday and just keeps going. I don't understand whether the output it is giving is positive or not ...

---

### Post by spiderbatdad on 2008-08-04
It's definitely safe to quit the memory test now. You might try searching google for installing Ubuntu 8.04 on your model of Acer. Perhaps some boot options are needed. Have you tried to boot the live cd on another computer to see if  it will boot up?

---

### Post by yme on 2008-08-06
Someone suggested that I try the alternative CD so I downloaded that. Everything went OK until I got to 78% install and then it asked me 't change media.

This is weird as the download page explicitly says that the alternative CD is a CD not CDs!

---

### Post by wpshooter on 2008-08-06
Are you burning the image at 4x or less ?

Are you checking the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

P. S. - If you are burning image to CD instead of DVDs, make sure that the capacity of the CD media is not less than 700mb.

---

### Post by yme on 2008-08-06
Yes, it verified fine so I presume there is no problem. I always burn CDs at the lowest possible speed.

I might try a DVD now ...

---

### Post by wpshooter on 2008-08-06
May I ask why you are trying to install such an old version of Ubuntu.  I don't think Hoary is even suppored anymore !!!

---

### Post by ajfisherman on 2008-08-06
My laptop stall so i used a ide (laptop type) to usb and installed using another computer.  I dont thing older version of ubuntu auto-detect hardware changes so you may need to fix some stuff like xserver.

---

### Post by yme on 2008-08-07
8.04 is what I am trying to install. It is the latest available. 

I thought it was called Hoary? It has a Heron on the desktop anyway ...

---

### Post by yme on 2008-08-07
As to ide and via another computer that all sounds way too complicated. If it won't work from a straightforward CD why via another computer.

---

### Post by brukewilliams on 2008-08-07
Simple way to get around it, without having to debug it, is to install a second bootable windows copy on the hard disk, and boot off of that one. at least then you're able to access your data (provided it's not EFS encrypted) and keep on working while you try to find a technician who can solve your troubles. Does it also hang in safe mode? If so, that's more sticky. if not, then uninstall drivers & hardware one at a time working backwards chronologically, until you find the one that fritzed the system.

-------------------
Brukewilliams

[Partybets Free bet and Bonus code]("http://www.bettingchoice.co.uk/Partybets-bonus-free-bets.php")

---

### Post by Bucky Ball on 2008-08-07
> **yme said:**
> 8.04 is what I am trying to install. It is the latest available. 

I thought it was called Hoary? It has a Heron on the desktop anyway ...

Hardy Heron. :) Hoary is ancient.

---

### Post by yme on 2008-08-07
I don't have Windows and certainly don't think it is simple to start talking about a second install. 

The HD is blank as I made sure to backup to CDs. Never quite trust the new install not to wipe over it.

---

### Post by Bucky Ball on 2008-08-07
> **yme said:**
> The HD is blank as I made sure to backup to CDs. Never quite trust the new install not to wipe over it.

... or the user! lol ;)

If you keep notes and keep track of where everything is, there shouldn't be a problem, especially if you have an empty drive and no Windoze to confuse the issue.

Everything is in the planning, and it is a good idea to get out a piece of paper and make a plan before installing anything. Once you have your install in (which would include '/' '/home' and 'swap' partitions (probably) but can contain any partitions you choose to make which is where your plan comes in), take it from there. If you want another OS in there, your plan has, of course, covered this and you have an empty partition in the appropriate spot for it.

Good luck ...

---

