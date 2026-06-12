---
title: "Howto: Compile Chromium on Ubuntu 9.10 Karmic Koala"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jonathank89 on 2009-10-12
I wrote this pretty straightforward tutorial for anyone interested in compiling the chromium web browsers themselves, as I said my my tutorial I did see a boost in performance as you'd expect from compiling something yourself, this was mostly seen in starting the application its self from a cold start. Not only is it working great performance wise, but it hasn't crashed on me at all which is nice.

Note: Compiling something of this size will take around an hour, just depends on the speed of your system.

Anyway, hope its helpful,

Link - [Howto: Compile Chromium on Ubuntu 9.10 Karmic Koala]("http://friendlytechninja.com/2009/10/11/howto-compile-chromium-on-ubuntu-9-10-karmic-koala/")

Link - [http://friendlytechninja.com/2009/10/11/howto-compile-chromium-on-ubuntu-9-10-karmic-koala/]("http://friendlytechninja.com/2009/10/11/howto-compile-chromium-on-ubuntu-9-10-karmic-koala/")

Jonathan

---

### Post by ikisham on 2009-10-12
Nice, thank you.

---

### Post by Regenweald on 2009-10-12
And how to add the nightly ppa!
```

sudo add-apt-repository ppa:chromium-daily

```

I think we have chromium locked down now :)

---

### Post by hanzomon4 on 2009-10-12
is there an apt-cache search type thing for ppa's

---

### Post by meborc on 2009-10-13
> **hanzomon4 said:**
> is there an apt-cache search type thing for ppa's

you mean locating packages? yes, it works the same...

or did you mean locating PPA's? then yes - google "chromium PPA" for example ;)

---

### Post by donniezazen on 2009-10-13
> **jonathank89 said:**
> I wrote this pretty straightforward tutorial for anyone interested in compiling the chromium web browsers themselves, as I said my my tutorial I did see a boost in performance as you'd expect from compiling something yourself, this was mostly seen in starting the application its self from a cold start. Not only is it working great performance wise, but it hasn't crashed on me at all which is nice.

Note: Compiling something of this size will take around an hour, just depends on the speed of your system.

Anyway, hope its helpful,

Link - [Howto: Compile Chromium on Ubuntu 9.10 Karmic Koala]("http://friendlytechninja.vndv.com/2009/10/11/howto-compile-chromium-on-ubuntu-9-10-karmic-koala/")

Link - [http://friendlytechninja.vndv.com/2009/10/11/howto-compile-chromium-on-ubuntu-9-10-karmic-koala/](http://friendlytechninja.vndv.com/2009/10/11/howto-compile-chromium-on-ubuntu-9-10-karmic-koala/)

Jonathan

Thanks a lot.

What about updates? Should i add the PPA? Can i move the folder to some other place as i don't want it on my desktop? Where should i move it? Is performance so good that you suggest compiling over download from ppa?

---

### Post by meborc on 2009-10-13
> **soham_1207 said:**
> Thanks a lot.

What about updates? Should i add the PPA? Can i move the folder to some other place as i don't want it on my desktop? Where should i move it? Is performance so good that you suggest compiling over download from ppa?

just delete the chromium you have now... then install the one from the PPA... adding PPA to your sources list will keep it always updated ;)

so next time you apt-get update && apt-get upgrade, chromium will get upgraded from the PPA

---

### Post by jonathank89 on 2009-10-13
I agree that the PPA is pretty good, however I still get better performance compiling it myself. Which again is the point of the thread.

I do like how karmic deals with PPA's now though, it's nice and easy...PPA's for Humans :D

---

### Post by meborc on 2009-10-13
> **jonathank89 said:**
> I agree that the PPA is pretty good, however I still get better performance compiling it myself. Which again is the point of the thread.

I do like how karmic deals with PPA's now though, it's nice and easy...PPA's for Humans :D

it all goes down to hardware. if you have a good processor and fast memory, then the difference is not that great

