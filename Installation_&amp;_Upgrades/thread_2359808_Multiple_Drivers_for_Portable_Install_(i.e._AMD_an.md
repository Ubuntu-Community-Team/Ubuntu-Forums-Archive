---
title: "Multiple Drivers for Portable Install? (i.e. AMD and nVidia driver availability)"
date: 2017-04-28
forum: Installation &amp; Upgrades
---

### Post by humanjhawkins on 2017-04-28
I've installed Ubuntu 16.04 on a portable drive. The primary computer that will use this has an nVidia graphics card. But I want to be able to plug into other computers (with the same 64-bit Intel architecture) and boot, achieving essentially full functionality. In this case, I would only expect one or the other driver to be active at any given time... Don't need to support multiple different cards in the same machine. 

Is it safe to install additional drivers to support various hardware on other machines I may plug into?

Thanks.
Jeff

---

### Post by Bucky Ball on 2017-04-28
Welcome. Lots of the drivers will already be in the kernel so ...

Hard question to answer as there is a plethora of devices out there and some need drivers not in the kernel, some don't.

I wouldn't be worried about that and would jump that hurdle when you need to. What I'd be concerned with is booting the thing on any machine and wireless. Graphics should work one way or the other (low graphics mode is usable), but that's not the case with wireless.

Know how many wireless cards are out there? Know which ones work out of the box with Ubuntu and which need drivers and which don't??? No, neither do we. Many have been identified but new ones arrive everyday. Impossible to tell you how to install the drivers for everyone of them, let alone which drivers.

As for boot, can your disk boot in *_either_* UEFI or legacy mode, depending on what the host machine boots in? It will need to. Start researching there because if you can't get it to boot, the rest is noise. :)

Just one question: how are you sure all the machines you are booting on will be Intel? It makes no difference whether they are or not really. What is important is 64bit or 32bit. AMD, Intel. Not relevant. What is relevant is the disk being capable of UEFI or legacy booting and I can't help with that. There is a way you can set it up to boot in either I think, but know nothing about it. Others do.

When I first got into Ubuntu and saw its potential I got very excited and had some ideas about what I could do with it (some big and very unrealistic ones amongst them!). As I learned more about it I realised some of my ideas were possible and some were fantastical. What you want to do will work, but perhaps not the way you are imaging it right now and perhaps with a few limitations you have not foreseen either.

Hope that helps a bit and good luck.

(PS: Does your username allude to [Screamin' Jay Hawkins]("https://www.youtube.com/watch?v=aSl9n4rlBH4") by any chance? No offence intended, just curious. :))

---

### Post by humanjhawkins on 2017-04-28
Thanks much for the reply. I think you've answered most (all?) of my concerns. What I meant by "Intel" was just that I'm not expecting to boot non-x86 derived processors (Qualcomm, etc). But it's really even more limited than that. Primarily this would be for booting a few different computers within my own home, rather than everything in the world. (I do hope to boot a friend's Windows laptop, and I don't know it's components. But I expect to have to handle some new driver issues when I get to that.)

My main concern was just that installing the AMD graphics drivers would kill or conflict with the nVidia ones. Threads from people wanting to run nVidia and AMD concurrently on the same machine seemed to indicate that was a minefield.

Cheers for the Screamin' Jay Hawkins reference... No relation here, and it's just a coincidence of naming. But that cat is maaad!

---

### Post by oldfred on 2017-04-28
No idea if any of this is still valid or works. Have not needed to try it.

 Easily Swap Between AMD & NVIDIA OpenGL Linux Drivers At Boot Time - systemd
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-GPU-Driver-Swap](http://www.phoronix.com/scan.php?page=news_item&px=Linux-GPU-Driver-Swap)
[https://github.com/mikeanthonywild/gpu-driver-swap/blob/master/gpuswap.sh](https://github.com/mikeanthonywild/gpu-driver-swap/blob/master/gpuswap.sh)
Boot using recovery mode & 'Reconfigure graphics' or
Create Portable Ubuntu for 2 different Video Cards - script
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)

---

### Post by Bucky Ball on 2017-04-28
> **humanjhawkins said:**
> My main concern was just that installing the AMD graphics drivers would kill or conflict with the nVidia ones. Threads from people wanting to run nVidia and AMD concurrently on the same machine seemed to indicate that was a minefield.

Your concern is warranted. Yes, that could cause chaos. The same is possible if you manually install more than one wireless drivers. That too could cause confusion and conflict. That's not to say there isn't a workaround for both eventualities. Matter of finding it or working one out.

Might pay to leave the install as 'vanilla' as possible, i.e. use the Nouveau open-source graphics driver. You may get a good (enough) or excellent result with that.

As mentioned, there's a lot of drivers in the Ubuntu kernel already so possibly a better better option is vanilla install, plug into each machine, see how it flies and work from there. As this is only for a few machines and not 'the world', then you might get lucky with vid and wireless on all machines.

Yes, Screamin' Jay is maaaad! Wonder if he and James Brown ever did a double act ... :-k

---

