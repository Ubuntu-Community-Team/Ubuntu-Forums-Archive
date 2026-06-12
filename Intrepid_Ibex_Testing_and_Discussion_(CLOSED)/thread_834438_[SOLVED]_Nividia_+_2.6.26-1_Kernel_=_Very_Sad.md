---
title: "[SOLVED] Nividia + 2.6.26-1 Kernel = Very Sad"
date: 2008-06-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by vbman11 on 2008-06-19
Hi all!
   So I don't consider myself a beginner, but this question probably
has a simple answer to it.  I decided to try out intrepid one day and so I "installed" it on to another partition on my hd.  Then I updated to the 2.6.26-1 kernel which messed up my Nvidia settings(6150 SE Integrated). But wait THERES MORE! After that I figured out I needed to patch my Nvidia dirvers. Well I didn't want to do that so I just removed the 2.6.26-1 kernel. Then I decided to reinstall the 2.6.24-19 kernel so I removed It but couldn't reinstall because synaptic says it has no version. So now I'm stuck in low graphics mode in the 2.6.24-16 kernel.

PLEASE HELP ME!:(
I was thinking I could just do a dpkg-reconfigure to the nvidia-glx-new package? Would that work?:confused:

---

### Post by Eclipse. on 2008-06-19
There is no -19 in intrepid.Theres only the stock 24-16 and 26-1.

But seriously, if you cant fix simple driver things then you should stick to hardy, alpha 1 isnt even out yet.

---

### Post by forestpixie on 2008-06-19
> **Eclipse. said:**
> There is no -19 in intrepid.Theres only the stock 24-16 and 26-1.

But seriously, if you cant fix simple driver things then you should stick to hardy, alpha 1 isnt even out yet.

+1

Or at the very least not put questions here, there is a forum for it

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

---

### Post by Technoviking on 2008-06-19
Thread moved.

---

### Post by vbman11 on 2008-06-19
First of all: Thanks for moving the thread.

Second: I thought(correct me if I'm wrong) a forum was for asking questions that one doesn't already know the answer to.

Third: I am using Intrepid because I want to learn, because I happen to have a computer that works perfectly in Hardy even in the beta of Hardy, and I wanted to have problems so I could learn.

So if someone could answer my question or direct me to a webpage that would help that would be great. And PLEASE don't send me a link to a wiki page on programming or on reverse engineering. I hate when people do that.

---

### Post by Raptor45 on 2008-06-19
The development version, especially in the pre-alpha stage, is not really the best idea for learning. A large amount of troubleshooting, and a good bit of know-how is required just to keep things kinda-working. You should never remove an old kernel until you have made sure the new one works.

That said, at this point, theres no real easy way to get the old kernel back... as that was the hardy kernel. I'd recommend either reinstalling from scratch, or just using the vesa or nv drivers for now.

---

### Post by Eclipse. on 2008-06-19
I would just stick to using hardys relase kernel and work from there.

Alot of problems are normally kernel orientated and thats the easiest way to avoid them.

---

### Post by vbman11 on 2008-06-19
Thanks for replying Raptor! I just ended up reinstalling hardy then intrepid. But the 2.6.24-19 & the 2.6.24-16 kernels were both effected by installing 2.6.26-1, and I only removed the -1 and the -19. I still had the -16, which (btw) worked perfectly before -1. Again thanks for replying!:)

---

### Post by psyke83 on 2008-06-19
> **vbman11 said:**
> First of all: Thanks for moving the thread.

Second: I thought(correct me if I'm wrong) a forum was for asking questions that one doesn't already know the answer to.

Third: I am using Intrepid because I want to learn, because I happen to have a computer that works perfectly in Hardy even in the beta of Hardy, and I wanted to have problems so I could learn.

So if someone could answer my question or direct me to a webpage that would help that would be great. And PLEASE don't send me a link to a wiki page on programming or on reverse engineering. I hate when people do that.

The Intrepid Testing & Discussion section is *not* the same as the Absolute Beginner section. What that means is that we are not here to spoon-feed users than do not know the fundamentals of how to maintain their system.

I understand that you want to learn, but you need to become self-sufficient in order to test the development release, especially if you begin testing so early in the development process - there hasn't even been an alpha release! You need to read 23meg's sticky threads, carefully. They are being edited for Intrepid, so you can see the old threads for Hardy, linked to the first post here: [http://ubuntuforums.org/showthread.php?t=826197](http://ubuntuforums.org/showthread.php?t=826197)

Finally, learn to search the forum rather than posting new threads - as I type, there is a thread about the NVIDIA driver literally two posts below yours (I'll forgive you this time, only because you first posted in a different forum ;)).

---

### Post by Raptor45 on 2008-06-19
> **vbman11 said:**
> Thanks for replying Raptor! I just ended up reinstalling hardy then intrepid. But the 2.6.24-19 & the 2.6.24-16 kernels were both effected by installing 2.6.26-1, and I only removed the -1 and the -19. I still had the -16, which (btw) worked perfectly before -1. Again thanks for replying!:)

Did you update hardy before moving to intrepid? That can cause problems at this point. The best way to move to intrepid is off a fresh install of hardy. Updating hardy first can cause versioning issues if the intrepid version has not caught up yet. (Essentially intrepid is forked off the release version of hardy, and does not necessarily have packages which are as up to date.) You may not actually see issues, but I don't think its recommended.

If thats not the case sorry; but I dont see why else you'd have the -19 around.

---

### Post by vbman11 on 2008-06-20
I fixed it myself. And yes I did update hardy then install intrepid

---

