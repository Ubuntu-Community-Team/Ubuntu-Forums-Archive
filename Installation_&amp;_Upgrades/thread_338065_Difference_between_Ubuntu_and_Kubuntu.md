---
title: "Difference between Ubuntu and Kubuntu"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by Mr. Doom on 2007-01-13
I read a thread where a gentleman asked this question and no one answered it. All they said was try both and see what you think. (I'm paraphrasing) Sooo, what are the differences...one is more suited for business and the other for home. Or one is more suited for newbees and the other for seasoned folks. I'm using Ubuntu now but would like to know if and why I would try Kubuntu.
Thanks, Mr. Doom

---

### Post by NeoLithium on 2007-01-13
The difference is basically the desktop environment it uses.  There's of course a few applications that aren't interchangable; but if you want to try it out without downloading a whole CD; you can 
```

sudo aptitude install kubuntu-desktop

```

If you don't like KDE; then you can just simply remove it.

---

### Post by Sef on 2007-01-13
If you are starting off with GNU/Linux, then Ubuntu is better because more people here use it, so questions tend to get answered faster.   After you feel comfortable, then try kubuntu.

---

### Post by Mr. Doom on 2007-01-13
That's nice but I'm still not understanding what the differences are. Why would I use one and not the other?????????????

---

### Post by aysiu on 2007-01-13
> **Mr. Doom said:**
> That's nice but I'm still not understanding what the differences are. Why would I use one and not the other?????????????
Read this:
[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

---

### Post by Mr. Doom on 2007-01-13
10 years ago I needed to learn unix to run our companies very old system. A friend said get Linux to help. It did. I learned it from the CL. SMB FTP and all. But that was 10 years ago and I want to get back into it but most of the forums I go to don't seem to be interested in answering the the questions I ask they just say "Use the CL". SOMEONE ANSWER THE QUESTION I ASKED! Sorry for yelling...

---

### Post by NeoLithium on 2007-01-13
As everyone constantly says; the differences the are the biggest between KDE and GNOME are personal preference.  They can be customized differently, look differently, and have a few select programs that are different between them.  There's no downside to using either one.

---

### Post by Mr. Doom on 2007-01-13
Neo and all
Thank you
But other than the viewable and menu differences why would I pick one over the other????

---

### Post by NeoLithium on 2007-01-14
The only way to explain it, is beacuse you'd like the feel of one over the other. I started off using GNOME; played around with KDE for around 6 months, then came back to gnome because I simply wanted to; there was no other reason.

---

### Post by Mr. Doom on 2007-01-14
Neo
No differences as far as home or office?

---

### Post by NeoLithium on 2007-01-14
No; both gnome and KDE have office programs that can be installed; something like openoffice for example, is available to use on both of them.

---

### Post by Mr. Doom on 2007-01-14
Downloaded the Kubunto iso...will investigate. Still can't understand why no one can get me a straight answer about the differences...purhaps I'll find out on my own!
Thanks to all!

---

### Post by aysiu on 2007-01-14
> **Mr. Doom said:**
> Downloaded the Kubunto iso...will investigate. Still can't understand why no one can get me a straight answer about the differences...purhaps I'll find out on my own!
Thanks to all!
I gave you a straight answer. Read the link I posted!

---

### Post by SqdnGuns on 2007-01-14
> **Mr. Doom said:**
> Downloaded the Kubunto iso...will investigate. Still can't understand why no one can get me a straight answer about the differences...purhaps I'll find out on my own!
Thanks to all!

](*,) ](*,) ](*,) ](*,) ](*,) ](*,) 

You won't know till you try them both.

IT IS A MATTER OF PREFERENCE, THAT's IT!!

---

### Post by The Pinny Parlour on 2007-01-14
Everything in it, starts with K.

Seriously though, KDE desktop environment is used in kubuntu.  I have tried both and this is my assessment.
kubuntu has some nice slick and flashy icons etc.  The thing that made me stick with ubuntu, is that everything is renamed and starts with the letter K.    As far as I know, both offer the same functionality.  I recommend you firstly find some screenshots of both to at least give you an idea of what they both look like.

---

### Post by Mr. Doom on 2007-01-14
I have aquired the Kubuntu iso and wil play! Thanks for putting up with my thick skull!
Doom

---

### Post by Mr. Doom on 2007-01-14
I get it now!! It's the K and G thing! Thanks again for your help and patience!
Doom

---

### Post by wererabbit on 2007-01-15
This directly answers your question.  [http://www.psychocats.net/essays/kdevsgnome](http://www.psychocats.net/essays/kdevsgnome)
It is very verbose and covers a lot of ground.  Read it! :)
-w-

---

### Post by Mr. Doom on 2007-01-15
Thanks for your your response! It has been pointed out to me by several folks that I haven't been paying attention...and rightly so. ( you know who you are) I was directed to a page close to the one you directed me to so I have read said item. I am using Ubuntu and installed Kubuntu as a 2nd system but I don't see it in grub....but give me a couple days and maybe I'll figure it out before I wuss out!
Thanks, Doom](*,)

---

### Post by Mr. Doom on 2007-01-15
Oh! Verbose...good word!

---

### Post by aysiu on 2007-01-15
Even when you have Kubuntu installed, it shows up as "Ubuntu" in the Grub menu, since Kubuntu isn't really a separate distro from Ubuntu--it's just a different set of default packages. Ubuntu should be listed twice, though.

---

### Post by Mr. Doom on 2007-01-15
Well...you didn't give me a chance to get un-stupid on my own but as long as you're there where do I go to make grub wait longer and what choice do I make for KDE? (as you ofcourse know) there's about 15 or 20 choices on the menu.](*,)

---

### Post by aysiu on 2007-01-16
```
sudo nano -B /boot/grub/menu.lst
``` Look for the part that says ```
timeout 10
``` and change it to ```
timeout 15
``` or ```
timeout 20
``` The number after *timeout* is the time (in seconds) before you have to make a choice.

I don't know what choice you make for KDE. You would know, since you installed it to its own partition. Look at the numbers. (hd0,0), for example, is /dev/hda1 and (hd1,2) is /dev/hdb3.

---

### Post by eppoh on 2007-01-17
I have used both on the same machine. My un-scientific sense is that K is a little faster than U

---

### Post by Mr. Doom on 2007-01-17
aysiu-I got grub slowed down. Was at 3 sec which was apparently too fast for my brain. In the grub menu there was no reference to a drive for the line that started Kubuntu. Didn't notice if there was in the file.
eppoh-Have K running. Haven't played with it much yet but it already crashed on me. U is doing fine.
Thanks for the help folks!
Doom

---

