---
title: "ubuntu 10.04 won't reboot"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by Cedar Waxwing on 2010-07-12
Greetings.

I just completed the lengthy installation for ubuntu 10.04 qnd now the computer won't boot up. It tries, but fails at the "Pre-Configuration" failure message. It appears to try to start ubuntu, but then goes dark.

How can I do a re-install? I downloaded ubuntu from the website to a disc. I've tried to boot from the disc, but the same thing happens.

I'm on a Toshiba Sattelite M20 laptop. Yesterday I was able to run in "low graphics" mode, but cannot even reach that today.....

The computer was fine running the previous version of ubuntu yesterday......

Many thanks!

Cedar

---

### Post by Rubi1200 on 2010-07-12
What type of graphics card do you have?

---

### Post by Cedar Waxwing on 2010-07-12
Hi,

I'm not sure. I was given the Toshiba Satellite M20 because the Organization was getting rid of them and upgrading.

It came with ubunto (the next lower that 10.04) and was running well yesterday.

The only issue I had was changing the Administrator properties, but that was solved and ubuntu ran just fine.

I then performed the Upgrade Download/installation and was then only able to run with the Low Graphics menu choice.

Now, I cannot even boot up. So, right now, I cannot say what the graphics card is.....

Is there any way to do a disc-format/re-install ubuntu? Right now it won't even boot from the cd.

---

### Post by QIII on 2010-07-12
Won't boot from CD may indicate other hardware problems -- or that the graphics will not work.  Hard to say.


Sticking with the graphics theme, from what I find on line, the integrated graphics for the machine:

Intel Extreme Graphics 2 Shared video memory (UMA)

We'll probably have to do some research to see if there is a compatibility problem with the latest X Server.

---

### Post by Cedar Waxwing on 2010-07-12
...well I just  was able to get it up to the "root" command line (looks like an old DOS command line)....

...now what?

---

### Post by davidmohammed on 2010-07-12
type


lspci | grep VGA

this will reveal the exact graphics card you have.

---

### Post by Cedar Waxwing on 2010-07-12
Thanks, here's the readout:

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)




...one other thing is that when the boo fails, it give the "Pre-configuration failure" message.

---

### Post by davidmohammed on 2010-07-12
thanks -

did you get to root via the grub - recovery menu option?

if so type

sudo nano /etc/default/grub

change the line 
GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_LINUX="i915.modeset=1"

save

then type

sudo update-grub

reboot

---

### Post by Cedar Waxwing on 2010-07-12
**woo hoo!!!!!**

That worked like a champ!

Thank you SOOOOOO much!

whattaplace!

---

