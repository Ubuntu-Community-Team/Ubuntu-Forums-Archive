---
title: "CD boot &amp; install works fine till a certain point. then blackness"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by azitizz on 2011-07-05
I just installed ubuntu 11.04 on a machine that was pieced together from a technician over the years. It was carrying win xp fine but had some booting problems in the end. 

I am able to boot up the computer using the live cd up to the poin to which I clik on "try only" then it loads a bit and the screen goes blank and gets no signal but the hard drive still seems to be working.

Same thing with installing. I fully installed it onto the computer but when it restarted on its own the screen stopped getting a signal...
any ideas?
Thanks

---

### Post by Toz on 2011-07-05
Have a look at this link for instructions on enabling the nomodeset kernel parameter: [http://thedaneshproject.com/posts/ubuntu-11-04-blank-screen-on-boot-solved/]("http://thedaneshproject.com/posts/ubuntu-11-04-blank-screen-on-boot-solved/")

---

### Post by azitizz on 2011-07-05
> **Toz said:**
> Have a look at this link for instructions on enabling the nomodeset kernel parameter: [http://thedaneshproject.com/posts/ubuntu-11-04-blank-screen-on-boot-solved/]("http://thedaneshproject.com/posts/ubuntu-11-04-blank-screen-on-boot-solved/")

Thanks for that. I tried it just now. On boot up I held down the shift key and the booting text said booting grub, (different from what it usually said) and then the screen when blank.

---

### Post by dFlyer on 2011-07-05
Why would you try to install an OS that would not allow you to boot to a live desktop and expect it to work. Did you check the md5sum before burning the cd? Did you check the cd by pressing the space bar when the little stick man appeared to make sure your burn was good?

---

### Post by azitizz on 2011-07-05
> **dFlyer said:**
> Why would you try to install an OS that would not allow you to boot to a live desktop and expect it to work. Did you check the md5sum before burning the cd? Did you check the cd by pressing the space bar when the little stick man appeared to make sure your burn was good?

Impatience, and not thinking is the answer to the first question. No to the second. I didnt realize the stick man space bar check was an option. Ive put aside the machine for now and found another among this pile that was able to work on the Live CD. Its going through the installation as we speak. I hope it works.

It just froze. I rebooted and am doing the disc check. thanks. I guess that should become habit from now on.

---

### Post by dFlyer on 2011-07-05
I didn't mean to be blunt but they are important questions. Always check the iso checksum and the cd after it's burned. Most of the time it's a bad burn or download.

---

### Post by azitizz on 2011-07-05
So the check came out clean. Install is in progress.... Its an "oldish" IBM ThinkCentre. with an 80gb harddrive. So far so good. Thanks for the pointers.

---

### Post by Toz on 2011-07-05
Don't give up on the first computer yet. I think you just need to set the nomodeset parameter to get the screen displayed. Its a common problem. What video card is in the computer?

If booting from the Live CD, press F6 before selecting "Try only" and select the **nomodeset** option.

If booting from the hard drive, try the previous linked instructions to edit the grub screen and add in the nomodeset kernel parameter.

---

