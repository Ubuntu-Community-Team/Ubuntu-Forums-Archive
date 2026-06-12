---
title: "try to install Ubuntu 12.04"
date: 2013-10-02
forum: Installation &amp; Upgrades
---

### Post by nAHE8Yx on 2013-10-02
I have a pc with the following properties: 2.0Ghz processor, 6Gb DDR2, 1GB Video, 500GB Hard. The problem is that at the beginning of the programming collapses the installation, it freezes and then restarts. and I tested several types of ubuntu and always with the same result. appreciate any help.

---

### Post by nerdtron on 2013-10-02
More details like the model of your CPU, motherboard and especially the model of your video card?

---

### Post by nAHE8Yx on 2013-10-02
Dell xps 710, intel core 2, video card Gygabyte. and the mother board im no sure

---

### Post by subhendu2 on 2013-10-02
Are you sure you have 6 GB DDR2 RAM in intel core2. As far as i remember there is 2 slots of RAM and you have 3GB in each slot???  Please check and confirm. Are the RAM came with the laptop , or you added your own?

---

### Post by DuckHook on 2013-10-03
> **subhendu2 said:**
> Are you sure you have 6 GB DDR2 RAM in intel core2. As far as i remember there is 2 slots of RAM and you have 3GB in each slot???  Please check and confirm. Are the RAM came with the laptop , or you added your own?This is possible and I've done it on older machines. There are four slots on the MOBO. So long as you make sure RAM is same specs, you can populate one pair of slots with 1GB modules and the second slot pairing with 2GB modules, thus 6GB. You must make sure to match each different RAM pairing to their matching slots, but provided this is done and RAM is same speed and timing, the system runs well and OS works reliably.

---

### Post by su:bhatta on 2013-10-03
Since you have not elaborated much as to when the system goes for reboot during the installation process this remains a guess, but might work.

Try the 'nomodeset' trick ?
Please see if following the instructions on this page helps: [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076)

---

### Post by nAHE8Yx on 2013-10-03
the memories are in the following order 1-3 and 2-4. I put them on. not a laptop is a tower. thank you all for your opinions and help, and forgive my ignorance

---

### Post by nAHE8Yx on 2013-10-03
the installation collapsed during the first image shown in the instructions you gave me

---

### Post by theDaveTheRave on 2013-10-03
can you confirm that the MD5Sum for the newly burnt live CD is correct.

If the MD5 isn't good that is likely your problem (although I'd be surprised if that was the problem), when you get to the 'first black screen' I'm guessing it is all blank.

Does it simply go back for a reboot imediately ?

Do you have time to hit enter ? if you do try it to see if you get the language selection list.

does it have to be Ubuntu on your system (you try other Debian derivatives, or go to debian itself, they may work)

Is your graphics card on the MBoard or external?
If it is an external card, do you have an video output on the mother-board, if so you could try plugging into this to do the install, then work on getting the extra card going later on.

How 'adventurous' are you (or how tech savy), you could give the 'alternate' installer a try (if I remember this will install via the command line not a graphic environment - so you won't have the 'try ubuntu' option, you'll be straigh into the setup.

David

---

### Post by su:bhatta on 2013-10-03
Now, 1) Do you get a chance to Hit Enter In that First page & get into the Language screen? Then you can try the 'nomodeset' trick!
2)you can go with DavetheRave's good idea, see if a text-based installation succeeds!

Have you given 13.04 (or 13.10 Beta2, depending on how adventurous you are) a try , it comes with newer kernel, maybe that will suit your hardware.

Also, I recommend giving Debian a go and see how you wind up!

---

### Post by Bucky Ball on 2013-10-03
*Thread moved to **Installation & Upgrades**.*

---

### Post by nAHE8Yx on 2013-10-04
I change the way of starting the installation dvd to usb and now if I have results. previously could not even press enter. thank you very much for all your help.

---

### Post by su:bhatta on 2013-10-04
Glad you got it working & welcome to the world of 'Linux for Human Beings'.

Please mark the thread as 'Solved' by Using the 'Thread Tools' at top right of the page.

---

### Post by theDaveTheRave on 2013-10-08
nAHE8Yx

As a matter of help to any others that may face a similar problem, I would recomend running an
```

lshw

```

and posting the output into a reply.

It may be that your hardware is particularly tetchy, and the extra info may help someone else who has the same / similar problem during install.

as your problem particularly seems to be a graphics problem you may simply copy the graphics details of your system.

David

---

