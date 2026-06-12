---
title: "Problem booting and installing"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by alex_foreman on 2010-07-17
hi guys

I recently did work experience for a company and they were binning a few of there pc's which i managed to grab, they weren't being binned because they were broken just because they were buying in new systems.

i am know trying to install ubuntu 10.04 on them but out of the 6 i have i have only managed to install it on one of them, 
on all of them i am putting the disk in, checking the boot options booting it from the cd, it loads up with human = keyboard i can then press space and load up that menu but then if i click to install or trial ubuntu it comes up with the ubuntu loading screen(with the 5 dots) and just does that for hours until i turn it of.
every now and again when i do it it comes up with the error "unable to mount file system"

*sorry forgot to put the specs up,
Intel 4 processor 2.8 ghz
memory between 513mb and 1.5 gb (can be adjusted if needs be, i have spares)
hardrive between 40 gig sata 80 gig sata and 250 gig the slower one(cant remember the name of it)
dvd multi cd drive(not sure of the speed)
(im not sure about the graphics card, how would I find out without a os on it?)
oh and i have tried booting with the nomodest option
any other details which I haven't mentioned i have forgotten:L

any help would be greatly appreciated

---

### Post by ezsit on 2010-07-17
I have the same problem, almost every third boot, the machine will just hang at the five dots splash screen and stay there as long as I wish to leave it. My solution was to go back to Ubuntu 9.10 and wait til October for the next release.

Then again, I just downloaded OpenSUSE 11.3 Gnome and it is really slick and solid. I might just switch this time. Ubuntu releases a broken LTS, I don't need this crappola.

---

### Post by YesWeCan on 2010-07-17
What are the text messages behind the splash screen saying?

---

### Post by alex_foreman on 2010-07-18
How do I see what it says?
(sorry nooby question)

---

### Post by alex_foreman on 2010-07-18
any help guys?

---

### Post by alex_foreman on 2010-07-18
is no one going to give me any advice?

---

### Post by davidmohammed on 2010-07-18
its probably a graphics issue - depending on what the graphics card - can I suggest you try pressing F6 from the live CD. At the bottom of the screen is your boot string - add one of the following immediately before "quiet splash --"

nomodeset
i915.modeset=1
i915.modeset=0

then select the option "try without installing".

---

