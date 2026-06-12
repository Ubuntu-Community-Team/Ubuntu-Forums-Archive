---
title: "Edgy crashes on stage 5 of 6 of installer (partitioning)"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by gammyhand on 2006-11-13
Hi,

I am trying to install 6.10. I currently have 5.04 installed and put in the 6.10 ISO I burnt (I checked the CD integrity and no errors).

It loads up fine and the installer process starts fine when double clicked on on the dekstop but when it gets to the partitioning stage it just gives up and I have to hard reboot as my hdd just sits there "ticking".

Anyone know how I can solve this? There is nothing wrong with my disk and 5.04 partitioned fine.

---

### Post by taurus on 2006-11-13
Try the alternate CD version since you have more control when you get to the partition part.  Again, don't forget to burn it at a slower speed like 4x.

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by gammyhand on 2006-11-13
All I am seeing on this problem is "try the alternate cd" so I have a couple of questions:

1) Why is it not mentioned on ubuntu site that you might well be wasting 2 hours downloading a CD that does not work

2) Why is the live/installer CD not still in beta? Surely the fact that you can't install the damn OS would count as a pretty major bug?

---

### Post by taurus on 2006-11-13
First of, I never use the desktop CD/LiveCD so I can't tell you why it's not installing on your machine.  I believe the main function of the LiveCD is for people to do a quick test drive of Ubuntu to see if they like it or not.  Also, a LiveCD is real handy to have in case you need to fix something on your Ubuntu (harddrive) when you can't boot with it.  I personally always use the alternate CD and never have any problem.  I like to partition my harddrive certain way and mount others in a certain areas so the alternate CD is an ideal for me.  So, you can try to get the LiveCD to work on your machine or you can try the alternate CD.  It's up to you.

---

### Post by gammyhand on 2006-11-13
Well you completely disagree with what the official UBuntu site has to say on the issue!

They say that the desktop CD is to try it and then install it from the desktop on there and that the alternate cd is for people with special requirements (network install, low RAM etc).

I appreciate that a lot of people have inside knowledge or a sixth sense but it is not doing the Ubuntu image any good.

I am fuming. I really needed a working system tonight and now I will have to sort it tomorrow night when I am supposed to be going out.

---

### Post by taurus on 2006-11-13
You don't have to believe me if you don't want to.  But a lot of people can't boot their machine using LiveCD because of graphic card that they have.  However, when they use the alternate CD to install, the whole thing works just fine since the alternate CD uses text mode...  Again, it's up to you if you want to figure out how to get the LiveCD to install on your machine or you can switch to the alternate CD.

---

### Post by gammyhand on 2006-11-13
I am not saying I don't believe you. I do. I questioned how first time installers and especially new users to ubuntu will know about this.

From my point of view I have wasted an evening downloading the ISO and trying to get it to install when I could have been told about this on the download page and had the choice of whether to risk the live cd (which says it is the install cd, not just the live cd) or download the alternate cd.

How many ubuntu virgins do you think will bother going to the alternate CD if the live doesn't work and how many do you think will just abandon it?

---

### Post by taurus on 2006-11-13
You now know there is another option so you can call in question whatever info or page you want.  I am not going to debate with you since I have better things to do.  And if you think they misled you, contact them directly and let them know...  All I can tell you is to try the alternate CD to see if you can install Edgy on top of your old Ubuntu version.

---

### Post by gammyhand on 2006-11-14
I have better things to do to be honest. I am just gonna use a different distro after one last attempt at the desktop CD tonight. It is advertised as a fully working CD designed for installing Ubuntu and if even the install procedure has problems then god knows what will happen if I do get it installed (before you fly off the handle, I don't mean Ubuntu is rubbish but if my machine doesn't even like the installer I don't fancy my chances on the actual OS.

---

### Post by mips on 2006-11-14
I myself never use the live/desktop cd. The first & last time I did it formatted a partition I did not select, I was fuming mad to say the least. Stick to alternate cd.

You should take the issue up with Ubuntu/Canonical.

When you insert the cd you get a **boot:** prompt, at this stage there are various parameters you can specify like video modes, advanced power management etc. If i was you I would try and get a list of these parameters somewhere and try booting with them.

---

### Post by gammyhand on 2006-11-14
> **mips said:**
> I myself never use the live/desktop cd. The first & last time I did it formatted a partition I did not select, I was fuming mad to say the least. Stick to alternate cd.

You should take the issue up with Ubuntu/Canonical.

When you insert the cd you get a **boot:** prompt, at this stage there are various parameters you can specify like video modes, advanced power management etc. If i was you I would try and get a list of these parameters somewhere and try booting with them.
I agree. But I don't know the commands to use on the boot prompt. Even hoary had a graphical install method on its install CD.

---

### Post by mips on 2006-11-14
Google- Linux BootPrompt

---

### Post by gammyhand on 2006-11-14
Thanks, will have a look....is there a way to use the boot prompt to get a guided install on the alternative cd? (stuff like auto config of video, date/time, network etc?

---

### Post by mips on 2006-11-15
> **gammyhand said:**
> Thanks, will have a look....is there a way to use the boot prompt to get a guided install on the alternative cd? (stuff like auto config of video, date/time, network etc?

I honestly dont know but i'm sure it's possible.

---

