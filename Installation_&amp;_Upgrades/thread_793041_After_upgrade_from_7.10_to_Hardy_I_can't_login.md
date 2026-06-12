---
title: "After upgrade from 7.10 to Hardy I can't login"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by brett11808 on 2008-05-13
So I installed 7.10 the updated my system and upgraded to Hardy. Then when asked to reboot I did and now I can't login. I have to use failsafe GNOME to use my computer.
Any Ideas of where to start? I have the next 2 days off of work and I really want to get this Desktop up and running.
Thanks in advance!

---

### Post by Rallg on 2008-05-13
Since you can use failsafe Gnome, your problem might not be too difficult to fix.

From failsafe (or you can use recovery mode), as Terminal:

sudo apt-get update && sudo apt-get upgrade

If there is any driver that was missing at the time you originally upgraded, that may find it for you. After installation, reboot.

If that didn't help, you will have to give details of your hardware, and whether you installed from CD or some other method. Then maybe someone with the same setup can give advice.

---

### Post by brett11808 on 2008-05-19
> **Rallg said:**
> Since you can use failsafe Gnome, your problem might not be too difficult to fix.

From failsafe (or you can use recovery mode), as Terminal:

sudo apt-get update && sudo apt-get upgrade

If there is any driver that was missing at the time you originally upgraded, that may find it for you. After installation, reboot.

If that didn't help, you will have to give details of your hardware, and whether you installed from CD or some other method. Then maybe someone with the same setup can give advice.

OK I tried that and still can't log in and I have also made a fresh 8.04 alternative live CD and installed it on a separate partition and I'm having the same problem with that install.  Whats next??? I don't know how to find out what mother board, graphics card, hard drive etc... so if some one can help me find that i can post it too if that will help thanks

---

### Post by brett11808 on 2008-05-21
After reading through the forums I have come to the uneducated decision that this is a graphics card issue. I have an ATI radeon express 200 graphics card??? Any fixes????

---

### Post by brett11808 on 2008-05-28
Someone out there has to know something about this???

---

### Post by brett11808 on 2008-05-28
Update:
graphics card is working..
still can't login to GNOME or X
I can only use failsafe GNOME
Someone please help

---

### Post by dkuhlman on 2008-06-02
> **brett11808 said:**
> Update:
graphics card is working..
still can't login to GNOME or X
I can only use failsafe GNOME
Someone please help

I have similar symptom -- I can login to a Gnome failsafe session.  I can login to a KDE session.  But, I cannot login to a normal gnome session.

For me it's not a big deal.  I'm OK with KDE.  But, seems like there should be a solution to this.

gnome failsafe mode says something about not running some initialization scripts, which starting a normal gnome session would do.  Where are those scripts?  Is there a way for me to reinstall them?

- Dave

---

