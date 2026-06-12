---
title: "Can't Boot or even load Ubuntu Dell Latitude 10.04"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by Konky_Chelsea on 2010-08-13
Got a free CD with Ubuntu on it using the Ship-it.

The disc is fine I have installed using the CD on an Acer Laptop without any trouble what so ever.  However now I need to install it on a Dell Latitude D505.

It was detected and started the disc and show Ubuntu with the five dots loading screen.  And then it goes black, with the laptop on.  The menu with options like Install, defect test etc. can't be seen.

In response to this I installed it inside Windows and that seemed to be ok, so I restarted the laptop and selected Ubuntu from the boot menu and does the dot loading screen and then black.

I have searched Google and it is just threads that end up dead.  I know I should take a hint, but is there any solution?

Cheers in advance. :KS

---

### Post by Rubi1200 on 2010-08-13
Hi,
please post the specs. for the Dell Latitude D505, especially the graphics card.

---

### Post by Konky_Chelsea on 2010-08-13
Intel 82852/82855 GM/GME Grpahics Controller.
40 GB Hard Drive.
1GB RAM

---

### Post by Rubi1200 on 2010-08-13
> **Konky_Chelsea said:**
> Intel 82852/82855 GM/GME Grpahics Controller

Take a look here for possible fixes/workarounds:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

To get you started:
[http://ubuntuforums.org/showpost.php?p=9239795&postcount=19](http://ubuntuforums.org/showpost.php?p=9239795&postcount=19)

Hope this helps.

---

### Post by Konky_Chelsea on 2010-08-13
Thanks, but I can't even get into a log menu, let alone get into Terminal.

Thanks again.

---

### Post by kiridude on 2010-08-13
Maybe you're cd is damaged. Try it in another computer to see if it works there.

---

### Post by Konky_Chelsea on 2010-08-13
The CD is fine.  Tried the i915.modeset=1 and done a lot of CLI inits.

It's a puzzling one, might just stick with Acers, if there is no fix.

---

### Post by FoxForceFive on 2010-08-14
Exactly the same problem here.

Dell Latitude D505, gets to the dot loading screen, then just blank screen. Left it for ages but nothing. 

Tried netbook version & full desktop version, multiple copies, both usb & cd.

---

### Post by paskyle on 2010-08-16
I'm having exactly the same problem:  dell latitude D505, 1.25GB RAM. After the dot screen, something flashes very briefly and then - nothing. Says the display adapter is an Intel 82852/82855 GM/GME.  Using 10.4 from an USB thumb drive.

---

### Post by Konky_Chelsea on 2010-09-02
I don't use it as my main laptop (by far not), I got in 2nd hand anyway, my proof adds to my theory that no one should ever by a Dell or Fujisu Simens computers.

---

### Post by swapnerd on 2010-09-06
I tried to install Ubuntu Netbook 10.04 on my Dell Latitude D505 and had the same problem with a blank screen after a short while. Using the i915.modeset=1 boot option worked for me though and I now have a working system. (My next problem is getting DVDs to play as X seems to crash - still investigating this one).

---

### Post by swapnerd on 2010-09-07
Update: For anyone interested, I have found that reverting back to kernel version 2.6.31 has fixed my being unable to play DVDs.

---

