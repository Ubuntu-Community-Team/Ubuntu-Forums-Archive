---
title: "Help I'm beginning to drown!"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by hunts12 on 2007-03-17
Can anyone please help me I am a total noob with Ubuntu. I tried to do a dual boot install. With Winxp and Edgy elft. 
I got the cd from ubuntu.com. When I tried to boot  from the cd it gives me some option  i.e. Start or install ubuntu/ check cd/ memory test and so on and so forth. 
What I do is press enter on start or install ubuntu. It then show me that it is loading kernel, but then this black screen with this message pops up: (  BusyBox v1.1.3 (Debian 1.1.1.3-2ubuntu 3) Built in shell (ash) Enter 'help' for a list of built in commands.
/bin/sh: can't access tty; job control off (initramfs).)
 And from here on out I have no clue whatsoever what to do. I have tried it several time and get the same result. I tred installing Suse 10.2 and it install properly. I would love to have Ubuntu install though.
Here is a list of my hardware: Core 2 duo e6600.inte mobo 965, 2gb of e5 hynix ddr2, 8800gts nvidia 320gb seagate. 500watts psu. winxp pro install. 
Anyhelp installing the  wonderfull ubuntu would be greatly appreciated. Thanks!:popcorn:

---

### Post by hunts12 on 2007-03-17
Can anyone please help me I am a total noob with Ubuntu. I tried to do a dual boot install. With Winxp and Edgy elft.
I got the cd from ubuntu.com. When I tried to boot from the cd it gives me some option i.e. Start or install ubuntu/ check cd/ memory test and so on and so forth.
What I do is press enter on start or install ubuntu. It then show me that it is loading kernel, but then this black screen with this message pops up: ( BusyBox v1.1.3 (Debian 1.1.1.3-2ubuntu 3) Built in shell (ash) Enter 'help' for a list of built in commands.
/bin/sh: can't access tty; job control off (initramfs).)
And from here on out I have no clue whatsoever what to do. I have tried it several time and get the same result. I tred installing Suse 10.2 and it install properly. I would love to have Ubuntu install though.
Here is a list of my hardware: Core 2 duo e6600.inte mobo 965, 2gb of e5 hynix ddr2, 8800gts nvidia 320gb seagate. 500watts psu. winxp pro install.
Anyhelp installing the wonderfull ubuntu would be greatly appreciated. Thanks!
Edit/Delete Message:popcorn:

---

### Post by Arby on 2007-03-17
Hi,

[This  thread]("http://www.ubuntuforums.org/showthread.php?t=384031&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty") describes the same problem and they seem to have fixed it so you might want to check that out. It seems to be caused by a problem in grub, the ubuntu bootloader. I have to go out for a while but I'll check back later and see how you're doing.

Finding a liveCD and figuring out how to mount your ubuntu partition from the liveCD is probably going to be helpful in this process. If you can do that and post the contents of /boot/grub/menu.lst here if you get stuck along with the output of fdisk -l for your ubuntu partition. Hopefully we'll be able to help you.

Back later
Arby

---

### Post by colo on 2007-03-17
The SATA- and IDE-Controllers of your motherboard are too new to be supported by Edgy . go for the Feisty Testing Images, they should boot and install just fine.

---

### Post by Prof.Arronax on 2007-03-17
> **colo said:**
> The SATA- and IDE-Controllers of your motherboard are too new to be supported by Edgy . go for the Feisty Testing Images, they should boot and install just fine.
Why not post the URL?  (Would really be helpful and save a LOT of time for us "noobs".)

---

### Post by Kateikyoushi on 2007-03-17
It's the headline on the main page of the forum.
Anyway here is the [LINK]("http://cdimage.ubuntu.com/releases/feisty/herd-5/")

---

### Post by hunts12 on 2007-03-17
You are all heaven sent :lolflag:  I have finally install it by using Feisty herd 4 in safe graphic mode.
 Now that I have it install the fun begins:guitar:  The 1st snag that I hit is graphics whenever I scroll it looks like I'm in the middle of the ocean with the wave all around me and it suck:mad:  any fix for that I have 8800gts320mb for my graphics card.
What should I do:confused:  Should try to install the driver that came with it. That's what I did for winxp. Again THANKS for all the help:popcorn: :guitar:

---

### Post by Kateikyoushi on 2007-03-17
The windows driver won't work.
The easiest way would be to install it via envy. [LINK]("http://albertomilone.com/driver.html") or check the Multimedia video part of the forum.

---

### Post by bapoumba on 2007-03-17
@ hunts12: merged your duplicate thread in here.

---

### Post by hunts12 on 2007-03-17
Again thanks the wavy thingy is gone hehehe. Now to better things. I have been doing a lot of reading about installing beryl or other apps but I can't seem to do it.
I can't even get VLC player. What should I do:confused:  Also  how exactly do I merge my thread Bapoumba:confused:   Thaqnks a bunch guys:guitar:

---

### Post by bapoumba on 2007-03-17
> **hunts12 said:**
>   Also  how exactly do I merge my thread Bapoumba
Hello,
I merged them (this is staff only), I just posted here to let you know ;)

---

### Post by Prof.Arronax on 2007-03-17
> **Kateikyoushi said:**
> It's the headline on the main page of the forum.
Anyway here is the [LINK]("http://cdimage.ubuntu.com/releases/feisty/herd-5/")
Thanks.  I did locate the download site on my own, but the headline for the forum page is, in fact, *new*.  (Besides, my link to the forums is usually by link from e-mail updates, so I hardly ever see the headline page.

At any rate, the download went smoothly and most importantly, I was able to install either version successfully on my DG965RY system.  The "feisty" build has some interesting features like capturing my account info from the WinXP partition without affecting the Windows install in any way.  Excellent. 

Now I'll have an entire new set of questions.  I should probably post those to a different thread...

But thanks again!

---

### Post by Kateikyoushi on 2007-03-17
I did not hear about these email updates yet, that's new for me, knew the rss though.

---

### Post by bapoumba on 2007-03-18
> **Kateikyoushi said:**
> I did not hear about these email updates yet, that's new for me, knew the rss though.

Hello Kateikyoushi,

User CP > Edit Options > Default Thread Subscription Mode. If you choose Instant notification, you will receive an email to the address you have specified for each thread you have posted in.
In addition, > Thread Tools (on a thread page in the forums) > you can subscribe to a thread you have not posted in.

Cheers :)

---

