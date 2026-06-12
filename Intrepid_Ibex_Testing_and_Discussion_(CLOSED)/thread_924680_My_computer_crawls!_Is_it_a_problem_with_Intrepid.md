---
title: "My computer crawls! Is it a problem with Intrepid?"
date: 2008-09-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Bou on 2008-09-19
Hi,

I recently bought a new [laptop]("http://www.arqui.com/arquitienda/producto.asp?pad=21&seccion=26&hseccion=495&nseccion=&id=8716&marca=&promociones=") and started testing Intrepid a few days ago. Now I'm having serious performance problems, compiz is for example far slower now than in my 3-year-old previous laptop.

If I visit a page with flash content the computer stops to a crawl. [This page]("http://fboiso.blogspot.com/2007/04/armas-prohibidas.html"), for example, makes htop show this:

[[img]http://img58.imageshack.us/img58/5960/pantallazoterminal1ev6.th.png[/img]](http://img58.imageshack.us/my.php?image=pantallazoterminal1ev6.png)

I really need to find out whether this problem is software or hardware related, so I can either return the computer to the store or file a bug. I hope you guys can give me a hand with this.

---

### Post by Nullack on 2008-09-19
What gpu do you have?

What video driver is installed?

Have you run top to get an idea of the performance profile while the problem occurs?

---

### Post by Bou on 2008-09-19
> **Nullack said:**
> What gpu do you have?

I've got a Nvidia Geforce 8400M.

> **Nullack said:**
> What video driver is installed?

Nvidia-glx-173.

> **Nullack said:**
> Have you run top to get an idea of the performance profile while the problem occurs?

I thought htop gave you more info, actually.

---

### Post by pdq on 2008-09-19
Try to identify the bottle neck.  Start by watching the system monitor to see if the CPU is flooded.

Next thing I would check is how fast your hard drive is reading at.

sudo hdparm -t /dev/sdb1

change sbd1 do whatever your drive is listed as (by typing sudo fdisk -l).

I'm no expert, but I would start there.

---

### Post by Nullack on 2008-09-19
dont use system monitor it adds too much overhead - top

---

### Post by pdq on 2008-09-19
> **Nullack said:**
> dont use system monitor it adds too much overhead - top

True.  I run conky for general stuff.  For more details on processes I use top.

---

### Post by psyke83 on 2008-09-19
> **Bou said:**
> Hi,

I recently bought a new [laptop]("http://www.arqui.com/arquitienda/producto.asp?pad=21&seccion=26&hseccion=495&nseccion=&id=8716&marca=&promociones=") and started testing Intrepid a few days ago. Now I'm having serious performance problems, compiz is for example far slower now than in my 3-year-old previous laptop.

If I visit a page with flash content the computer stops to a crawl. [This page]("http://fboiso.blogspot.com/2007/04/armas-prohibidas.html"), for example, makes htop show this:

[[img]http://img58.imageshack.us/img58/5960/pantallazoterminal1ev6.th.png[/img]](http://img58.imageshack.us/my.php?image=pantallazoterminal1ev6.png)

I really need to find out whether this problem is software or hardware related, so I can either return the computer to the store or file a bug. I hope you guys can give me a hand with this.

Bou, I wouldn't send that laptop back quite yet. I can't give you specific bug reports, but I'm also noticing a very strange performance regression on my system (Dell Dimension 1100, a desktop system). It's not due to a graphics driver, but seems to be kernel related.

As for Flash, the version in Intrepid is actually quite buggy and saps 100% CPU on certain flash content (again, it's not the fault of your laptop).

---

### Post by ronacc on 2008-09-19
try the nvidia-glx-177 driver and flash 10 , attached is a screenshot of top with the page you linked to open in firefox .

---

### Post by cevans on 2008-09-19
> **Nullack said:**
> What gpu do you have?

What video driver is installed?

Have you run top to get an idea of the performance profile while the problem occurs?

I'm a bit confused: did Bou edit his post to add the htop screenshot, or did everyone just ignore it?

Bou, disregard the points about top; htop is almost the same and should be fine here. Notice that X is taking up a huge portion of the cpu (essentially saturating one core). Have you tried disabling compiz, to see if it is something compiz-specific? You might also want to look at how well something like glxgears -printfps works, or the output of glxinfo; it would be my guess that this is some sort of video driver problem, which is the sort of thing that compiz tends to bring out. I would try seeing if flash without compiz works better.

And of course, you can always try gnash.

Editing again: Bizarrely enough, my laptop mainly has problems with flash *on that page*. Have you tried other flash videos?

---

### Post by Nullack on 2008-09-20
Perhaps if you knew more about top you would comprehend why it is a more informative tool by far than htop which has only simple utlisation metrics.

EDIT: Ronacc's right on the money - give the 177 beta a go until flash gets updated in the repos.

---

### Post by cevans on 2008-09-20
> **Nullack said:**
> Perhaps if you knew more about top you would comprehend why it is a more informative tool by far than htop which has only simple utlisation metrics.

X is saturating one of the cpus. If it wasn't clear, then certainly, things like iowait might be useful.

---

### Post by Nullack on 2008-09-20
> **cevans said:**
> X is saturating one of the cpus. If it wasn't clear, then certainly, things like iowait might be useful.

One of the benefit with top is that is breaks down the cpu utilisation into more specific areas. Top provides more meaningful details for this problem. As per Ronaccs post.

---

### Post by Bou on 2008-09-20
I've just realized something: if I use the open nv driver, my laptop's performance seems to be OK. Only, then I can't use compiz. I'll do some more tests later -I can't right now- but, based on that, what do you think I should do?

---

### Post by ronacc on 2008-09-20
hmm so many directions to go , until you isolate what is causing the problem , try the 177 driver, try flash 10 , try blocking flash , try the nvidia driver(s) without compiz , install nvidia-settings and see if anthing looks "wrong" , is it only when you have a page open with flash that things go bad ? try a different browser , are your powermanagement settings too agressive ? has the problem been there from the start or did it begin after an update ? are you using the default xorg.conf or a custom one ? the default works best with the new xorg for most people but some laptops seem to need some tweaks ( for the touchpad I believe , i'm on a desktop so I can't say for sure) .

---

### Post by psyke83 on 2008-09-20
> **ronacc said:**
> hmm so many directions to go , until you isolate what is causing the problem , try the 177 driver, try flash 10 , try blocking flash , try the nvidia driver(s) without compiz , install nvidia-settings and see if anthing looks "wrong" , is it only when you have a page open with flash that things go bad ? try a different browser , are your powermanagement settings too agressive ? has the problem been there from the start or did it begin after an update ? are you using the default xorg.conf or a custom one ? the default works best with the new xorg for most people but some laptops seem to need some tweaks ( for the touchpad I believe , i'm on a desktop so I can't say for sure) .

Yeah... what he said ;)

However, I can't emphasize enough the terrible performance of the older flash beta in the official repository. Keep an eye on the [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=866965") thread for Flash news. An official update will come in a little while, but the new version of flash is already in my PPA if you want to test (and diagnose a possible source of your problem).

Additionally, this thread is vital for NVIDIA users: [http://www.nvnews.net/vbulletin/showthread.php?t=118088](http://www.nvnews.net/vbulletin/showthread.php?t=118088)

---

### Post by ronacc on 2008-09-20
the default seems to work best for most people (attached) , did you enable the driver in system>administration>hardware drivers or just install it via synaptics or apt-get ?

---

### Post by ronacc on 2008-09-20
> **ronacc said:**
> the default seems to work best for most people (attached) , did you enable the driver in system>administration>hardware drivers or just install it via synaptics or apt-get ?

ignore this I posted it to the wrong thread, sorry

---

### Post by plun on 2008-09-20
> **ronacc said:**
> the default seems to work best for most people (attached) , did you enable the driver in system>administration>hardware drivers or just install it via synaptics or apt-get ?

Yup, with a clean alpha 6 it was so at least for me. 

Some minor works remains which Alberto looks at.

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/272238](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/272238)

The MMI/UI can be discussed. :)

Something was broken with earlier releases.

---

### Post by philinux on 2008-09-20
> **Bou said:**
> If I visit a page with flash content the computer stops to a crawl. [This page]("http://fboiso.blogspot.com/2007/04/armas-prohibidas.html"), for example.

Great track there. Interesting thing, I've got compiz on and the 177 driver. loading that page does not make my pc crawl however system monitor does show that flash is intensive on cpu as we all know. The interesting thing is that when I scrolled down the page which left the flash playing but not in view the cpu maxes out. With the video in view a cyclic behaviour is the norm. Odd.

---

### Post by Bou on 2008-09-20
> **ronacc said:**
> hmm so many directions to go , until you isolate what is causing the problem , try the 177 driver, try flash 10 , try blocking flash , try the nvidia driver(s) without compiz , install nvidia-settings and see if anthing looks "wrong" , is it only when you have a page open with flash that things go bad ? try a different browser , are your powermanagement settings too agressive ? has the problem been there from the start or did it begin after an update ? are you using the default xorg.conf or a custom one ? the default works best with the new xorg for most people but some laptops seem to need some tweaks ( for the touchpad I believe , i'm on a desktop so I can't say for sure) .

I think most of these things don't address the real problem. It's not a problem with flash I'm having, it's a general sluggishnesh when I'm using the nvidia driver. Noticeable when I'm switching tabs and stuff, annoying when I use compiz, and outrageous when I visit flash sites. But after using nv for a while I'm sure of it, the nvidia driver is to blame.

As for some specific questions you made:

> **ronacc said:**
> try the 177 driver

I will and report back.

> **ronacc said:**
> try the nvidia driver(s) without compiz

I was, actually, using that when I wrote the first post. Same problems still apply.

> **ronacc said:**
> has the problem been there from the start or did it begin after an update

Well, this is a new computer so I guess it's been there from the start. That's not long ago, though.

> **ronacc said:**
> are you using the default xorg.conf or a custom one ?

Default one. I only added the "driver &#8594; nvidia" line.



So, supposing it's a driver problem and considering that they're closed, is there even a point in filing a bug against the package? Is there anything I should do to get it fixed?

---

### Post by psyke83 on 2008-09-20
> **Bou said:**
> I think most of these things don't address the real problem. It's not a problem with flash I'm having, it's a general sluggishnesh when I'm using the nvidia driver. Noticeable when I'm switching tabs and stuff, annoying when I use compiz, and outrageous when I visit flash sites. But after using nv for a while I'm sure of it, the nvidia driver is to blame.

The nvidia driver has serious 2D performance issues with the 8/9xxx series.

There is a very large thread dealing with the issue here: [http://www.nvnews.net/vbulletin/showthread.php?t=115916](http://www.nvnews.net/vbulletin/showthread.php?t=115916)

The 177 driver addresses these issues (for all cards supported), but you need to enable "experimental" options manually. As I said, this is the thread you need to see: [http://www.nvnews.net/vbulletin/showthread.php?t=118088](http://www.nvnews.net/vbulletin/showthread.php?t=118088)

---

### Post by ronacc on 2008-09-20
> **Bou said:**
> I

Default one. I only added the "driver &#8594; nvidia" line.



So, supposing it's a driver problem and considering that they're closed, is there even a point in filing a bug against the package? Is there anything I should do to get it fixed?

hmm I suspicious of that , it should have been done for you when you enabled the driver through system>administration>hardware drivers , you did do it that way didn't you ?

the rest of the suggestions I was just throwing out things to try so we could see where the problem was .

---

### Post by Bou on 2008-09-20
> **ronacc said:**
> hmm I suspicious of that , it should have been done for you when you enabled the driver through system>administration>hardware drivers , you did do it that way didn't you ?

Jockey crashes on my computer, so I had to install and enable the drivers by myself.

> **ronacc said:**
> the rest of the suggestions I was just throwing out things to try so we could see where the problem was .

Yeah thanks, I didn't want to sound rude or anything, just to make clear mine is a driver problem, not a flash problem :)

---

### Post by Miguel on 2008-09-20
Hi Bou,

I don't know how bad is the 2D performance issue with recent nVidia cards, since I've always suffered from slow 2D and 3D in fglrx. However, if you want to discard a faulty gfx card, try to run something GPU-intensive. Maybe openarena in high resolution, or the Quake4 demo, or something similar. You may also want to have a look at the phoronix test suite.

Also, if you still have the windows partition, you may also want to try a demo of a recent game there in order to see if it's properly working in other OSes.

OT: I attended a conference in Valencia last week and had a great time! The oral sessions took place in the ADEIT building near the cathedral, so you can imagine we visited Carrer Cavallers often when the talks were over. We were surprised to see brazilian girls and guys at the Johnny Maracas too!

---

### Post by ronacc on 2008-09-20
did you install the drivers from synaptics or nvidia.com ? the drivers from nvidia have to be edited for the new kernel and xorg , this has been done for the ones from synaptic that is whay that way is better right now. I don't know about the latest 177.76 version mabye nvidia has adjusted that one , you might want to try that one , see this link.
[http://www.nvnews.net/vbulletin/showthread.php?t=119682](http://www.nvnews.net/vbulletin/showthread.php?t=119682) 
that link was provided by steveway in another thread .

---

