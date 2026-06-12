---
title: "New install Ubuntu 6.10 kernel panic not syncing"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by bamboozler on 2006-11-07
Hi everyone, first time Im trying to use linux and was advised to try out ubuntu
So I downloaded ubuntu 6.10 burnt it to disc, attempted to install to a PC...
Used boot from cd in bios, PC is a celeron 667 128Mb ram some sort of cheap graphics card (est 2-8mb) let me know if it matters and I will check for certain, and some small cheap hdd (approx 6Gb Id guess)

So boot from cd
Screen comes up, not sure what it says as its only there for a second and gone again, then monitor goes blank, after a while monitor says something like frequency not supported or something like that, a while longer and the screen comes back to life and on the screen are a heap of command lines and at the bottom it says

[17179569.480000] <0>kernel panic - not syncing: Attempted to kill the idle task!
[17179569.484000]

Does anyone know what this means or do I need to post the above few lines as well?
Any help would be appreciated as I have wanted to test out linux for a while now and have only just got around to downloading a distro and at least attempt to install it.

---

### Post by Cool Surfer on 2006-11-07
Whats ur screen resolution ...

---

### Post by bamboozler on 2006-11-07
Im not sure, I always thought screen resolution was set by the OS?

From what I can get off the monitor menu 
HF: 31.4Khz
VF:70.0Hz
user mode 4
preset mode 8

Its a "digital" (if thats even a brand?)
PCXBV-EY

Although Im not sure what the screen resolution would have to do with an installlation program?

---

### Post by Cool Surfer on 2006-11-07
Mine is a old system with 800 x 600 resolution. Most os try to install or load on 1200 x 800 resolution. So I have to manually make changes to make
it work on my system.

I agree there could be another issue here.

---

### Post by bamboozler on 2006-11-07
I can understand that being the reason for the screen to go blank while installing, but I dont see that as being a reason for the error Im getting when the screen does come back online?
Ohhh, unless its something to do with the graphics card?

---

### Post by bamboozler on 2006-11-09
I changed the graphics card and then I was able to see what the menu screen said, instead of it auto running.

Did a memory test and cd test as a result removed one memory stick as it was full of errors.

Now it is starting to load, showing the ubuntu screen and loading for a while (approx 3-5 mins) then the screen goes blank again and even after leaving it for several hrs it doesnt come back on.
What am I doing wrong?
Hard drive is freshly formatted fat32.

---

### Post by bamboozler on 2006-11-10
Just wanted to thank everyone for their help and I see you're a really close knit group choosing to help only those already in. As such I'll go back to an OS that has support and actualy works on every system Ive ever installed it on... Microsoft Windows.

---

### Post by sparkleanimesh on 2006-11-30
even I am getting the same error. Any luck?

---

### Post by connells on 2007-02-11
I received the same message when I tried to install on an old pc.  I also tried the memory test which I killed after about one hour.
After trying every option and always getting the same kernel panic message I decided to install Windows Server 2000 using "their" ;-)  installation CD. I figured if that installed then the Ubuntu CD was the problem.  When I was installing Server 2000 I got the very terminal message
STOP: 0x00000050
PAGE_FAULT_IN_NONPAGED_AREA .

So I did a search and found the MS KB 171003 page which said that this is caused by faulty RAM and it gave instructions to hunt down all the places to find where the faulty RAM is.  My first thought was to replace the RAM sticks/cards before disabling cache levels and so on.  So I raided another pc and replaced the RAM.

When I tried to install the Ubuntu 6.10 CD again with the new RAM it worked!  I now have Ubuntu installed.  Joy.

So MS helped me with my Ubuntu installation problem. :lolflag:

---

### Post by doctor_mohamed on 2007-04-20
i have the same problem
i downloaded the iso image of ubuntu 6 10 & burned it every thing was allright 
1:iboot from cd 
2:i choose install ubuntu
3:then there was apage in its end i read kernel panic
try to kill init:guitar:

---

### Post by ByteofKnowledge on 2007-05-08
What system are you installing it on? I had to upgrade the BIOS and put in a bunch of flags to get mine to install...

[http://ubuntuforums.org/showthread.php?p=2616756#post2616756]("http://ubuntuforums.org/showthread.php?p=2616756#post2616756")

---

### Post by Francoisdp82 on 2007-11-29
I also had "Kernel Panic - not syncing:Attempted to kill the idle task ..." but on 7.04, turned out to be ram. The Linux installer seems to be very sensitive to faulty ram.

---

### Post by thedstro on 2008-04-24
This problem went away for me just by swapping the memory DIMMs in my system.

---

