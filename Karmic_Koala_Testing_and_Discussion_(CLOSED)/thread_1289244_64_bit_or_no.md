---
title: "64 bit or no?"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Choad on 2009-10-12
so what's the deal these days with 64 bit? what doesn't work with it?

---

### Post by steeleyuk on 2009-10-12
How long is a piece of string?

---

### Post by Choad on 2009-10-12
> **steeleyuk said:**
> How long is a piece of string?
half as long as twice it's length

---

### Post by philinux on 2009-10-12
> **Choad said:**
> so what's the deal these days with 64 bit? what doesn't work with it?

Been running it for 18months now. Not a single problem. 

Even got 64 bit flash.

---

### Post by Choad on 2009-10-12
> **philinux said:**
> Been running it for 18months now. Not a single problem. 

Even got 64 bit flash.
good to hear. i'm getting the 64 bit beta, will test it out for a few weeks and if it looks up to scratch i'll make the switch permenantly

---

### Post by keplerspeed on 2009-10-12
I have always run 64ibt ubuntu. No issues now, a few back in the Hardy era, but not now.

If you have 64bit hardware, use it.

---

### Post by waspbr on 2009-10-12
as far as I can tell java is still a little bit of an issue

---

### Post by vinutux on 2009-10-12
more than 1 year in 64 ........no prob.... yes some tweaks needed...enjoying better speed when encoding video/audio and rendering 3d files etc...

one problem i am faced is tweetdeck (adobe air app) is not well under 64...but fixed now

---

### Post by waspbr on 2009-10-12
so am I alone on the java thing?

---

### Post by truck87bp on 2009-10-12
Yes for 64, 

Had problems with 32..tried Evolution, big mistake, entered a piece of fat finger data (fail of course) and decided to install Thunderbird. Error was passed on to Thunderbird. Could receive mail but couldn't send. Passwords are stored in a new place...Got upset.

new Skype64 works fine.

Installed 64 and everything is working fine except: 

Ear Candy won't start.Fail

Controls on youtube won't function but the vid plays, just no way to pause without cancel. Full screen seemed to work ok.

Very happy camper so far!:P

---

### Post by coldReactive on 2009-10-12
More than likely, since I've rarely ever used JAVA myself on linux.

Also, I've heard rumors that Microsoft is not going to support x86 in their next windows after Win7.

---

### Post by Paqman on 2009-10-12
> **Choad said:**
>  what doesn't work with it?

From my experience only some 3rd party apps: Gears, Amazon mp3 downloader and Adobe Air. None of which are a huge hassle to get working.

---

### Post by keplerspeed on 2009-10-12
I havnt played with java at all, so I cant comment.

For what I use, ie for flash and any apps, everything works as well as 32bit.

---

### Post by viper8 on 2009-10-12
I've been running 64-bit here for the past couple years.  Yeah Flash used to be a pain to get working 100% correct, but since 8.10 stuff just WORKS!  It is great to get to use all of the 4GB of memory the computer has.

9.10 Beta 64-bit has been a breeze.  I highly recommend it.  

ETA: Oh, even Hulu for Linux Desktop 64-bit works! :)

---

### Post by coldReactive on 2009-10-12
> **truck87bp said:**
> Controls on youtube won't function but the vid plays, just no way to pause without cancel. Full screen seemed to work ok.

I've used flash in x64, and controls for youtube vids were--oh wait, that's right, I use 32-bit flash coupled with ia32-libs. *facepalm*

So why doesn't Ubuntu first try to get 64-bit flash, and if that fails, THEN get 32-bit flash? Or is firefox also 32-bit?

---

### Post by taavikko on 2009-10-12
> **coldReactive said:**
> I've used flash in x64, and controls for youtube vids were--oh wait, that's right, I use 32-bit flash coupled with ia32-libs. *facepalm*

So why doesn't Ubuntu first try to get 64-bit flash, and if that fails, THEN get 32-bit flash? Or is firefox also 32-bit?

Because 64-bit flash is still in very alpha state.
when it is released officially, then it would be added to repos.

Though I agree, at this stage, it would be nice addon to have.
If $ARCH = x86_64;
then wget adobelabs.libflashplayer.so.x86_64
install 
else

Lol, ^^ what a load of "insert profanity here"
Shouldn't try to code :D

---

### Post by Choad on 2009-10-12
seems good so far. still can't get rid of the screen tearing tho, which is a big disappointment

---

### Post by coldReactive on 2009-10-12
> **Choad said:**
> seems good so far. still can't get rid of the screen tearing tho, which is a big disappointment

