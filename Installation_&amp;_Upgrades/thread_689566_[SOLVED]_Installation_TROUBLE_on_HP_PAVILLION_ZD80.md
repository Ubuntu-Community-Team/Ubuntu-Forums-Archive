---
title: "[SOLVED] Installation TROUBLE on HP PAVILLION ZD8000"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by pmshirey on 2008-02-06
Ok. this is very weird. I just downloaded the regular installation for Linux, and on the Live CD, the screen just goes completely blank, and on the alternate disk, the screen starts alternating from white to black.:mad:

---

### Post by jan quark on 2008-02-06
what are your specs?

might be a graphic card or monitor compatibility issue...

---

### Post by pmshirey on 2008-02-06
Linux has been on this computer several times, let me get my specs.

---

### Post by pmshirey on 2008-02-06
Here are my specs, Intel Pentium 4 Processor, ATI Mobility Radeon X600 graphics, 1gb ram, 80gb hardrive, CD/DVD Writable Re Writable.

---

### Post by jan quark on 2008-02-06
if you get to the options where you can choose whether to install or do a memory test

you can try pressing f6 and remove the word quiet at the end of the boot options, and change splash to nosplash-add noapic irqpoll noirqdebug

or you do not get to this stage, perhaps the CD was burned too fast, and the integrity of it is flawed. Do you have done a midsum check?

I must guess because I don't know how you have burned your CD and if you already have installed ubuntu successfully using this CD.

I encounter sometimes the same issues, but than I burn the cd image once more, perhaps even slower and it usually works then.

Weird problem you have---

---

### Post by pmshirey on 2008-02-06
I'm still getting this problem, I figured out my error, i get an error that says cannot allocate system 9 (or something like that) I put a 64bit amd-intel disk in, and that still gives this same error.

---

### Post by pmshirey on 2008-02-06
The problem was the screen resolution. My dad switched the resolution to 800 x 600. Thanks for all the help.

---

### Post by Carrrl on 2008-02-09
I finally managed to get through the entire installation part on a zd8000.
I used the regular 7.10 CD, and at the start pushed F6 and inserted 
vga=771 noapic nolapic
between the rest of the commands on the command line.
This installation failed when I tried it in the evening (warm computer, computer just shuts off at 94% installation progress), but succeeded when I did it in the morning (cold computer, propped up on books for better air flow).

So I definitely think ONE of the problems with the zd8000 is overheating.

I have not gone further than this, so I don't know about the graphics and other stuf yet.

---

### Post by Carrrl on 2008-02-09
Well I'll be darned, the computer actually starts up with graphics on the first attempt. When I try to solve the problem with proprietary drivers that Ubuntu kindly tells me about, the computer just quits (overheating again I guess)

---

### Post by duervo on 2008-03-08
It's not a design issue with your zd8000 that's causing it to overheat.  It's most likely caused by dirt and dust restricting airflow of the cooling fans, and restricting ability of any heatsinks to dissipate heat properly.

HP's support website has some docs that tell how to disassemble the zd8000 so that you clean the fans and heatsinks.  I suggest you do so when you get a chance.

Keep in mind, though, that since your zd8000 has already overheated more than once, there is a possibilty that some components may have already been damage by the heat.

(I have had my zd8000 since June, 2005, and it has been rock solid the entire time, which is more than I can say for a Dell Inspiron I once owned, and a Lenovo Thinkpad T60 I currently use for work.)

---

