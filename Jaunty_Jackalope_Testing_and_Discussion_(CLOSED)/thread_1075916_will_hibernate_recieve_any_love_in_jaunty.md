---
title: "will hibernate recieve any love in jaunty?"
date: 2009-02-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by deathsshadow77 on 2009-02-20
right now on my eee pc using ext4, jaunty boots from grub to gdm in approx 35 seconds.
 
hibernate goes from grub to lock screen in approx 30 secs. It is almost the same as booting. 

In this release will hibernate recieve any more of a boost than what it has from ext4?

---

### Post by Nullack on 2009-02-21
What your seeing now is mostly what youll get in final aside form bug fixes. Youll need to wait for the koala for more changes. Though Im not sure how koala will turn out, cos the truth is in my country most koalas down south are mighty burnt at the moment :) Poor things.

---

### Post by FrancoNero on 2009-03-01
again I think it's a discgrace for Ubuntu that hibernate is still in a state of disrepair ever since.... release after release people moan about it, its a hot issue in brainstorm, again and again its said that this Ubuntu will be for laptops and that Ubuntu will be for laptops, but in the end, hibernate is as messy and unusable as always. Is ANYone working on this at all? Now we're being promised that this will work in Koala... but actually I have huge doubts.... How long do I have to wait until I CAN switch to Ubuntu? For me it's no longer the do I make the switch from Windows, it's when is Ubuntu finally ready to ... W O R K on my laptop as it should...

sorry for the rant, but this issue is simply ridiculous

---

### Post by dBuster on 2009-03-01
I use hibernate all the time in what aspect are you saying it isn't working?  Sure it takes about the same amount of time to boot and a little longer to hibernate than shut down but any running apps at the time of hibernation are fully restored when waking up the laptop....

So in my opinion I would say it is working as I know hibernation to be working.  Could it be that suspend is the one that is not quite working?  I have yet to try that out.

---

### Post by elefantcrossing on 2009-03-01
on my dell xps m1530 both suspend and hibernate work without any problems

---

### Post by RebateFX on 2009-03-01
I'm running Jaunty Alpha 2 and hibernate is still messy but it works even if it takes a while. Anyway, I choose to just shut down completely. Shut down and start up are two things that are very fast in Jaunty which I like.

HP Pavillion dx6000

---

### Post by Lorenz on 2009-03-01
Hibernate never worked for me. I don't even try it on the new releases, it's a waste of time. I think it's because of the graphic card :( (ibm t60, ati x1300)

---

### Post by Gina on 2009-03-01
Neither work on my laptop but I haven't investigated why - I might be me :lolflag:

---

### Post by a fenderson on 2009-03-01
Hibernate "works" for me but I can't use my Atheros wireless card afterwards.  Is there a way to automatically unload the driver before hibernation and reload it afterwards?

---

### Post by blackened on 2009-03-01
> **FrancoNero said:**
> again I think it's a discgrace for Ubuntu that hibernate is still in a state of disrepair ever since.... release after release people moan about it, its a hot issue in brainstorm, again and again its said that this Ubuntu will be for laptops and that Ubuntu will be for laptops, but in the end, hibernate is as messy and unusable as always. Is ANYone working on this at all? Now we're being promised that this will work in Koala... but actually I have huge doubts.... How long do I have to wait until I CAN switch to Ubuntu? For me it's no longer the do I make the switch from Windows, it's when is Ubuntu finally ready to ... W O R K on my laptop as it should...

sorry for the rant, but this issue is simply ridiculous

Unless you are part of a large group of people experiencing the exact same problem, your only recourse is to submit a patch for your particular hardware.

This is _free_ and open-source software. The devs don't owe any of us anything.

> **a fenderson said:**
> Hibernate "works" for me but I can't use my Atheros wireless card afterwards.  Is there a way to automatically unload the driver before hibernation and reload it afterwards?

Is the card not recognized at all after you return from hibernation or can you bring it up with ifconfig?

---

### Post by nyarnon on 2009-03-01
Hibernate works fine here although at the moment I loose alsa after restore. What I miss is the issue here? What is the logic behind the assumption that hibernation should be faster then rebooting? Correct me if I'm wrong but in the optimal scenario shouldn't a reboot always be faster?

---

### Post by blackened on 2009-03-01
> **nyarnon said:**
> Hibernate works fine here although at the moment I loose alsa after restore. What I miss is the issue here? What is the logic behind the assumption that hibernation should be faster then rebooting? Correct me if I'm wrong but in the optimal scenario shouldn't a reboot always be faster?

I agree. Returning from hibernation, logically, should take as much time as, if not a little more than, a cold boot. The two processes do about the same thing: take the os from the harddrive to a usable state, with hibernation giving the added benefit of reinstating session info, hence why it would be allowable for it to take longer.

---

### Post by Nullack on 2009-03-02
Kernel 2.6.29 has code changes in this area

---

