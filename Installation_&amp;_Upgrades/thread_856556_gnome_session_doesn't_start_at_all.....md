---
title: "gnome session doesn't start at all...."
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by knockonankur on 2008-07-11
Somebody plzz help
I'm a newbie..

I happen to install ubuntu 8.04 on my windows xp machine with dual boot
the installation was complete and successful 

Then when I tried to log into ubuntu the gnome session simply didn't start.....
After I entered my password the screen went completely orangish for a while and then again the username promt window displayed and this cycle repeats continuosly.....
the gnome session doesn't start at all
Though I'm able to hear drumbeats in the background after logging

However I'm able to freely log into fail safe mode without any probs...

Help will greatly be appreciated to enrich my first linux experience....

---

### Post by Rallg on 2008-07-11
Try this: Log in to recovery mode, which gives you a text console. When you finally get a command line prompt:

sudo apt-get update && sudo apt-get dist-upgrade

That might find some packages that weren't included with your installation. Then re-boot. It may or may not help, but it won't hurt. It sounds as if your graphics driver is wrong.

---

### Post by bkasindorf on 2008-07-12
> **Rallg said:**
> Try this: Log in to recovery mode, which gives you a text console. When you finally get a command line prompt:

sudo apt-get update && sudo apt-get dist-upgrade

That might find some packages that weren't included with your installation. Then re-boot. It may or may not help, but it won't hurt. It sounds as if your graphics driver is wrong.

Hi,
I have 2 other 8.04.1 systems running fine, and 7.10 was running well on this machine. I upgraded to 8.04 then got this problem. Did a clean install and it still happened. I changed the video driver and it still happened. I ran a failsafe Gnome session and it worked fine. I ran a terminal from there and started nautilus, ran synaptic and updated everything again. The session works fine if I manually start it. I don't know what script is running or where the error log for this is to look at. The video seems fine since it starts OK, does the logon sounds and dies later.  Almost starts, does the bongos and then asks me to login again but doesn't give an error anywhere to look at. I don't know what the Xclient script is or where to start removing things to get it to work
Any help would be appreciated.
It is an AMD 64 system with an ATI video, I have used all flavors of FGLRX and the Radeon Xorg drivers and the situation is the same.
Thanks
-Barry

---

### Post by pigSTI04 on 2008-08-21
I am having the exact same thing happen. Has this been solved or is there another thread with some instructions detailing a fix?

Thanks for any help.

I'm going to be using this machine as a server and don't like the idea of always logging into failsafe mode.

Just for posterity, this isn't happening on the PC listed in my sig. It's on a compaq presario with a AMD brisbane 3400+

---

### Post by TekNullOG on 2008-09-09
I am experiencing the same problem. I upgraded to 8.04 and GNOME won't start. The failsafe session works and all so how do I make the regular session work again?

---

### Post by TekNullOG on 2008-09-09
I tried selecting GNOME from the list of session instead of the failsafe GNOME and it worked. It asked me if I wanted to make it default ( i said yes ) and when I rebooted, it continued to work.

I don't know why it was no longer default after doing updates. Hope this helps others.

---