if you are using something from the last century, you should look into compiling

---

### Post by ikisham on 2009-10-13
> **hanzomon4 said:**
> is there an apt-cache search type thing for ppa's

[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

[QUOTE=meborc]it all goes down to hardware. if you have a good processor and fast memory, then the difference is not that great

if you are using something from the last century, you should look into compiling [/QUOTE]

I have an Athlon XP 1700+ (1466 MHz/single core) and DDR400 (limited to 333 by the mobo). Ubuntu itself is a bit too much for it. Is this a case of compiling?

Would it be updatable?

---

### Post by jonathank89 on 2009-10-13
> **soham_1207 said:**
> Thanks a lot.

What about updates? Should i add the PPA? Can i move the folder to some other place as i don't want it on my desktop? Where should i move it? Is performance so good that you suggest compiling over download from ppa?

There might be away to apply updates to your compiled code, you'd basically be applying patches. I don't know how do to it myself, but I'll keep an eye out. I've found the current source code be very stable, haven't run into any problems. The only thing I'd know to apply all new updates is to recompile the code, but thats quite time consuming. As I said I'll look into it. PPA might be your best bet.

> **meborc said:**
> it all goes down to hardware. if you have a good processor and fast memory, then the difference is not that great

if you are using something from the last century, you should look into compiling

Whether your using new or old hardware I think it is still a good thing to compile things yourself, because you'll always see optimisation. I agree that you'll see this more so on older machines, however new machines such as mine will still get significant boosts. Now it's just easier to add the PPA and let the updates roll in via update manager, but you're not going to get the best performance out of your application.

> **ikisham said:**
> [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)



I have an Athlon XP 1700+ (1466 MHz/single core) and DDR400 (limited to 333 by the mobo). Ubuntu itself is a bit too much for it. Is this a case of compiling?

Would it be updatable?

I'd say it would be worth while compiling it, but it will take a very long time to do so for you inparticular. I'm a little surprised that your PC seems to struggle with ubuntu, the recommend specs with for visual effects are 1.2 GHz x86 processor and 384 MB of RAM...You might consider jumping to Xubuntu, specs are even less.

In conclusion I'd say if you like tinkering around with software, want to get the most out of your application and are patient then compile away! However if you just want the quick and dirty method get the PPA.

I'm going to look into making patches for it...don't see why you'd need to always recompile to get updates.

---

### Post by hanzomon4 on 2009-10-13
No I mean from the command line.. I mean that would make add-apt-repository ppa:whatever ppa a lot more useful

---

### Post by ikisham on 2009-10-14
> **hanzomon4 said:**
> No I mean from the command line.. I mean that would make add-apt-repository ppa:whatever ppa a lot more useful

In the future Software Center is supposed have that.
[http://ubuntuforums.org/showthread.php?t=1288403](http://ubuntuforums.org/showthread.php?t=1288403)

[QUOTE=jonathank89]I'd say it would be worth while compiling it, but it will take a very long time to do so for you inparticular. I'm a little surprised that your PC seems to struggle with ubuntu, the recommend specs with for visual effects are 1.2 GHz x86 processor and 384 MB of RAM...You might consider jumping to Xubuntu, specs are even less.

In conclusion I'd say if you like tinkering around with software, want to get the most out of your application and are patient then compile away! However if you just want the quick and dirty method get the PPA.[/QUOTE]

I have antiX in another partition and it opens everything immediately. The 'problem' is not the background since I had a minimal Ubuntu with IceWM and also crunchbang (#!) (which is more or less the same thing) and they worked pretty fast (specially the former). Gnome is slower and Ubuntu's default desktop even more.
I installed Karmic because it's cool ;) and it is quite speedy considering the refinement. It's like there's a setting that makes everything lag a bit before opening (besides the normal lag).
I'm thinking about compiling Chromium for antiX (replacing the dependencies for Debian ones) and in Karmic, if needed, install from the PPA.

---