### Post by scaine on 2009-03-02
> **blackened said:**
> I agree. Returning from hibernation, logically, should take as much time as, if not a little more than, a cold boot. The two processes do about the same thing: take the os from the harddrive to a usable state, with hibernation giving the added benefit of reinstating session info, hence why it would be allowable for it to take longer.

My mate has a Samsung NC10 notebook running XP (stock build - 1Gb RAM and 160Gb drive) and he can resume from hibernation in about 10 seconds, maybe 15, plus WIFI reconnect time.  It's almost as fast as resuming from Standby.

So, regardless of logic, if XP can do it so quickly, then comparisons will always be made.  I never use it myself though.  Suspend is fine for my needs - I rarely have big sessions running and so I'm happy to shutdown after my use of the laptop.

I should add that my mate rarely has much running either, which might explain why his resume form hibernate is nice and quick.

His boot on that NC10 netbook is about a minute or so, therefore he will almost always hibernate/resume instead of shutdown/startup.

---

### Post by nyarnon on 2009-03-02
Scaine!

What is your point? Your saying absolutely nothing. Facts please. What did, which Ubuntu, under what circumstances, do on that machine? As for the moment please Google 'boot time xp versus linux' and tell me where you see big noticable differences?

IMHO this is all a hype and I don't think that sifting about a few seconds will make any difference in my daily work. I choose Ubuntu because it's free, I have input during development, I have support 24/7 at no extra costs, and it is stable.

Ad ergo boottime is not a priority to me and probably to most normal users.

---

### Post by scaine on 2009-03-02
Nyarnon!  Calm down!  I'm not not saying absolutely nothing!  How very dare you!  :P

I'm saying, generally, that XP can resume from hibernation very quickly indeed.  Sorry if my post confused you!

I didn't google for this and I don't feel like doing so.  I simply watched my mate's netbook resume from hibernation amazingly quickly.

Are we all good?

---

### Post by FrancoNero on 2009-03-02
> **blackened said:**
> Unless you are part of a large group of people experiencing the exact same problem, your only recourse is to submit a patch for your particular hardware.

This is _free_ and open-source software. The devs don't owe any of us anything.

Please check brainstorm, this issue is fairly huge. I'm not saying anyone owes anyone anything, but this is an essential feature of an operating system working on mobile computers in... jeez, it's 2009, not 1999 anymore.

And why would I submit a patch for my particular hardware? a) I'm not a software developer, I'm one of those annyoing "human beings" Ubuntu claims its for and b) I'm not the only one using a regular off the shelf HP laptop (not even new, no ati/nvidia stuff, no fancy add ons, nothing) ...   just saying...

---

### Post by gaspard.leon on 2009-03-02
well I was quite impressed my when I got my Nvidia Geforce 5900XT to suspend correctly (and come back from suspension) on a PC that had never suspended correctly under XP, simply by disabling AGP... I lost a little performance of course, but it was slow already because of the graphics stack design...

Note: only worked with proprietary drivers with AGP disabled
Open source driver never suspends correctly.

RE: cold-boot vs hibernate
I think that the reason hibernate is/could be quicker is that it's simply copying a large file into memory, instead of building the in-memory objects from various files on disk... in-fact, if hibernate *is* quicker, the method it uses e.g. copying an image of the memory into memory should be considered for "faster" booting...

my 2 cents

---

### Post by nyarnon on 2009-03-03
> **gaspard.leon said:**
> 
RE: cold-boot vs hibernate
I think that the reason hibernate is/could be quicker is that it's simply copying a large file into memory, instead of building the in-memory objects from various files on disk... in-fact, if hibernate *is* quicker, the method it uses e.g. copying an image of the memory into memory should be considered for "faster" booting...

my 2 cents

Yes true as long as the processor is slower then the harddisk :-) It's all very relative if you ask me. Especially if the trend of a onchip OS is continuing.

Again I think boottime is one of the worsted possible specs to base your choice of OS on.

---

### Post by mariner09 on 2009-03-03
Boot-time is very critical to a mobile business user.  How many times does someone run into a meeting because his plane was delayed and have to boot up in front of everyone and get his presentation started.

If it was all up and just hibernated, then you dramatically reduce the wait.

Impressions are everything...

I've been a laptop user for over 10 years now and with linux for 7 years.  I've played with standard suspend/hibernation on a few laptops and it always leaves me desiring more.  My current issue is that resume from hibernation seems to leave a residual amount of swap usage that builds upon itself with subsequent hibernates/resume cycles.  I've seen this in the last few releases of FC and Ubuntu.

Over the last few years I began using Suspend2 or TuxOnIce as it's currently called.  I can't tell you how much faster the process is with this tool.  Nigel and Co really have a nice product with very good support and if enough people call for it, it could become a standard.

I can restore a fully hibernated system running Lotus Notes and many other apps within 43 seconds.  You can't get to that state with a cold-boot in less than a couple of minutes.

I too look forward to Koala as I doubt Jaunty will get any hibernate love.

---

