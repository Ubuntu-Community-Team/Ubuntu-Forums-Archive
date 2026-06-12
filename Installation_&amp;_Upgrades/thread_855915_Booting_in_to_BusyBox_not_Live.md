---
title: "Booting in to BusyBox not Live"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by Name141 on 2008-07-10
I have recently decided to try Ubuntu again.  However, this time I keep getting booted to "BusyBox" or something of that nature instead of going fully inside of the live CD or install.
I have restarted the computer many times with all fails.
Any ideas what could be causing this?  7.10 also did this.. However, eventually with enough reboots it would turn out the correct LIVE session.

---

### Post by Sef on 2008-07-10
Have you checked the cd to make sure it is good?  Go down to 'check cd for errors'.

---

### Post by Name141 on 2008-07-10
It came from the company, but I shall.

---

### Post by Name141 on 2008-07-11
OK, I tried all the CDs I had.  I got no further than the Ubuntu/Kubuntu scrolling animation.  Till BusyBox shows up.

The CDs where: Kubuntu 8.04, Ubuntu 8.04, and Ubuntu 7.10.

All "from the company".

---

### Post by Name141 on 2008-07-11
The computer is a Dell Inspiron 530, if that helps.  (I am sure specification of hardware is needed though?)

---

### Post by VMC on 2008-07-11
It's a pressed cd and it still fails? Can you boot another bootable disk, form that cd drive?

---

### Post by Name141 on 2008-07-11
I don't know if you mean like a live session , or just a bootable install.  However, I suppose the answer is yes.  I have once before, was able to boot to the LIVE session, and WindowsXP setup has never failed to load.

---

### Post by Name141 on 2008-07-11
I am thinking/guessing it is some kind of hardware it doesn't like?  Such as the externals ? I can see the keyboard lights flashing, then the external lights blinking.. then WHAM.. it stops loading and goes to "BusyBox".

---

### Post by k4sgt on 2008-07-12
The fix is to change the SATA setting in your BIOS from IDE to RAID.  This fixed the very same issue on my Inspiron 530.

---

### Post by Name141 on 2008-07-16
I am not quite sure I understand how this would be a fix to it?

---

