---
title: "Jaunty Beta is unusable for me"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Alpha UMa on 2009-03-27
I'm still using Ubuntu 8.04, as it has less issues on my laptop: with Intrepid my integrated webcam stopped working, plus other regressions and problems, until I gave up.

Today I downloaded both Kubuntu and Ubuntu 9.04 Beta, because I read about better performances compared to previous versions, about how the team did a great job and, from some alpha testers, how it was already good and stable. 

So I started Kbuntu 9.04 beta live CD, with great expectations and curiosity:
[LIST][*]maybe the boot time is somewhat faster, but I cannot see that clearly from the live CD, so I waited to test it better after the installation. Sadly, after the boot, the live CD displayed **so huge fonts, that it was completely unusable**. My laptop has an Intel 945GM and this bug is around for quite some time, it also affects Fedora and Mandriva (maybe OpenSuse too, if I remember correctly, when I tested it). :( I had an hard time even to get the controls to reboot, luckily it reconizes Ctrl+Alt+Canc.
[/list]

So I discarded Kubuntu and I tried Ubuntu, but:
[LIST][*]Ubuntu 9.04 beta **hangs on boot time**. I had to press Ctrl+Alt+F1 and type *startx* to get into Gnome. The problem was with **ACPI**, so I rebooted and I checked ACPI=off. This time the boot was OK, but I never had this problem with the previous versions on boot time.
[*]Gnome set the fonts size correctly, but **graphic performances were just horrible**. 2D redraw was painfully slow, I could see how slow it was just by moving windows around the screen. On 3D side, glxgears showed only 297-298 FPS against 1093-1096 FPS I found in Hardy. I had similar issues with Ubuntu 8.10.
[*]as with 8.10, there was no sign of life from the webcam. Nevertheless I'd like to try with "Cheese", but **Synaptics didn't started**, nor apt worked on the live CD. On Ubuntu 8.04 the stk11xx driver worked fine for my cam, but for an upsidedown image problem, that I was able to fix using a quick workaround: *sudo modprobe -r stk11xx* and then *modprobe stk11xx vflip=1*
[/LIST]

---

### Post by cariboo on 2009-03-27
Please read the release notes located [here]("http://www.ubuntu.com/testing/jaunty/beta"). The faster bootup times have no affect on the LiveCD, you will only see a benefit if you install the Jaunty beta and format your hard drive as ext4.

Also read this [sticky]("http://ubuntuforums.org/showthread.php?t=1107854") to to solve the synaptic problem.

Jim

---

### Post by Alpha UMa on 2009-03-27
Hi Jim, thank you for your answer. I had no clue that Python was related to my apt and Synaptics problem, I will try it. Could it be related to the hanging on boot too?
I really wished to install Jaunty and test how faster it was to boot, but all those issues dissuaded me to put the thing on my HDD.

As for performance regressions concerning Intel chipsets, notes says to try UXA: I already did that when I was using Intrepid and that just worsened my situation. The best solution I found was to put *Option "AccelMethod" "XAA"* inside xorg.conf. That made Intrepid closer to Hardy in graphic performace, but still somewhat slower, notably with QT apps, if I remember correctly (and Hardy itself is already below Windows). I know that people here are doing the best they can, and I'm grafeful, but this is a severe issue IMHO, that is around for many months: if I was a new user who decided to try Intrepid, I would never switched myself  to Ubuntu or GNU/Linux. So I'm somewhat worried about Jaunty and I hope this regression (as the others) will be fixed out-of-the-box someday.

---

