---
title: "Installation Fails on Dell Inspiron 100 Laptop"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by IggySaffron on 2008-04-05
Hi Folks,
I am trying to install Ubuntu 7.10 onto a Dell 1100 laptop (14.1XGA, P4, 2.2GB, 256MB RAM).  My plan would be to dump Windows (not partition).

It cycles through the loading of the LiveCD, but then reaches a point where the CD drive stops, and the screen is black.  There a nanosecond flashes of (crooked) screen graphics, but nothing display.  I tried the Safe VGA mode.  It runs through the ini steps, but stops, also.

Fearing the 256MB being the problem, I switched to Xubuntu 7.10.  (I now always burn the ISO to CD at 2x).  I encounter the same issue.

I read TheKen's October '07 posting for a clue; he had the same laptop, but with a bit more power.  I tried the F4 option and switched from VGA to the only other screen res available (was it 640x480x16?).

And still no luck.

I am a true novice at this, so any help offered will have to be written in step-by-step which a 7-year old could follow.  (That might be my mental age - I'm not sure at this stage).

Thanks for any guidance.

Iggy

---

### Post by Pumalite on 2008-04-05
With your RAM, I'd try Xubuntu Alternate CD: 
[http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)

---

### Post by Pumalite on 2008-04-05
You need 340 MB of RAM to boot a Live CD. Alternate Ubuntu might install, but will be so slow in your system that will kill you. You can boot a Live CD making a 500 /swap partition ahead of time. Xubuntu will install easy and will run very fast in your system.

---

### Post by IggySaffron on 2008-04-06
I used Text mode of the Alternative installation CD for Xubuntu 7.10.  Following TheKen's thread/advice, I selected only the lowest screen res (640x480).

Upon completion, the computer stops at a black screen (afte the Ubuntu loading screen progess bar reaches completion).

I'm not sure what to try next.

Thanks.

---

### Post by Pumalite on 2008-04-06
Have you rebooted?

---

### Post by IggySaffron on 2008-04-06
It's an Inspiron 1100; ignore the subject line.

Yes, I have rebooted several times.  After the Xubuntu progress bar finishes, again as with my previous tires with the Live CD, I see a nanosecond flash of what looks like the Xubuntu graphic.

Sometimes when I push the power button to try a reboot, I can see for a moment that the 'bus something failed", and there might have been a line above that that failed, too.

Thanks for your help.

---

### Post by Pumalite on 2008-04-06
Post:
lshw

---

### Post by IggySaffron on 2008-04-07
I have gotten as far as a command prompt, and the display lshw options (-xml, -html, etc.) but I am not clear what exactly to do to display the lshw list.  Once it is displayed, I am a bit unsure how to post it here.  I am corresponding on another computer.  I can type up the items listed on the Dell invoice, but I suspect that you are looking for detail.

Also, many of the posts mention flashing the BIOS to the newest version.  Mine seems to be A06, which is pretty old.

My question: I overwrote XP when I installed Xubuntu.  Should I reinstall XP (gasp) to do some of these administrative steps?

Thanks, Mark

---

### Post by Pumalite on 2008-04-07
Download a new iso, follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on the iso, burn at 4x or less on CD-R, check CD integrity after burn and before install. If everything is OK., reinstall.

---

