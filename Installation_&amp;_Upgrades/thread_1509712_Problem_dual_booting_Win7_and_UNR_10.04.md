---
title: "Problem dual booting Win7 and UNR 10.04"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by JasonGW on 2010-06-14
I've worked in IT for 15 years supporting Windows/DOS systems, but really only ever dabbled in Linux very lightly. Therefore, I'll just admit it upfront: I'm a Linux n00b. Please forgive me.

In any case I was so impressed with UNR booting it off a USB stick on my netbook that I decided I would install it on my netbook to run alongside my install of Windows 7 Professional. Doing a little quick reading, I came across several sites that basically said the same thing: create some free space, let UNR use that free space, and it'll do all the magic of setting up your dual boot with Windows no problem. So I used GParted to shrink my Windows partition from 160GB to 95, and let UNR use the free space to install, expecting it to auto-create the dual boot GRUB menu.

Problem is, it didn't. Instead, I've got a fully functional UNR--which is nice and I like it a lot--but I don't even get an option to boot to Windows. Tried doing a repair install with my Win7 USB stick and it says Win7 can't use the partition because it's the GPT type. The Disk tool in UNR claims it doesn't know what the Windows partition actually is.

So at this point I'm stuck, and in spite of a week's worth of googling I appear to be no closer to an answer, so I throw myself at the mercy of the Linux community. Help, please? :smile:

Thanks!

Jason
 
Posted this in the hardware/laptops section figuring that was appropriate (since I'm using it on a laptop, you know) but can't seem to get a response. Might as well try the installation forum, I suppose.

---

### Post by oldfred on 2010-06-15
Post this. If you have GPT partitioning that is more like the apple system have. Do you then have a BIOS boot partition? I thought windows would not boot from GPT, but there are some mixed versions also.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by JasonGW on 2010-06-15
> **oldfred said:**
> Post this. If you have GPT partitioning that is more like the apple system have. Do you then have a BIOS boot partition? I thought windows would not boot from GPT, but there are some mixed versions also.
 
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.
 
I'll try that out. What I can tell you is this: It wasn't GPT before I installed UNR (you're right, Win7 will not boot from GPT. In fact, no version of Windows will, at least not to my knowledge.) but I have no idea why UNR would make that change. Perhaps I should boot with GParted and switch it back to MBR...
 
Thank you for your reply! :)

---

