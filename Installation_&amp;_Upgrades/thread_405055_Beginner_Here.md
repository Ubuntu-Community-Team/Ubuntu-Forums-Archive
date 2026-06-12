---
title: "Beginner Here"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by alx4 on 2007-04-09
i've just downloaded ubuntu 6.10 and i wanna install it.


i have windows xp instaled 

when i boot from ubunto cd....i get 
```
BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)
```

why??

WHAT TO DO??

---

### Post by in_flu_ence on 2007-04-09
I guess you might not have done a proper cd burn and some bits are missing. Try burning the CD image again at a lower speed.

That's what i think which goes wrong.

Once burned, try check integrity of the image before installation as well.

---

### Post by alx4 on 2007-04-10
i've burned the ubunto CD  again and verified ....all looks fine, but when i try to install ubunto  6.10 on my WindowsXp system same error message again...

i've tried with same CD on my laptop, and all looks fine

where can be my problem?
what to do??

---

### Post by in_flu_ence on 2007-04-10
So you manage to boot into the livecd and work? it is only when you click on the install icon and the error message pop up?

---

### Post by alx4 on 2007-04-11
i have 2 computers: a desktop and a laptop computer...

when i've tryed Ubunto on laptop i dind't get that error message. this error it's only when i try to install ubunto on my desktop computer.

can be some unsupported hardware? how can i check??

---

### Post by cantormath on 2007-04-11
ubunt**_U_**, not ubunto :) 

Welcome to the club........

First, what is your hardware? I suggest you go into the bios and reset to default settings the bios as well.  Make sure to change to boot order back to the cdrom if it gets changed.

---

### Post by darrenm on 2007-04-11
Where does the message appear? Straight away after booting from the CD?

---

### Post by alx4 on 2007-04-12
> **darrenm said:**
> Where does the message appear? Straight away after booting from the CD?

after 2 minutes from installation ....

---

### Post by alx4 on 2007-04-12
> **cantormath said:**
> ubunt**_U_**, not ubunto :) 

Welcome to the club........

First, what is your hardware? I suggest you go into the bios and reset to default settings the bios as well.  Make sure to change to boot order back to the cdrom if it gets changed.

i've turn to BIOS defaut , but same error message....

i have same problem like in this post
[http://ubuntuforums.org/showthread.php?t=400784](http://ubuntuforums.org/showthread.php?t=400784)

they didn't have an answer yet...do u have??

thx again

---

### Post by adriantry on 2007-04-12
Hi Alx4

> **alx4 said:**
> BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

That message is displayed when you have burned the CD using an incorrect method in Nero.

Here is a guide about the best way to burn your CD
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Adrian

---

### Post by alx4 on 2007-04-12
> **adriantry said:**
> Hi Alx4



That message is displayed when you have burned the CD using an incorrect method in Nero.

Here is a guide about the best way to burn your CD
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Adrian
thx but i've used same cd to install ubuntu on my laptop

---

### Post by adriantry on 2007-04-13
> **alx4 said:**
> thx but i've used same cd to install ubuntu on my laptop

Sorry about that. I was trying to remember a similar problem a couple of years ago, and was thinking of the wrong thing.

Here's a thread that may be related to your problem
[http://ubuntuforums.org/showthread.php?t=282956](http://ubuntuforums.org/showthread.php?t=282956)

Post 21 may have the answer to you.

Adrian

---

### Post by alx4 on 2007-04-14
i didn't passed instalation yet

---

### Post by adriantry on 2007-04-14
> **alx4 said:**
> i didn't passed instalation yet

I know, but I thought it might help. The other person's processor didn't like the default kernel. Is there some way to ask Ubuntu to boot from a different kernel while using the Live CD?

Maybe the alternate install CD would work?

---

