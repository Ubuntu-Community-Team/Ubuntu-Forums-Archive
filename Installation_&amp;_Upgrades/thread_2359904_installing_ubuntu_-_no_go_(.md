---
title: "installing ubuntu - no go :("
date: 2017-04-29
forum: Installation &amp; Upgrades
---

### Post by eelie on 2017-04-29
Hello,
 
I&#8217;m try to installUbuntu 16.04, 16.10 and 17.04 on my brand new computer and seem to be hittingroad blocks with all of them.
 
It&#8217;s a HP Zbook 17G3 with Xeon processor, NVIDIA Quadro 4000 with 1.0 TB HDD and one 500 MB Solidstate drive.
 
It&#8217;s a dual boot, Windows 10 Pro on solid state drive and I wantUbuntu on the 1.0 TB HDD. Here&#8217;s what I do
 
Download the ISO, use the universal USB install to &#8216;extract&#8217; the isofile to a bootable, formatted USB. Turn the computer on and go through the entireUbuntu installation process  (with the 4partitions, boot, home, / and swap) without any problems&#8230;.except at the veryend where it say &#8220;Restart the computer to finish the install&#8221;. 
 
At this point it stalls, or hangs for long time. When I power off andpower back on, I select Ubuntu through the Grub menu and  it still stalls or hangs. When I go toadvanced option in Ubuntu, and then select load normally (or the first option)then it works. 
 
It does this for all three versions of Ubuntu.
 
Why cant it just load normally into Ubuntu through grub?
 
thanks

---

### Post by kc1di on 2017-04-29
The problem may be your Nvidia graphics driver. 
Try putting nomodset in the grub boot line right after quite splash.  
If if boot up to a DE go to additional drivers and install the correct nvidia driver for your card.
this [post ]("https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu")though dated should still work.

---

### Post by eelie on 2017-04-30
thanks, that worked!

It now boots normally. The only issue is now is that system is so slow and choppy, the computer is barely usable. I even change the video driver to the NVIDIA from oxrg but the slow and choppiness still exists.

This related to the monodeset?

thanks again

---

### Post by Bucky Ball on 2017-04-30
Welcome. Where did you install the NVidia driver from? For the moment, suggest you go back to the Nouveau open-source driver (switch off the NVidia driver) and see if that speeds things up. If so, you've answered your question: the NVidia driver is slowing you down.

You are running the Live session from 'Try Ubuntu'? That will be slower than an install and also will not retain anything you do to it on reboot. Drivers you install, changes you make, etc. will be gone. Trying to get this stuff going on a live session is sometimes a waste of time.

---

### Post by eelie on 2017-04-30
thanks all. I think the problem is solved. What I did was remove the nomodeset command from the grub file and now everything works. I've reset the computer 3 three times (after updating) and it logs in no problem with no stalls or hang-ups.

I used the update software for the NVIDIA driver (switched the bullet point from 'xorg' to 'NVIDIA', think its 375.39?), and btw, I'm running Ubuntu 17.04. Seems to be working fine.

thanks all for your help so far!

---

### Post by kc1di on 2017-04-30
Glad you didn't give up - Enjoy ;)

---

### Post by Bucky Ball on 2017-04-30
Good news. You can mark the thread as solved to help others using Thread Tools at top right of page (or see link in my signature).

Enjoy! ;)

---

