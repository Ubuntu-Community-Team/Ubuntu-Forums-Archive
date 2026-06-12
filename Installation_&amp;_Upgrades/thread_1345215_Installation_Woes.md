---
title: "Installation Woes"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by 337 on 2009-12-03
Well, I'm another "new to GNU/Linux" with an installation problem.

I'm disappointed that I need help so soon.

Booting from the CD of Ubuntu 9.10 I got from "The Linux Store" gets me through the language selection page to the Ubuntu Menu.  I select the first choice - which is "Try Ubuntu without any changes to your computer".

The screen then goes to a pulsating Ubuntu logo for about 90 seconds, then blank.

Next is displayed a page of text from which I believe I could learn a lot... if it was there for more than the 5 seconds it remains before going blank again.

After about 20 seconds the screen begins flashing text.  The same line is repeated, with the beginning of the line appearing to be some sort of incremental counter and the end of the line being "[drm:intelfb_restore] *ERROR* failed to restore crtc configuration: -22"

At this point I execute a few cntl-alt-del to force a re-boot.

I am truly looking forward to getting Linux running and would really appreciate asome help.

Thanks,
Lee

---

### Post by gdonwallace on 2009-12-03
I had a similar problem as well.  It would get past a few lines on the screen, and freeze up.  What I had to do, was after the language selection, press F4, this will change the settings for how the video will display.  As I recall it was the first option that comes up on the list.  choose that, and the menu will go away.  then choose the option to run Ubuntu without installing and it should work.

---

### Post by 337 on 2009-12-03
F4/Safe Graphics Mode did it.  Thanks!

Say, if you have the time, do I want a "Linux-Swap" partition for the Linux installation or another "type" of partition.

Thanks again, it's looking good.

Lee

---

### Post by oldfred on 2009-12-04
Linux needs swap but not as much as it used too since most computers have lots of memory. When we only had 256KB or 512KB, swap needed to be twice memory. With typical 2GB of memory you just need 2GB of swap and if you have more memory and hibernate you need swap as least as large as you memory.

---

### Post by 337 on 2009-12-04
Okay... so, I have about 50 gig I can partition just for Ubuntu.  What "type" should I use for the installation?  Do I actually need a "swap" file?

I've now booted from the CD, I just want to install it on the hard drive PROPERLY and I'm being deliberately slow to insure that I do it right the first time.

Thanks,
Lee

---

### Post by 337 on 2009-12-04
oldfred, I just re-read your post and, perhaps, you could help me understand something that has eluded me.

What does "hibernate" do??

---

### Post by oldfred on 2009-12-04
Hibernate is more for portables or if your want to save the working state without shutting down. It copies RAM to the harddrive so to start up all you do is copy the hard drive data back to RAM memory. It is quicker than rebooting. I never shutdown my desktop, I have sleep modes on HD and display so the convenience only costs a little and some think turning electronic devices on & off reduces life. Windows requires rebooting to reset things peroidically and on just about any software update, Ubuntu only requires a reboot for a new kernel.

---

