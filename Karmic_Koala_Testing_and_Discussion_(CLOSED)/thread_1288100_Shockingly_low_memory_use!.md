---
title: "Shockingly low memory use!"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jcris on 2009-10-10
I jumped on Intrepid, and Jaunty betas at alpha 6, and they were boring tests with nothing worth noting. I got on Karmic early on at Alpha 5 this time choosing Xubuntu, and Ive had everything go wrong to blank screens, and shut downs out of nowhere, and its been a "fun" eventful, hair pulling test. I notice after the kernal update yesterday that memory use has dropped quite a bit, making me think we are winding down and everythings coming together. But after todays kernal update, I was close to having a heart attack at just how low memory use has really dropped. At boot up idle it was sitting at 81 Meg! Everything is popping and snapping, and what I thought was gonna be a total mess has really become the best Ubuntu version so far. I'm curious at what we are gonna end up with, and now I'm obsessed with trying to get that idle ram use down to the 70's LOL. Has anyone else noticed this tremendous drop in overall ram use or is this just a fluke and tommorow's batch of updates gonna put us back into hell?

---

### Post by psyke83 on 2009-10-10
> **jcris said:**
> I jumped on Intrepid, and Jaunty betas at alpha 6, and they were boring tests with nothing worth noting. I got on Karmic early on at Alpha 5 this time choosing Xubuntu, and Ive had everything go wrong to blank screens, and shut downs out of nowhere, and its been a "fun" eventful, hair pulling test. I notice after the kernal update yesterday that memory use has dropped quite a bit, making me think we are winding down and everythings coming together. But after todays kernal update, I was close to having a heart attack at just how low memory use has really dropped. At boot up idle it was sitting at 81 Meg! Everything is popping and snapping, and what I thought was gonna be a total mess has really become the best Ubuntu version so far. I'm curious at what we are gonna end up with, and now I'm obsessed with trying to get that idle ram use down to the 70's LOL. Has anyone else noticed this tremendous drop in overall ram use or is this just a fluke and tommorow's batch of updates gonna put us back into hell?

It's absolutely impossible that you could boot into a default graphical environment (GNOME or KDE) with just 81mb of ram used, and while Xubuntu is a lot lighter, I seriously doubt that the XFCE environment is so frugal. You must have misinterpreted the free memory displayed - perhaps you were looking at the swap usage?

While in the graphical environment, please post the output of:
```
$ free -m
```

Having said that, I hope you prove me wrong... :)

---

### Post by alphacrucis2 on 2009-10-10
> **psyke83 said:**
> It's absolutely impossible that you could boot into a default graphical environment (GNOME or KDE) with just 81mb of ram used. You must have misinterpreted the free memory displayed - perhaps you were looking at the swap usage.

Please post the output of:
```
$ free -m
```

He says he is using xubuntu.

---

### Post by psyke83 on 2009-10-10
> **alphacrucis2 said:**
> He says he is using xubuntu.

Yes, I'd like to see the detailed memory usage. I installed Xubuntu 8.10 or so on a 196mb PII system, and I recall it maxing out the memory, and dipping into swap after opening a single application.

---

### Post by keithpeter on 2009-10-11
> **psyke83 said:**
> Yes, I'd like to see the detailed memory usage. I installed Xubuntu 8.10 or so on a 196mb PII system, and I recall it maxing out the memory, and dipping into swap after opening a single application.

OK, results below not Karmic but Jaunty Ubuntu command line install with a core XFCE on top (missed out network manager and a few other bits and pieces that take ram), and I think I'm using the slim graphical log in (its on autologin and I can't remember!). If there is a possibility of even lower memory use on this kind of hardware (700MHz copper mine with 256Mb ram) the little hard drive will be truly grateful!

```
Fresh boot on a 'core' xfce (not the full xubuntu) on top of Ubuntu Jaunty command line install (the 'minimal' one).

keith@l400:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           244        131        113          0          7         65
-/+ buffers/cache:         58        186
Swap:          768          0        768
keith@l400:~$ 

Running Firefox 3.0.14 and a second terminal window with vwdial running on my web'n'walk modem

keith@l400:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           244        200         44          0          8         95
-/+ buffers/cache:         96        148
Swap:          768          0        768
```

---

### Post by MacUntu on 2009-10-11
Pretty fresh Ubuntu installation needs 110 MiB on my machine - IMO that's pretty good!

---

### Post by rex4u on 2009-10-11
By the way, which are the biggest memory hogs in Ubuntu or Linux in general ? Any tips anyone...;)

---

### Post by Copernicus1234 on 2009-10-11
> **rex4u said:**
> By the way, which are the biggest memory hogs in Ubuntu or Linux in general ? Any tips anyone...;)

Firefox.

But its so worth it. I dont get this obsession with memory use. Are you all running Ubuntu on 7 year old machines? I can highly recommend running it on a modern machine. Last boot time for the beta is 20 seconds from white logo to desktop... firefox starts in less than 2 seconds. Im on my favorite site a few seconds later. Its simply amazing.

---

### Post by rex4u on 2009-10-11
> **Copernicus1234 said:**
> Firefox.

But its so worth it. I dont get this obsession with memory use. Are you all running Ubuntu on 7 year old machines? I can highly recommend running it on a modern machine. Last boot time for the beta is 20 seconds from white logo to desktop... firefox starts in less than 2 seconds. Im on my favorite site a few seconds later. Its simply amazing.

Thanks bro'
Well I think i am running a modern machine with a pretty good RAM and processor. Anyways, I don't believe in wastage of resources and would love to switch to more effecient but equally feature rich software/s wherever choices present themselves. What u say ? ;-)

---

### Post by Copernicus1234 on 2009-10-11
> **rex4u said:**
> Thanks bro'
Well I think i am running a modern machine with a pretty good RAM and processor. Anyways, I don't believe in wastage of resources and would love to switch to more effecient but equally feature rich software/s wherever choices present themselves. What u say ? ;-)

Sounds good, but if you dont like wastage of resources you should actually use that RAM you payed for. :)

---

### Post by rex4u on 2009-10-14
Great...another way of looking at the things.
Well I use my RAM by running Virtual Machines(VirtualBox) alongwith browsing Net(Firefox 3.5.4), listening music(Rhythembox) and checking mails(Thunderbird). Thats why I talked about optimal use of resources bro' :guitar:

---

### Post by edujose on 2009-10-14
Hi! Good to know low-mem machines will adore Karmic! :-)

Seriously, it's a good thing Linux still keeps a reasonable memory foot print. Many places still use ancient computers (those 7 year old machines mentioned some posts above), like schools (a new batch of PCs have arrived to replace the old ones in a computer classroom, so the old get used in departments, teacher's room and the library), not-so-wealthy homes and everywhere in general.

Oh, this is what my free -m shows:

```
jose@jose-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           497        480         16          0          5        194
-/+ buffers/cache:        280        216
Swap:         1027         10       1017
jose@jose-desktop:~$ 
```

This is with a PIII 1 GHz machine, 512 KB RAM and 10 GB hard disk, with a terminal window, firefox with lots of tabs, a nautilus window and update-manager updating away :-)

---

