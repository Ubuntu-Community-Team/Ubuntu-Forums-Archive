---
title: "Access BIOS"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by epihammer on 2010-03-13
I have installed Ubuntu 9.10 and love it but I have one question. I tried to access the bios so that I can activate the Num-Lock during bootup but it's asking for a password. I tried my user password but that didn't work. How do I get that password? It's the only OS on the computer.

  Thanks,
 Epihammer

---

### Post by PA_Dummy on 2010-03-13
Do you have the manual for the motherbaord ?

There is a jumper on a three pin socket.  It is generally near the battery.   The battery looks like a new nickel.

Move the jumper from the two pins it is on --- onto the other edge of the three pin setup.  Power on.  Power off.  Reset jumper to orginal position.
Boot and attempt to access BIOS -- usually DEL key.

(The jumper will always be on the center pin)

This will reset the BIOS.

__

---

### Post by epihammer on 2010-03-13
I feel like such a fool. I was thinking that since I reformatted the HD that there shouldn't have been a password to get into the bios. Once I remember that I went into the bios and saw that the num-lock was already setup to turn on during bootup. So my new question is: Is there somewhere within Ubuntu Control Center that I need to set?

---

### Post by d3v1150m471c on 2010-03-13
Your BIOS shouldn't ask for a password unless you applied one to it. In the case that you did, you're in a real crap situation if you forgot it. Your bios is the first thing you see when your computer boots and it has absolutely nothing to do with ubuntu, or any operating system. Look at the F? key prompt when you start your computer that says something like settings or menu adjacent to it. This is not your grub menu.

---

### Post by Mark Phelps on 2010-03-14
> **epihammer said:**
> I have installed Ubuntu 9.10 and love it but I have one question. I tried to access the bios so that I can activate the Num-Lock during bootup but it's asking for a password. I tried my user password but that didn't work. How do I get that password? It's the only OS on the computer.

  Thanks,
 Epihammer

There a ways to blank passwords of various OSs -- but no way to actually recover them.  And, I know of no way to recover a BIOS password, either.

Is this a laptop or desktop? 

If it's a desktop, you can use PA_Dummy's post to clear your BIOS password.

If it's a laptop, apart from taking the laptop apart, there's no way to clear the BIOS password.

---

