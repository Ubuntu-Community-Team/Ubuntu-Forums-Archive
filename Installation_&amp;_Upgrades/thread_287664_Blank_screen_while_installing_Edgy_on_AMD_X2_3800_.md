---
title: "Blank screen while installing Edgy on AMD X2 3800 with ATI X700"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by nbhaskar on 2006-10-29
By the way my machine used to be a dual boot with XP and breezy. I deleted linux parttion and reduced the partion size with Partition Magic in windows and also I fixed the MBR with fixmbr command, now GRUB shows only windows. I had installed Breezy on my machine with no problems, well, except ATI X700 problem.

Now I'm trying to install edgy eft in the same machine as a dual boot, when live CD starts, an error pops up saying my graphics is not set up correctly and I should correct it and start gdm, then I click ok on the next 2 windows. Finally I get a blank black screen, i don't see any thing but whatever I type in, it looks like there is no response from the system at all. After that, only thing I can do is reboot. Please check my signature for my machine config. I've tried i386 as well as AMD64 version with no luck.

I've a Toshiba laptop Pentium M, 1 GB RAM, 80 GB and intel integrated graphics chip, edgy worked like a charm when booted from the i386 iso CD.

Any help would be appreciated. Thanks in advance, I know I can count on the experts in the forum.
](*,)

---

### Post by kypez on 2006-10-29
I am sure that there are alot of people with that problem. Like me for instance. I too have the x700 card and I also get a black screen at the login. CTL-ALT-F2 brings me to a screen with a bunch of nonsense which none of it I can read. CTL-ALT-F7 brings me back to the login screen where I can actually type in my login and pw. I then hear the intro music as 6.10 loads but I still can't see anything. The key is getting to the terminal where you can then edit your xorg.conf file. I haven't figured that out yet and I am still waiting for an answer!

---

### Post by nbhaskar on 2006-10-29
Just managed to login to edgy. Here are the steps I followed.

Once you are in the blank screen press Ctrl + Alt + F1, this will take you into command prompt. There you can type sudo vi /etc/X11/xorg.conf. Modify the Device section to have "radeon" instead of "ati". Then you need to login as root, the technique I followed in type sudo shutdown - 1, which will shutdown the GDM and take you to root prompt in 1 minute. Then type gdm which will start the GDM and voila!! you are on.

As a matter of fact, I'm typing this from my edgy login.

But when I try to install edgy, i go past the first 5 screens by giving appropriate information, on screen #6 I selected the appropriate partitions for /, /home/ swap and when I click forward, it tells me that there is not root mount selected. But I double checked the values, I see / selected.

Advance thanks for any help.

---

### Post by nbhaskar on 2006-10-29
Finally I did install edgy on my machine and I'm typing this from edgy.

thanks to everybody who helped me get through this installation.

:-D

---

