---
title: "Problems installing Ubuntu under Samsung R60 Notebook"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by aw5k on 2007-09-22
I downloaded the new Ubuntu 7.04 Live CD and tried to install.
Following problems:

When I choose to start and install ubuntu, it loads but I end up with a terminal, not in graphics mode. What do I need to do?
I tried to "startx" but it said s.th. like "screen found but no usable configuration".

Can anybody please help?

---

### Post by Pumalite on 2007-09-22
Try Alternate CD. Post your specs.

---

### Post by aw5k on 2007-09-22
Hi.
I'd rather stick with the Live-CD. I've got Vista installed and don't want anything messed up. There's a site that tells me exactly what to do in order to get it done, that's why.

Anyway, I get a screen like this:

[   57.347068] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
Loading, please wait...
Last login: ..
etc
..
..
ubuntu@ubuntu:~$: 


Any idea? I have got the Samsung R60. It's an ATI graphic chip.

---

### Post by Pumalite on 2007-09-22
If you have an ATI and you want to continue installing with the Live CD you are hitting your head against a brick wall.

---

### Post by aw5k on 2007-09-22
Really?
But isn't installing from Alternate too risky? I don't want to mess up my Vista.
Is there an option to install on the unpartitioned space?

---

### Post by Pumalite on 2007-09-22
What do you mean by 'unpartitioned space'?

---

### Post by aw5k on 2007-09-22
Well, I've got ~30GB that is not used by Vista. I want to install Ubunto in that space.

---

### Post by Pumalite on 2007-09-22
Make a partition out of it with Vista's partitioner and Install Ubuntu to it.

---

### Post by maluka on 2007-09-25
well, this issue was never resolved. i just purchased a SAMSUNG R60 with ATI readeon express 1250 graphics card for my daughter. i have installed using the alternate cd. i have looked at all the possible solutions to the problem but have been unable to find a workaround to succesfully boot into X. any help would be appreciated. :confused:

---

### Post by Pumalite on 2007-09-25
The one I saw in Google had this:Graphics Card: Intel 950

---

### Post by maluka on 2007-09-25
this is an R60 plus core2duo ati radeon express 1250 2 gig ram. ([http://www.mediamarkt.de/top5/ansicht/index.php?pid=293](http://www.mediamarkt.de/top5/ansicht/index.php?pid=293))

---

### Post by maluka on 2007-09-25
[IMG]http://i20.tinypic.com/hwznt4.jpg[/IMG]

[IMG]http://i20.tinypic.com/jb5uo5.jpg[/IMG]

[IMG]http://i20.tinypic.com/a5kk78.jpg[/IMG]

this is where i am now

[IMG]http://i24.tinypic.com/qoit84.jpg[/IMG]

---

### Post by maluka on 2007-09-25
there seems to be a driver for this card here: [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

how would i go about installing it?

---

### Post by Pumalite on 2007-09-25
Don't install the driver yet. At the login, login with your username and password, then:
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx
Once IN the system we can talk about installing drivers.

---

### Post by maluka on 2007-09-25
i've tried that several times and still get the no screens found fatal error

---

### Post by maluka on 2007-09-25
i'm doing a fresh install in order to start from scratch again.

---

### Post by Pumalite on 2007-09-25
Your ATI Card must be the killer.

---

### Post by maluka on 2007-09-25
i know :-D there must be a way to get it working though. i have reinstalled and found the same problem. i will retry in an hour (after my download ends) using the 64bit version of the alternate cd. if that doesn't work, it's back to the store with this machine!

---

### Post by maluka on 2007-09-29
SOLVED!

:popcorn::):KS

go here: [http://ubuntuforums.org/showthread.php?t=559250&highlight=maluka](http://ubuntuforums.org/showthread.php?t=559250&highlight=maluka)

---

### Post by Pumalite on 2007-09-29
Glad you got it to work. Please use 'Thread Tools' and mark it SOLVED to help other readers. Thank you.

---

### Post by maluka on 2007-09-29
unfortunately i didn't start the thread so i can't mark it as solved ...

---

### Post by Pumalite on 2007-09-29
Forgot that...Thanks anyway.

---

### Post by maluka on 2007-09-30
no problem :)

---

