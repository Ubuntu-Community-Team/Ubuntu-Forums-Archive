---
title: "acer travelmate 521it wont run live CD"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by crankster on 2006-12-07
Hi, I'm new to linux. Just downloaded the current CD and I'm trying to run it from my ACER travelmate 521it. I get a splash screen then a black screen with a cursor (but can't type). I've searched this site and I found a reference to changing acpi=off  I have no idea where or how to do this. Any help getting started would be welcome.
C

---

### Post by Sef on 2006-12-07
When it first starts up, press F1, the help menu and it will tell you which F(x) button to push, so you can add  acpi=off.  I think it is F6, but check the help menu to avoid aggravation.

---

### Post by randiroo76073 on 2006-12-07
Also when you're in BIOS look for something called "Boot Order" and make sure that cd or cdrom is first to boot, then hdd

---

### Post by crankster on 2006-12-07
Hi guys, thanks for your suggestions.  I have tried them. Sef, I'm assuming that I use the F keys in the initial Ubuntu splash screen. It takes me through various help options and mentions the apic=off but again, it seems to assume that you know where to type this. I can't find this magical place ;)  I have changed the boot order. Whilst I was playing with the Ubuntu splash screen, I thought I'd change the video setting (F5) and change it from vga to 800*600 screen res. I have progress. Now It shows a new ubuntu splash screen with a cyclops status bar thingy. That hangs after a while and I get back to a 'busy box' prompt type screen with the following:
/bin/sh/: can't load tty: job control turned off

If I do nothing it then tells me that irq 15: nobody cared and it loops through a few lines after that.

Does this help cos I'm confused  ](*,)

---

### Post by pegazuz on 2006-12-07
I don't know enough about linux to fix anything or even install it on my hard drive but have used several Linux Live 
CD's. I have an Acer Aspire 5102 and Ubuntu 6.10 does a great great job of detecting everything and setting up what ever is needed to run Ubuntu Linux. It does take awhile to load everything. 

Mepis and Knoppix also work well on my machine but several other live CD's just would not boot up for reasons I never understood or else some programs wouldn't work like the wireless mouse or wi-fi internet connection.  Have you tried other live CD's?

Darn Small Linux and Puppy Linux are two easy ones to download too as they are both very small.  These generally worked with every machine I tried too. I also had one Ubuntu Live CD that didn't work due to some problem either with download or the CD. Have you tried other CD's to see if they work on your machine?

---

### Post by crankster on 2006-12-07
> **pegazuz said:**
> I don't know enough about linux to fix anything or even install it on my hard drive but have used several Linux Live 

snip

Darn Small Linux and Puppy Linux are two easy ones to download too as they are both very small.  These generally worked with every machine I tried too. I also had one Ubuntu Live CD that didn't work due to some problem either with download or the CD. Have you tried other CD's to see if they work on your machine?

Good point. I haven't tried but then this is my first look at Linux so I'm not familiar with the options. I read about Ubuntu and liked the philosphy of it. I'm normally a Mac person so windows and linux are foreign. The laptop I'm using has only minimum ram and a 5gig hardrive so not sure if loading diff OS's will be a problem. I'll look into those other options.
Cheers
C

---

### Post by pegazuz on 2006-12-07
> **crankster said:**
> Good point. I haven't tried but then this is my first look at Linux so I'm not familiar with the options. I read about Ubuntu and liked the philosphy of it. I'm normally a Mac person so windows and linux are foreign. The laptop I'm using has only minimum ram and a 5gig hardrive so not sure if loading diff OS's will be a problem. I'll look into those other options.
Cheers
C

Then you might not have enough ram to run a program like Ubuntu 6.10 but something like Darn Small Linux might work fine. Try that and see if it boots up OK.  There are versions of linux you can run on very old machines.  I did install it once on an old P2 with a 2 GB HD and 64 ram and it ran fine but wi-fi would not work.

---

### Post by unleashx on 2007-04-12
Hi
I also had troubles running live CD on my Acer Travelmate 521iT
i am currently running Kubuntu 7.04 Fiesty on Acer Travelmate laptop.
i found that on the screen when it asks if you want to install and all those other options, i found the extra commands "vga=771" and "irqpoll" really heaped me boot into the live CD.
hope this has helped.

MY System Specs:
Intel Celeron 600Mhz
256MB Ram
80GB of HD Space
8MB Video Memory

---

