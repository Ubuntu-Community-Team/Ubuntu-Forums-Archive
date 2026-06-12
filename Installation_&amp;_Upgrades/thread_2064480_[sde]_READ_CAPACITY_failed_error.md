---
title: "[sde] READ CAPACITY failed error"
date: 2012-09-29
forum: Installation &amp; Upgrades
---

### Post by ancap2540 on 2012-09-29
I have been trying to install 12.04 for the past week or so. I have tried both CD and USB. It will load from either, then drag on for several minutes, then I am presented with this inscrutable mystery which reads in part:

>  2 (or 3 or something):0:0:02(or 3...) [sde] READ CAPACITY failed
                                                                   Driver OK (or words to that effect)
                                                                   attempting write through (yada yada yada...)

repeating over and over again And this could theoretically  go on till the end of time.

The computer is an eMachine 1161-07 with a nVidia 6150SE graphics card.
I have 2 hard drives on board, one is the original Hitachi 320Gb unit, the other is a 1 Tb Seagate.

I am under the impression that [sde] must refer to some sort of drive. So I disconnected one of the drives, then the other, and everything from the USB ports (except the keyboard). I tried several different downloads, and all the md5s checked out, Burned them all to several discs at different write speeds formatted and reformatted the USB drive and reloaded 12.04, just in case the last time was the problem. Every time i am back to the same problem, this damned [sde] that it can't write home to...

ETA: This problem occurs whether I try to install it directly to the drive, or if I try it out first. I also tried every possible permutation available in the f6 option menu. Nothing there worked too.

---

### Post by ancap2540 on 2012-09-29
Oh well, nothing left to do but to give up on Linux for good. Yes it is free, but I estimate that at least two years was taken from the expected life span of this machine by trying to get this to work. Sorry Uncle Bill for doubting your wisdom.

---

### Post by ancap2540 on 2012-10-02
Well, I had to do it. I caved in to my masochistic streak and decided to try this all over again. After many hours of tweaking this and modifying that I did manage to get this abortion of an OS onto my hard drive. (I seriously believe that it was built broken.)  I had to go into the BIOS and completely disable the USB inputs. By some miracle I held on to the original PS/2 track ball mouse that came with the computer and I had an adapter for the keyboard. 

But that was only one phase of my torment. I soon found out that the Grub loader didn't want to play with my monitor. When I restarted it all I had was this "Input not Supported" message dancing across the screen. If I had known yesterday that after many hours of research and trying out all sorts of advice would have been a complete waste of time I would have simply dropped a few hits of acid and tripped while watching that message. It would have been time well spent.

I'll stick to Vista. Knock it all you want. but at least it **works! **

---

### Post by dino99 on 2012-10-02
a first step help:

```
https://help.ubuntu.com/community/Installation
```

is the iso booting when you answer "try without installing" ?

---

### Post by ancap2540 on 2012-10-02
> **dino99 said:**
> a first step help:

```
https://help.ubuntu.com/community/Installation
```is the iso booting when you answer "try without installing" ?

Thank you for the input.

Yes, I did read that guide, to the point where I could recite stretches of it like poetry.

I did mention that I could boot it in my first post. In fact I finally solved the problem of installing the system itself. I was in a new purgatory over getting the grub loader to function. There are two options I could find. One was using a grub customizer. I downloaded it and tried to use it. But it froze up, colder than a pawnbroker's heart. Another option was the command line, and manually input the resolution and bit depth. After trying a few it dawned on me that there are literally dozens of combinations of the two and  it would have taken quite a bit of time to find the right one, not to mention the wear and tear booting and rebooting to see if the last combo worked.

So there is nothing left to do but admit defeat, and warn anyone else to avoid this Ubuntu if they wish to keep their sanity.

---

### Post by Bashing-om on 2012-10-02
ancap2540; Hi !

I regret that you are experiencing such difficulties.
Have you tried booting to the boot options menu when installing and trying any of the offered solutions ? (i.e. "nomodeset). Once installed an appropriate driver can be installed for your Nvidia card.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Please advise on results.

Rant response: Once you get your feet wet with ubuntu, you will discover it as the greatest operating system in the world, Millions of programmers for generations have made it so (linux has been around since day 1). The support is suburb [ask a pertinent question] and documentation is outstanding. It is, however, a constantly evolving os and one must be aware of major changes -when, where, how they effect and affect the present system.
[INDENT]kind regards <==BDQ
  
[/INDENT]

---

### Post by ancap2540 on 2012-10-03
Thank you for your time and response.

Allow me to repeat myself. After untold agony I did the impossible and actally installed this confounded Ubuntu.  Yes I had to play with all those boot options, but the kicker was to entirely disable the USB ports from the BIOS. I was then prompted to restart my computer. When I did that all I had for my troubles and perseverance was a message bouncing around the screen informing me "Input not Suppoted".

So it was back to the drawing board. Like I said, I tried every available option to get the GRUB loader to work. Every attempt was an abject failure. 

For those of  you who enjoy Ubuntu and managed to get it to work, more power to you. I'm done with it.

---

### Post by ancap2540 on 2012-12-10
What a difference a few months can do.  I installed 12.10 without a single problem, and am enjoying the experience. One minor hiccup was using the "Dash Home" resulted in some serious graphics problems, but between installing updates and the graphics driver, it appears to have solved itself. 

I hereby take back all those negative comments I made back in October.

---

