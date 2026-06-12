---
title: "Latest kernels boot once, then black screens going forward"
date: 2010-03-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Robertjm on 2010-03-11
Hi all,

Really odd thing happening on my system. Every time there's a new kernel update it seems like I can log into Ubuntu just fine. However, the very next time I try it, all I get is a black screen, and this happens on every attempt to boot with that kernel.

Sometimes I will get the quick drum roll sound, but most often nothing. And I can't use the 3 finger salute to kill the gnome desktop to get to a prompt. This has happened with every kernel update starting with 2.6.32-12.

What's odd is that I can always log in successfully with kernel 2.6.32-10!!

Any thoughts short of a clean install of alpha3?

HP/Compaq NC6000 laptop
W7 RC1/Lucid Lynx a2 (fully updated) dual boot

Robert

---

### Post by Robertjm on 2010-03-11
Just an update. I tried booting into the newer kernels using recovery Mode. after a whole bunch of stuff flies over the screen I can get to a prompt. There I start the GUI with startx. Takes a bit but then Gnome launches, albeit it to a generic-looking gui, and as Root user, not robertjm.

The first time I did that I ran the -15 kernel. things seemed to work well and then all of a sudden my screen went black, the cursor locked up and two of the three indicator lights on the computer started flashing slowly. I had to kill the power to get out of that. This time I've launched the -16 kernel. Have been in it about five minutes and so far, so good. 

Robert

---

### Post by Seventh Reign on 2010-03-12
The first time I got a black screen, I simply hit enter and it logged me right in.  After removing several unneeded items from the startup applications, it no longer gives me a black screen at all.

---

### Post by Robertjm on 2010-03-15
I must've missed the notification of your response. Sorry about that. 

I'll try the hitting enter method tomorrow (Lucid is on my laptop, not the desktop I'm using), but I thought I had tried that, only to get some jibberish printed on the screen.

Are you talking about startup applications before or after the gnome desktop login has appeared? I can't even get to that point.

Robert


> **Seventh Reign said:**
> The first time I got a black screen, I simply hit enter and it logged me right in.  After removing several unneeded items from the startup applications, it no longer gives me a black screen at all.

---

