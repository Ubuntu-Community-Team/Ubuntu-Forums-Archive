---
title: "quick Question"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by czanella on 2010-02-28
Ok I have 2 questions actually, and only one of them is on topic. My first question is, I want to install Ubuntu on my Toshiba Satalite but I had the pleasure of running kubuntu on my moms vaio and my major concern is the boot menu... Vista was and will be my primary OS. On my moms Vaio the Boot menu always loads Kubuntu First...(if i want Windows i have to click every time) is their anyway to change the order in which the boot menu Boots? 
And my second question which is off topic, I am so mad at Vista at the moment... I hate the Windows Update program, It is always so needy... I want a way to shut the stupid thing off without getting some stupid baloon popup that says i shut off the automatic updates... If i shut it off then OBVIOUSLY I KNOW I SHUT IT DOWN, So why does it need to remind me every ten seconds.... I hate being in the middle of something, then restarting my pc, Then Somehow i have 4 updates needing to be installed and it takes like 60min to install them. By the time the updates are done installing what i was in the middle of passes... LIKE CLASS! cant do anything when and update is installing.....Any help would be appreciated, Thanks in advance and for listening to me rambling...

---

### Post by jcitguy78 on 2010-02-28
To answer your 2nd question, Vista was released as an unfinished OS which is why Windows 7 looks and feels like a healthy Vista. I still won't use either though. I am still using XP on my desktop and about to install 9.10 as a stand alone OS on my laptop. 

As for your first question, there is a way to change the Grub menu to boot Vista first, but sadly I have forgotten the step. I have been out of the Ubuntu loop since the 7.10 release just now getting my feet wet again.

---

### Post by czanella on 2010-02-28
DOes anyone else know how to boot windows first? Thanks for your post btw, lol i also am out of the loop.

---

### Post by darkod on 2010-02-28
There are few ways. One is according to the position in the boot menu, counting from 0, not 1. So for example, if Vista Loader is on 5th position, you would enter 4. You need to change this in:

sudo gedit /etc/default/grub

in the line

GRUB_DEFAULT=0 just change to =4, etc.

Save and close the file. Run

sudo update-grub

When ever the vista position changes because of new kernels in the list for example, you will need to adjust the number.

Another way is to use the full vista title, exactly as it is. You can either write it down or copy it from /boot/grub/grub.cfg from the windows entry.

So it would be like

GRUB_DEFAULT="Vista Loader on (/dev/sda1)"

That way you don't have to adjust when new kernels are added because you used the title.

As for the auto updates in vista, there is a way to tell it not to remind you that you have turned it off. Look around in Control Panel, in Security Centre or something like that. I don't remember the exact place any more.

---

