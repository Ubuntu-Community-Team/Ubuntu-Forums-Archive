---
title: "booting from external drive with non-pae CPU"
date: 2014-06-20
forum: Installation &amp; Upgrades
---

### Post by zemega on 2014-06-20
[This post was moved into an own thread from [a thread about booting from a USB 3 HDD]("http://ubuntuforums.org/showthread.php?t=2229968")]

May I add that running Ubuntu from external on a computer that don't support CPU PAE will sort of corrupt Ubuntu(not using non PAE kernel of course), it does not even load properly into Ubuntu. And the effects persists when you run Ubuntu on a normal computer. Of course this may seem irrelevant to the topic (which is latest hardware), but just in case you thought of running it on old computers.

---

### Post by sudodus on 2014-06-20
@zemega

Your case is interesting, but as you wrote, may seem irrelevant to the topic of [that thread about booting from a USB 3 HDD]("http://ubuntuforums.org/showthread.php?t=2229968"). I create a new thread with your post and make a link from there.

We can continue exploring your case in this thread. Please specify your computer to make it easier to give relevant advice to help you

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

And please describe the Ubuntu system in your external drive

- version (14.04 LTS?, 32-bit or 64-bit?, 'installed' or 'live'?)

Finally, please describe what happened, how it was damaged by trying to run in the computer without a PAE capable CPU.

---

### Post by zemega on 2014-06-21
Alright, let me be clear on this matters. First I installed Ubuntu 12.04 32 bit using normal Ubuntu download (which means it requires PAE capable CPU) on a PAE capable CPU. Everything works fine, even on other PAE capable machine. Now when I plug this external into a non PAE capable machine and boot up, it doesn't boot up properly until the normal desktop you normally will see. It shows the desktop without any top panel or Unity launcher. I can still open gnome-terminal using Ctr+Alt+T, did not manage to restart Unity, So I just shut down the machine. Next I boot from the external on a normal capable PAE machine (the original machine I installed Ubuntu on the external). What happens is it did not boot into normal desktop just like the situation at the non PAE capable machine. So I'm stuck at the desktop without Unity launcher and the top panel. Interesting is that I can restart Unity this time. And when I restart the Ubuntu inside the external , the next boot load into the normal desktop just as it suppose to be. I tried again with the non PAE capable machine, and the same thing happen again. I do not know what actually happens, but that is my story. 

Now, I don't have the machine anymore, its HP Compaq Presario something (2004 or 2005 release). All machine within my care are new, and I do not plan to touch older hardware anymore. So I do not wish to pursue this discussions. I'm just informing my experience if anyone is interested.

---

### Post by mörgæs on 2014-06-21
When you write

> **zemega said:**
>  into a non PAE capable machine 

I read *into a ten years old machine with a weak graphics processor not suitable for Ubuntu*. This is likely to be the problem, not the PAE capability.

If there is a PAE problem you either boot or not. When the problem is a more or less complete desktop the cause is something else.

---

