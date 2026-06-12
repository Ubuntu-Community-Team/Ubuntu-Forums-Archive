---
title: "Alpha 3 Live CD Crashes"
date: 2008-07-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MilkeySUFC on 2008-07-28
Hi,

I've been a Ubuntu convert since Feisty and thought I'd have a dabble with Intrepid.

Being a noob when it comes to testing I wouldn't know where to start with my issue of the Live CD crashing when loading on my Samsung Q45 laptop.

Any help/info on where to go/what to do next would be appreciated.

Cheers,
Milkey

---

### Post by ronacc on 2008-07-28
a little more info would be helpful , like when is it crashing ? are there any messages displayed ? does it lockup completly or just hang while booting ? 
edit: also which exact live cd there are daily versions .
edit: opps didn't pickup on the alpha3

---

### Post by MilkeySUFC on 2008-07-28
> **ronacc said:**
> a little more info would be helpful , like when is it crashing ? are there any messages displayed ? does it lockup completly or just hang while booting ? 
edit: also which exact live cd there are daily versions .
edit: opps didn't pickup on the alpha3

(See told you I was a noob)

I dl'd & burnt the Live CD Saturday morning from the link pointed to in one of the "Is Alpha 3 out yet" threads in this forum.

It 'hard' locks up on the Ubuntu splash screen (with the progress bar at about 2 bars loaded). No keys active, on/off switch is the only way out.

Also, the progress bar corrupts and I end up with, as well as the main one, half a progress bar above and to the left of the 'real' one and half of one below and to the right.

Thanks,
Milkey

---

### Post by ronacc on 2008-07-28
what kind of graphics does that laptop have ? alpha 3 is reported to have problems with ati . are your keys completly dead ? if so I don't think much can be done , if you can alt+F1 and get to a terminal it might be possible to get some clues .

---

### Post by MilkeySUFC on 2008-07-28
> **ronacc said:**
> what kind of graphics does that laptop have ? alpha 3 is reported to have problems with ati . are your keys completly dead ? if so I don't think much can be done , if you can alt+F1 and get to a terminal it might be possible to get some clues .

Intel X3100. GM965 chipset. Yes, keys completely unresponsive.

---

### Post by ronacc on 2008-07-28
looking more around the forum ( you really should search the forum to see if anyone else is posting about your problem ) it seems that intel graphics are having a problem with usplash ( the boot splash screen ) I don't know if you can do it with the live cd but removing splash from the boot line should get you to a desktop , actualy I would remove both quiet and splash so you can see what is going on .

---

### Post by MilkeySUFC on 2008-07-28
> **ronacc said:**
> looking more around the forum ( you really should search the forum to see if anyone else is posting about your problem ) it seems that intel graphics are having a problem with usplash ( the boot splash screen ) I don't know if you can do it with the live cd but removing splash from the boot line should get you to a desktop , actualy I would remove both quiet and splash so you can see what is going on .

Well, I DID search for various cominations of "Ibex/Alpha/Intrepid" & "Live CD crash" but couldn't see anything that resembled my problem. What with being a noob - and only wanting to help test, but on my non-main machine, I plumped for the laptop. And being a novice at these things, had no idea to look for the issue being graphics related specifically.

So "remove both quiet and splash", is that in the boot options line?

---

### Post by ronacc on 2008-07-28
I don't have a live cd handy to look at to see if it is even possible to alter the boot options on the live cd , but yes that would be on the boot line somewhere . I just checked the alternate install cd and on it you can alter the boot options .so you probably can on the live cd .

---

### Post by MilkeySUFC on 2008-07-29
> **ronacc said:**
> I don't have a live cd handy to look at to see if it is even possible to alter the boot options on the live cd , but yes that would be on the boot line somewhere . I just checked the alternate install cd and on it you can alter the boot options .so you probably can on the live cd .

Thanks, ronacc, I do appreciate your help. I will attempt to play with the boot options tonight.

---

### Post by Gina on 2008-07-29
Just run up Alpha 3 from Live CD and I can confirm that the Live CD has the options too (using F keys - help line along bottom of screen).  My Live CD runs on my P4 with ATI graphics card - using it now.

---

