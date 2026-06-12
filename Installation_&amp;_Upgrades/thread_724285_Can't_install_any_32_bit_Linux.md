---
title: "Can't install any 32 bit Linux"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by sclewis12 on 2008-03-14
Specs.
amd 5000 on an asus mobo with the amd 690g chipset. The onboard video is disabled, and I have a 7800gt for the video card. 4 gigs of ram.

I can install 64 bit Ubuntu 7.10 with no problem. But then I can't get any graphics drivers to work.

I can't even live boot any version of 32 bit Ubuntu. I get an error every time.
I also tried 32 bit suse just for troubleshooting purposes. Same problem.
I also tried the alternate install CD's with no luck. 

Is there known issues with this chipset and 32 bit debian linux?
I tried searching for anyone with the same issue with no results.

I do have 7.10 running on my laptop (amdturion) and my work pc, (AMd 3800 nforce4)

The computer also runs sata 300, could this be the issue?

I know everyone will probably tell me it's my graphics, I do not think this is the case. I think the error message said something about failure to load pci1.

I am going to try my other graphics card i know works, just so I can see it's not the graphics card.

---

### Post by Kerin on 2008-03-15
Without concrete information on the error, diagnosing your problem's going to be pretty difficult.  Mind getting that for us?

I have an 8800GTS, and a friend of mine uses a 6800GS - nVidia cards are pretty well-supported in linux, so unless your specific video card is defective it's unlikely to be at fault.

---

### Post by Pumalite on 2008-03-15
Try installing with 2 GB of RAM

---

### Post by Peter09 on 2008-03-15
what is the model of your mother board

PC

---

### Post by Peter09 on 2008-03-15
Look at this thread, see if its appropriate.

[https://answers.launchpad.net/ubuntu/+question/8921](https://answers.launchpad.net/ubuntu/+question/8921)

PC

---

### Post by sclewis12 on 2008-03-17
> **Peter09 said:**
> Look at this thread, see if its appropriate.

[https://answers.launchpad.net/ubuntu/+question/8921](https://answers.launchpad.net/ubuntu/+question/8921)

PC
WOW!
That is the motherboard in question. Thank you so much!
I was seriously going to go build another pc just to install Linux.

Now all I have to do is try and get it to work. I'm pretty good with computers, but am still new to linux.

Thanks for the help.

---

### Post by sclewis12 on 2008-03-17
I just want to say thanks. With all the questions that come through here it is hard to believe that this many people took the time to answer my question.

I answer posts at the ATI forum all the time, and I posted a question about ATI and compiz. Basically I was just wondering if everyone had the slow scrolling issues under mozilla with ATI 2x00 series cards with compiz enabled.
It has been 3 weeks and no one has replied once.

I guess the Ubuntu community is where it's at.
So thank you all.

---

### Post by sclewis12 on 2008-03-18
It worked. And now the Nvidia drivers work.

All I need to figure out is how to get twinview working correctly. 
I tried extended but for some reason the first screen was set to the right resolution. But the screen was actually larger than the panel. I have to pan to see parts of it.

---

