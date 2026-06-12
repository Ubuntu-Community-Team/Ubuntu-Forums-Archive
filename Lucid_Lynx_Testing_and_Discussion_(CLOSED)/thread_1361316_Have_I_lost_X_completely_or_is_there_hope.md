---
title: "Have I lost X completely or is there hope ?"
date: 2009-12-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jerrynewt on 2009-12-21
After about a two week absence I tried to log on to my laptop last night but all I could get was cli on tty3 asking me for login and password. Tried updating and upgrading, then "sudo startx" and got "exec: 3: /usr/bin/X: not found". Tried booting into recovery mode and running "fix broken packages" which worked fine, but still the same result after trying to start x again. Any ideas what to do next ?? Thanks

---

### Post by ranch hand on 2009-12-22
I would boot to recovery every day and use the "root with networking" option and update and upgrade and give it a try.  It will probably come around in a day or two.

Watch it before you do any dist-upgrades.  One today wanted to remove, along with other "unimportant" things, linux-image-2.6.32-9.

To get soe things it is best to just run the dist-upgrade to get the list of held back stuff and abort.  Then you can install the ones you want one or two or three at a time.

---

### Post by ronacc on 2009-12-22
fix-broken or just upgrading may not help , something may have removed X causing the  "exec: 3: /usr/bin/X: not found" . see this thread and try what is suggested in post #5 .[http://ubuntuforums.org/showthread.php?t=1351375](http://ubuntuforums.org/showthread.php?t=1351375) . that thread applies to nvidia but another driver may have done the same thing .

---

### Post by VMC on 2009-12-22
> **jerrynewt said:**
> After about a two week absence I tried to log on to my laptop ...
Jerry,

I'm not sure how you run your computer, but for me, I find myself re-booting almost after every update.

 I don't want any surprises to show up with my morning coffee...

Follow Ranch's advice and see if it clears up.

---

### Post by ranch hand on 2009-12-22
And you can fire up the LiveCD and just go have a look too.

This is testing, all who enter here abandon all hope.

---

### Post by Gina on 2009-12-22
My best monitor's packed up but I don't think that's anything to do with testing.:lolflag:

Good job I've got a "fall back" though 1280x1024 and 17" is horrible after 1680x1050 on a 22" job.

---

### Post by phillw on 2009-12-22
> **VMC said:**
> Jerry,

I'm not sure how you run your computer, but for me, I find myself re-booting almost after every update.

 I don't want any surprises to show up with my morning coffee...

Follow Ranch's advice and see if it clears up.

Drat .... I always forget to reboot ..... Been on 10.04 for 2 days solid now, Guess I should re-boot ... brb (I hope) :lolflag:
/edit -- back :-)
Phill.

---

### Post by ranch hand on 2009-12-22
I am going to different OS' all the time so I reboot regularly.  What is the point of not rebooting in testing?  How do you know if things are working well or not?

---

### Post by trulan on 2009-12-22
> **ronacc said:**
> fix-broken or just upgrading may not help , something may have removed X causing the  "exec: 3: /usr/bin/X: not found" . see this thread and try what is suggested in post #5 .[http://ubuntuforums.org/showthread.php?t=1351375](http://ubuntuforums.org/showthread.php?t=1351375) . that thread applies to nvidia but another driver may have done the same thing .
I'll second this recommendation - I ignorantly 'installed' the nvidia drivers through jockey (hardware drivers) and it removed X with no warning messages or indications of any kind. And I was left wondering why all I had was a command line...

> **VMC said:**
> I find myself re-booting almost after every update.  I don't want any surprises to show up with my morning coffee...
That's where all the fun is, the "let's see if this works" reboot...there's something delightfully morbid about it...

---

### Post by jerrynewt on 2009-12-24
Tried all of the suggestions, but cant seem to remove nvidia-glx-173, error2 everytime I update and upgrade. After removing nvidia* and xserver-xorg-core, I tried update and upgrade and looked good but still error message about not removing nvidia-glx-173. Tried sudo startx and still missing the usr/bin/X.

---

### Post by ranch hand on 2009-12-24
I would just keep updating and be patient.  It should catch up with you sometime.

I had one last cycle thatdin't work for about 10 days.  Then it worked just fine.

As large a drive as you have could hold a lot more than 2 OS'.  Why don't you install the Lizard again and use the generic drivers.  When your other lizard come out of its' stupor, get them to match pretty well and then you can try updates and changes on one to wee if it works and leave the other one alone until you know the changes are safe.

I am nuts and have 5 variations on board right now.  Amazingly, it may be different in the morning, all were working when I came back to stable OS land this evening.

---

