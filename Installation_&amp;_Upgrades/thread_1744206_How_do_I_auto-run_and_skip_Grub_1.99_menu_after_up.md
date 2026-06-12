---
title: "How do I auto-run and skip Grub 1.99 menu after upgrade?"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by scooby1970 on 2011-04-30
This seems to be a strange problem, and I have searched high and low for answers. Since Ubuntu 10.04 I have been upgrading via LiveCD and had no problems, however after an upgrade to 11.04 I now have Grub 1.99 giving me a list of versions to chose from before the OS loads.

Now, call me fussy, but I don't want this, I just want to turn on my PC and go straight into Ubuntu as it always has done.

I have tried various fixes such as looking for old Kernals in Package Manager, but no old kernals show up! Same for Ubuntu-Tweak, nothing shows up when I click on clean kernals.

There has to be a soloution to this!!! Can someone please help me?

Thank you in advance.

Mark

---

### Post by dino99 on 2011-04-30
you might think about the day you will get trouble with this setting :(without countdown timer from /etc/default/grub)

- broken kernel
- recovery mode not easily available

well do it as you like

---

### Post by scooby1970 on 2011-04-30
> **dino99 said:**
> you might think about the day you will get trouble with this setting :(without countdown timer from /etc/default/grub)

- broken kernel
- recovery mode not easily available

well do it as you like

So you're saying it's better to have the option of recovery mode and other Kernals etc?

I have tried Startup Manager to give it a 3 second on-screen presense, but that does not work either, even if that worked I would be happy with that.

Mark

---

### Post by dino99 on 2011-04-30
its my point of view and experience of course, but what a difference 3 seconds makes in your life by the way ?

---

### Post by scooby1970 on 2011-04-30
Is there a way to disable the grub menu though??? I've tried everything I can find so far.

:) Mark

---

### Post by scooby1970 on 2011-04-30
I've been trying to remove Grub from asking me which version all day, tried everything in my original post and nothing. Can anyone suggest any help please?

:) Mark

---

### Post by jonathansfl on 2012-01-24
I'm using 11.04

I have this same problem and no one answered this thread. I'm setting Ubuntu up for clients and I DONT WANT THEM TO SEE THE GRUB MENU. I do care about the 3 seconds, but more importantly i don't want them screwing it up by clicking something. Furthermore, they don't have keyboards, they have tabletPCs with touchscreens, so we have to connect a keyboard just to click Enter to get past this damn menu. 

How can i hide this grub menu? I too have tried the Startup-Manager. No effect. I used Terminal and changed the /etc/default/grub file parameters to GRUB_TIMEOUT=0 and GRUB_HIDDEN_TIMEOUT=0. I even added GRUB_SAVEDEFAULT=true to try and fix this nonsense. 

How can we skip the grub menu?

---

### Post by Canaryguy on 2012-01-26
I'm using Ubuntu 11.10 and I'm also trying to find a solution for this. I haven't had luck so far but probably the solution is very easy. I also just want to avoid de grub menu and to see it only when I need it via keeping Shift pressed while restarting the computer.

---

### Post by Liber81 on 2012-12-15
Hi,

I had exactly the same problem. I had to edit "config.cfg" manually, it means change all entries with "timeout=-1" to "timeout=0".
This is not safe procedure, but it works for me and it did not harm my system (Linux Mint 13 64bit).

---

