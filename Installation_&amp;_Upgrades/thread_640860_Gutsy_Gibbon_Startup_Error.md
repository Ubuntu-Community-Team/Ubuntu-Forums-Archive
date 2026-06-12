---
title: "Gutsy Gibbon Startup Error"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by Fzero on 2007-12-14
Today I decided to install Ubuntu 7.10 Gutsy Gibbon so I created a partition through the Ubuntu setup. The partition seemed to be created without any problems and so did the installation. But when I tried to boot into Ubuntu through the GRUB menu I got this error message.

I'm using a Toshiba Satellite  M40X Laptop.

Sorry about how blurry it is, I had to take it on my phone :p

Caution 56K users

[URL="http://img527.imageshack.us/img527/9646/photooflinuxku5.jpg"]Link
[/URL]

Here's another picture of after I waited a while to see if anything happened. [Link]("http://img145.imageshack.us/img145/3339/dsc00017filteredvb5.jpg")

I tested out running Windows XP after this and it was able to run perfectly. I also tested the Ubuntu recovery mode and it worked fine.

---

### Post by Sef on 2007-12-14
Is your screen resolution set the right specs?  System > Preferences > Screen Resolution.

If you have tft monitor (the thin ones), there is one setting that is the right one.  If you have one, what should the resolution be?

---

### Post by Fzero on 2007-12-14
My screen resolution is 1280x800 if that's what your wondering. Also I have installed Ubuntu Feisty Fawn and Gutsy Gibbon before so I don't understand why I have a problem.

---

### Post by Fzero on 2007-12-14
Bump

---

### Post by PmDematagoda on 2007-12-14
Not entirely sure if it would solve your problem, but did you check the Live CD for errors? 

At what speed did you burn it? 

Also did you try verifying the downloaded image file by checking it's MD5 sum?

---

### Post by Fzero on 2007-12-16
Bump

---

### Post by PmDematagoda on 2007-12-16
You still did not answer my questions, may be if you answered them I could help you out with your problem.

---

### Post by Fzero on 2007-12-16
I did check for defects and there were none. I think I wrote the image at the fastest speed.

---

### Post by PmDematagoda on 2007-12-16
If you wrote the CD at the fastest speed(I am assuming that it may be 52X), then you may have corrupted your Live CD.

Burn the Live CD at a speed of 4X or lower **only**, a greater speed can cause the created Live CD to be corrupted which can cause some weird problems such as the one you are having right now.

---

### Post by Fzero on 2007-12-16
Thanks for the advice I hope it works.

---

### Post by nowshining on 2007-12-16
i hope u get ur problem sorted out, let us know.

---

### Post by Fzero on 2007-12-16
I wrote the image at a slow speed and then checked for errors but I still get the error.

---

### Post by Fzero on 2007-12-16
Bump

---

### Post by Dryw Paulic on 2007-12-16
Hey Fzero (Great vid game, btw),

First Suggestion: Are you using any PCMCIA cards or any other external devices with the laptop during bootup? If so, try removing them and booting up again. 

Secondly, I found a posting regarding this particular error:

[http://lists.infradead.org/pipermail/linux-pcmcia/2007-June/004772.html](http://lists.infradead.org/pipermail/linux-pcmcia/2007-June/004772.html) 

To summarize:It looks like it's a known driver issue in Kernel version 2.6.22. There is a patch available, but I'm not sure if it's been merged into the tree yet. You may want to try downgrading to version 2.6.21 or applying the patch to your kernel sources to see if that allows you to boot. One *really* easy way to test would be to whip out a an older copy of ubuntu that uses a different kernel version to see if you get the same error.

The other option (if you don't use the infrared port) that may work would be to disable the loading of the infrared drivers on bootup.

-Dryw

---

### Post by Fzero on 2007-12-17
Yep it is a great game, now back on topic

I have used Gutsy before but it was one of the beta versions and it worked fine. Does it have a different kernel then the official 7.10?

( If it helps I do have an infrared port )

---

### Post by ubuntu_demon on 2007-12-20
Maybe you did a command line installation ?
Can you login after pressing enter or going to ctrl-alt-f2 ?

---

### Post by Dryw Paulic on 2007-12-20
Hi Fzero,

I forgot to ask this as well - - does booting up in recovery mode work properly?

Cheers,

Dryw

---

