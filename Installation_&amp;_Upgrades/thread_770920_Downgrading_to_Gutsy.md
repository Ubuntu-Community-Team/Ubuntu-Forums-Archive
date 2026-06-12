---
title: "Downgrading to Gutsy"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by iflanery on 2008-04-27
After a disastrous attempt at upgrading Ubuntu to Hardy Heron, my computer stalled (after restarting) at the loading screen, then showed me what wasn't working. So I had to do a clean reinstall of Gutsy, wiping out all my data in the process (because I still haven't had the courage to try moving my /home/ directory to a separate partition).

Things are working alright for the most part right now, but I have two nagging problems.

1) After logging out, I'm taken to a blank screen with no login prompt (and yes I do have KDM installed). Basically, every time I want to get back into my system, I have to do a hard restart. I've got the nvidia-glx-new drivers installed. Could that be the problem?
**UPDATE:** I've uninstalled the nvidia-glx-new drivers and gone back to nvidia-glx. Doing Ctrl-Alt-Backspace Did nothing. Damn.

2) One of my first tasks upon completing the installation was to reinstall GNOME. This also went without much headache, though I can't for the life of me figure out how to get the window borders/controls to work.
**UPDATE:** It was suggested to me on a newsgroup that I check to see if I have GDM installed, which I do. I've not tried to log back into GNOME because of the problem above.

Thanks in advance for any help.

---

### Post by chek2fire on 2008-04-28
Try to use envyng programme and install nvidia driver with it. You can find it in synaptic

---

### Post by iflanery on 2008-04-28
Problem solved. What I did was enable the restricted drivers for my card.

---

