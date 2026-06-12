---
title: "Install Ubuntu on Dell XPS M1330 Media Direct Partition"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by michae1duc on 2008-09-25
(Newbie)

I would like to install Ubuntu on my Dell M1330 on the partition that is currently storing the Dell Media Direct software.  

Dell Media Direct looks like a lightweight operating system that has a media player, dvd player, etc. and it's about 3gb, so it will probably need to be resized as well.

Ultimately, I would like to be able to launch Vista using the power button (without bringing up an OS boot menu), or launch directly into Ubuntu by pressing the Media Direct button.

Is this possible?

Thanks!

---

### Post by oilchangeguy on 2008-09-25
> **michae1duc said:**
> (Newbie)

I would like to install Ubuntu on my Dell M1330 on the partition that is currently storing the Dell Media Direct software.  

Dell Media Direct looks like a lightweight operating system that has a media player, dvd player, etc. and it's about 3gb, so it will probably need to be resized as well.

Ultimately, I would like to be able to launch Vista using the power button (without bringing up an OS boot menu), or launch directly into Ubuntu by pressing the Media Direct button.

Is this possible?

Thanks!


is there a special reason you don't want to install it on the c: partition?

---

### Post by michae1duc on 2008-09-25
> **oilchangeguy said:**
> is there a special reason you don't want to install it on the c: partition?


I want to avoid the boot screen where you have to choose an OS.  Also, I don't use the Media Direct function and I would rather use the button to launch Ubuntu.


When I press the power button now it boots directly in Vista, and when I press the Dell Media Direct button it boots directly into Dell Media Direct.

I spent a good bit of money on a new laptop and want it to boot as quickly as possible, but also want to learn how to use linux on the same machine.

If anyone has tried this same setup and can give any advice, it would be greatly appreciated.

---

### Post by werries on 2008-09-25
Dude. good idea. I wish I knew how to do that. I've got the same feature on my laptop. But then again..i run only ubuntu...so....

---

### Post by michae1duc on 2008-09-25
Thanks, I found another thread about it on another site... [http://forums.techguy.org/unix-linux/569616-vista-ubuntu-linux-dule-boot.html](http://forums.techguy.org/unix-linux/569616-vista-ubuntu-linux-dule-boot.html) but I don't think anyone ever came up with a solution.

They also linked to this site talking about an HPA... [http://www.goodells.net/dellrestore/mediadirect.htm](http://www.goodells.net/dellrestore/mediadirect.htm)  that explains how the Dell Media Direct partition is set up.  (I don't have a computer science degree, so this is beyond me)

I like Microsoft, and even if their software has flaws, I don't think I'll be giving up Windows completely anytime soon.  I've tried various linux distributions on my old p.o.s. laptop, and I'm really looking forward to using Ubuntu on a decent piece of hardware on a regular basis. 


What I love about Ubuntu, and the open-source community in general, is that I can post a question like this, and people with similar experiences will actually reach out and help each other!

I'm looking forward to all of your responses, and thank you (in advance) to the uber-nerd (I'm a nerd too, so I don't mean that in a derogatory way) who posts step-by-step instructions on how to make this work.

Thanks again - Michael

---

### Post by werries on 2008-09-27
It looks like the media direct partition is set up on a truly hidden partition. explains why it still boots on my system. ( i accidentally hit my button, was confused as to why it was still there, and ignored it.)
However, you would have to figure out the size of your HPA in order to know if you can unhide it and then install linux onto it. 
That would require taking what your harddrive size is supposed to be, doing a bit of math from decimal to bits, and then finding out the space is actually there. You then take the actual size, subtract the size reported by the OS, and you then have the size of your HPA. :)

---

### Post by showcaser on 2008-10-10
I got my M1330 last February and immediately wiped it clean and set it up the way your describing. Hitting the power button starts vista directly, and hitting the media direct button starts up ubuntu directly. problem is I don't remember how I did it.

The reason I came upon this thread is I want to do a clean install of Intrepid beta. (tried the dist upgrade but a few things went wonky) and don't remember which partition grub has set as the active drive.

From what I remember I followed instructions that are out there for triple boot (Vista, Ubuntu, MD). The trick afterwords is that there's a command you can enter (from where I can't remember) which re-assigns what partition the MD button will load. My partition setup when all was said and done is (50mb fat16, 150gb Vista, 45gb Ubuntu, 3GB swap).

I'll look around a bit to try and jog my memory and get back to you if anyone is still interested.

---

