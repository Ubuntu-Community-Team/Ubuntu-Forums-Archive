---
title: "glxgears slow fps"
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by svaens on 2010-03-12
Hi all. 

Just want to help with testing. I have noticed since installing (though not on the lucid liveCD) that glxgears shows a slow fps. 
About half that running on the liveCD. 

Anything anyone knows that I should do to improve the situation?

---

### Post by Atermoon on 2010-03-13
How slow? Also do you have Sync To VBlank enabled in compiz (or your video card's control panel if any)?

With Sync To VBlank I get ~300 frames in 5.0 seconds (60fps), without it I get ~5600 (1120fps).

And of course [glxgears is not a benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

---

### Post by svaens on 2010-03-13
Hi, 

Here is my second reply to your post. My first one got swallowed up by an untimely systems crash on starting gconf-editor ;)

Basically, the Sync To VBlank option doesn't seem to make any difference to the frame rate. 

On Karmic, it tells me 15000 frames in 5.0 seconds. 
On lucid live CD, it tells me 10000 in 5.0 seconds, 
on lucid after installation, it told me 5000 in 5.0 seconds, 
on lucid after updates, it tells me 2000 in 5.0 seconds.

Another notable change in behaviour, 

On lucid live CD, and after initial installation of the alpha 3, there was a thin band of noise in the top part of the glxgears window. After updates, that noise is gone, but the frame rate is also down.

I should have mentioned, I am running lucid on a sony vaio ,with ATI HD 3470 Mobility GPU
I'm not sure what you get with other card types, but I don't think there are any extra settings you get to set when using the free drivers for ATI .. ?

---

### Post by seeker5528 on 2010-03-13
> **svaens said:**
> On Karmic, it tells me 15000 frames in 5.0 seconds. 
On lucid live CD, it tells me 10000 in 5.0 seconds, 
on lucid after installation, it told me 5000 in 5.0 seconds, 
on lucid after updates, it tells me 2000 in 5.0 seconds.

It seems odd that it would change that much, but glxgears is just a basic test to see if 3D is working or not, not a benchmark, the numbers don't have much relevance to what you can expect with something that makes significant use of 3D.

Later, Seeker

---

### Post by Rob2687 on 2010-03-13
It is dependent on your CPU too. Disable speedstep, don't leave anything running in the background and don't forget... glxgears is not a benchmark. ;)

---

### Post by glasen on 2010-03-13
Please write 100x : "GLXgears is not a benchmark!". Further explanations :

[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

---

### Post by svaens on 2010-03-13
Well, yes, I did read that. So, glxgears is not an exact benchmark. But surely, there is an indication that something 'could' be amiss. ... when I compare one running of glxgears to another ... and there is a dramatic change in performance. For while it only tests a minor subset of the openGL functions, a reduction in performance from one run to another indicates that at least those minor subset of functions are not running as well as they used to be. 

But like I said. I probably do not 'need' the super performance, as I do not play 3d games and all that. I got all that out of my system on my old commodore 64 back 20 years ago. Just thought it might need mentioning ... see if anyone thought there was something to it. So far as other problems that used to occur in Karmic are concerned, so far lucid proves an improvement. At least with the free drivers.

---

### Post by psyke83 on 2010-03-13
> **svaens said:**
> Well, yes, I did read that. So, glxgears is not an exact benchmark. But surely, there is an indication that something 'could' be amiss. ... when I compare one running of glxgears to another ... and there is a dramatic change in performance. For while it only tests a minor subset of the openGL functions, a reduction in performance from one run to another indicates that at least those minor subset of functions are not running as well as they used to be. 

But like I said. I probably do not 'need' the super performance, as I do not play 3d games and all that. I got all that out of my system on my old commodore 64 back 20 years ago. Just thought it might need mentioning ... see if anyone thought there was something to it. So far as other problems that used to occur in Karmic are concerned, so far lucid proves an improvement. At least with the free drivers.

You think you're the first person with such a "yes, but..." response? Everybody is tired of explaining why glxgears is completely inaccurate in measuring performance, so don't expect detailed responses to your query.

The radeon driver now uses KMS, which means that the new DRI2 acceleration framework is being used. One characterisic of DRI2 when compared to DRI1 is that it appears to give poor benchmarks on simple rendering operations such as glxgears, but gives superior performance on real-world operations (such as games).

The only thing you need to verify is whether direct rendering is enabled (I imagine it is):
```
$ glxinfo | grep direct
```

Some better information on glxgears in conjunction with DRI2: [http://qa-rockstar.livejournal.com/7869.html](http://qa-rockstar.livejournal.com/7869.html)

---

### Post by svaens on 2010-03-14
So, while you've told me I shouldn't expect a detailed response to my query, you have in fact, kind sir, given me about as detailed explanation as I need (or would, in fact, understand). 

So, thank you for the information. I do wish I could be of some help in the whole development process. And I did just think that if I install it and put it out there exactly what things I am seeing, some extra bugs might get fixed which could help a lot more people than just myself. I get the feeling I am not yet achieving any results through my otherwise good intentions. 

It would be good if there were (or perhaps there is, but I haven't come across it yet) some kind of template of tests that people could run on their hardware so that the sort of bugs that turn up in the first weeks of the final release get caught instead at the alpha or beta stages. 

If any of you know how I can better put my alpha partition to better use, i'd be open to suggestions.

---

### Post by seeker5528 on 2010-03-15
Phoronix did some benchmarks with different kernels in Lucid using ATI for the Video portion and shows 2.6.32.9 getting some better performance than the kernels before and after it.

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_lucid_kernels&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_lucid_kernels&num=1)

Later, Seeker

---

