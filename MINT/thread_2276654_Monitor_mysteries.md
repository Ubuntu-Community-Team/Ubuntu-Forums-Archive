---
title: "Monitor mysteries"
date: 2015-05-04
forum: MINT
---

### Post by veddox on 2015-05-04
Hello everyone,

sorry for the slightly non-descriptive thread title, but I couldn't think of a better one. Here's the situation:

Recently I was visiting friends whose old Packard Bell XP laptop was dying. To give it a new lease of life, they asked me to put Linux on it - so I went for my standard option for these cases, Linux Mint 13 with Mate. Installation was no problem, it seemed to work fine too, until we tried to play a film. Both with VLC and the inbuilt video player, we could hear the sound track, but saw nothing on the screen - the video window stayed black. We did a lot of experimenting with different DVD drives, video file formats, etc., but nothing seemed to work.

Then we attached an external monitor. The desktop showed up fine on it, even though in the system settings Mate did not recognize that any other device had been attached. By chance we tried playing another film - and it worked! On the external monitor, that is; the main one stayed as black as ever. The problem was: the mouse cursor could only be seen on the laptop monitor, it simply didn't show up on the external one. So we could watch videos on the external monitor, but had to navigate around on the inbuilt one.

What the heck???

I have never seen anything like it, does anybody have any idea what the cause might be? (My to hypotheses are that the installation DVD was corrupted, or that there were some hardware defects in the computer.)

---

### Post by Bucky Ball on 2015-05-04
*Thread moved to **Mint**.*

Have you installed arandr and tweaked with that? It is a front-end for arandr and you might be able to get to the bottom of it by checking how the machine thinks your monitors should be set up.

---

### Post by kc1di on 2015-05-04
First of all you would most likely have a better chance at an answer if you posted your question on the Mint Forums found [here.]("http://forums.linuxmint.com/index.php?sid=c5356285be993c715c36529cfe7dcca4")

I don't have mint installed at the moment. But if I remember right in Mate you can go to the video setup and tell it to mirror monitors so the mouse should appear on the external as well as the internal screen. 

I would also suspect the video driver for the laptop is the wrong one.  you may want to tells us what video card is in that machine.

---

### Post by Vladlenin5000 on 2015-05-04
+1 to everything above.

I would just add that you also need codecs for most of the videos being currently used/shared. How to install them? Again, Mint forums...

---

### Post by Bucky Ball on 2015-05-04
This thread has now been moved to the Mint section. Thanks for pointing that out. My mistake, I only registered the Mate part and not the Mint. ;)

---

### Post by veddox on 2015-05-05
Sorry, my apologies for a badly-started thread. Yes, it should have been posted elsewhere. And I am afraid I forgot to add something: I am currently about 1000km away from the computer in question, so I won't actually be able to fix it. I was just wondering what the cause of this phenomenon might be.

@Vladlenin5000:
I thought about codecs too - but Mint comes with all necessary codecs preinstalled. I have used that ISO image I used here many times without any problems of the kind (elsewhere, videos played perfectly). That's what made me think it had to be something else.

---

### Post by rewyllys on 2015-05-07
I believe that Linux Mint 13 is no longer supported and its repositories have been frozen.  

It would probably be a good idea for you to install LM 17.1, and see what problems then remain, if any.

---

### Post by veddox on 2015-05-08
@rewyllys:

Linux Mint 13 is actually still supported until April 2017, like Ubuntu 12.04. But upgrading sounds like a good idea anyway...

---