Screen tearing is to be expected in open-source drivers for graphics, and even flash itself. There are numerous ways something can be at fault for screen tearing. The graphics devs may blame flash, and flash may blame the graphics devs, because both or one could be at fault.

---

### Post by Choad on 2009-10-12
> **coldReactive said:**
> Screen tearing is to be expected in open-source drivers for graphics, and even flash itself. There are numerous ways something can be at fault for screen tearing. The graphics devs may blame flash, and flash may blame the graphics devs, because both or one could be at fault.
what's it got to do with flash? the whole desktop tears like a mofo

---

### Post by coldReactive on 2009-10-12
> **Choad said:**
> what's it got to do with flash? the whole desktop tears like a mofo

Then obviously your graphic drivers are at fault. But tearing happens in flash specifically on some graphics drivers. I would submit a bug to your drivers package in launchpad.

---

### Post by philinux on 2009-10-12
> **waspbr said:**
> as far as I can tell java is still a little bit of an issue

Yep just the odd java app sometimes will not run where it will run in 32 bit.

---

### Post by ikt on 2009-10-12
> **Choad said:**
> what's it got to do with flash? the whole desktop tears like a mofo

and this wasn't happening on your 32 bit system?

---

### Post by Choad on 2009-10-12
> **ikt said:**
> and this wasn't happening on your 32 bit system?

yes it was, i wasn't saying it was the fault of anything in particular, just commenting that it still doesn't work

---

### Post by Anubis on 2009-10-12
When will these threads EVER cease?

There is a sticky right there up front no?:confused:

---

### Post by FuturePilot on 2009-10-12
I've been using 64bit since Jaunty and it's great.

---

### Post by davidryderuk on 2009-10-12
> seems good so far. still can't get rid of the screen tearing tho, which is a big disappointment


Never had this problem myself, but is this what you are looking for?

[http://tombuntu.com/index.php/2009/09/20/make-compiz-run-smoothly-and-without-tearing/](http://tombuntu.com/index.php/2009/09/20/make-compiz-run-smoothly-and-without-tearing/)

---

### Post by emarkay on 2009-10-12
Why would I want to go to 64 bit?  (really...)

---

### Post by coldReactive on 2009-10-12
> **emarkay said:**
> Why would I want to go to 64 bit?  (really...)

Because microsoft will probably stop supporting x86 soon?

---

### Post by FuturePilot on 2009-10-12
> **emarkay said:**
> Why would I want to go to 64 bit?  (really...)

I think the question should be "why would I want to go 32bit?" If you have 64bit hardware, it makes no sense to slap a 32bit OS on it. That would be like buying a race car and imposing a limit on it so that you can't go faster than 25mph. That's just my opinion. This thread may help you [Advantages and Disadvantages of 64bit.]("http://ubuntuforums.org/showthread.php?t=765428")

---

### Post by Choad on 2009-10-12
mmmmmm 2.6 ghz core 2 quad 64bit OS and 4 gig of ultra low latency ram = my computer is a BEAST

yet still adobe manages to write flash so poorly that it can't maintain 30fps at full screen (well, on some higher definition vids anyway)

---

### Post by dabl on 2009-10-12
I've been running 64-bit since 6.10.  The only issues I've ever had, that were due to the 64-bit arch, were flash and java.  Speaking of which:

> **waspbr said:**
> so am I alone on the java thing?

Kind of depends on what constitutes a problem for you.  :)

As far as I can tell, java works just fine -- I admit I am not heavily dependent upon it, and probably don't push it very hard. However, a friend of mine is forever asking me to check my 64-bit system on one of the java test sites, and half the time it reports that my version of java is out of date, or some such thing. So yeah, java might or might not be 100% capable at all moments.

I haven't seen an issue with flash in at least a year -- it just works on my hardware.

BTW, for amusement I often check the 64-bit forum here:  [http://ubuntuforums.org/forumdisplay.php?f=343](http://ubuntuforums.org/forumdisplay.php?f=343)

Typically, of the 20 posts that show on the first page, only 2 or 3 actually have anything at all to do with the 64-bit architecture.  The rest of the "no audio, nvidia driver is broke, can't see my new hard drive, what about i810 ..." stuff is irrelevant to the architecture.

---

### Post by emarkay on 2009-10-12
> **emarkay said:**
> Why would I want to go to 64 bit?  (really...)

Thanks!

A partially related thread hijack handled professionally!  :)

---

