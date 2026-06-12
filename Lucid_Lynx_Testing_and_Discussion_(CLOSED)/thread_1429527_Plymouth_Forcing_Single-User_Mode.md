---
title: "Plymouth Forcing Single-User Mode?"
date: 2010-03-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by moore.bryan on 2010-03-14
Yesterday, when I logged-in to my lappie, I found myself greeted by not GDM, but the text prompt. Clicking Ctrl+Shift+F7, I get back to GDM, so it seems Plymouth is trying to start me in single-user mode. Anyone else having this problem and is there a fix besides just waiting for an update?

---

### Post by keithpeter on 2010-03-14
Hello All

I had this today after a large update. 

I did a shutdown -r and restarted and selected the previous kernel in the grub list (-15) and had a desktop, 

I've just restarted again, and am now on the default 2.6.32-16-generic kernel going straight into gdm, so I can't reproduce the behaviour at present.

Cheers

---

### Post by VMC on 2010-03-14
> **moore.bryan said:**
> Yesterday, when I logged-in to my lappie, I found myself greeted by not GDM, but the text prompt. Clicking Ctrl+Shift+F7, I get back to GDM, so it seems Plymouth is trying to start me in single-user mode. Anyone else having this problem and is there a fix besides just waiting for an update?

I don't think your dropped into a single user mode, because that's superuser. Its just GDM and plymouth is messed up. The VTTY1 asks for a login, correct?

Yes, I get dropped into VTTY1 at times. Not all the time. At any rate, here is the [**_bug#538214_**]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538214") for that.

---

### Post by teh603 on 2010-03-14
> **VMC said:**
> I don't think your dropped into a single user mode, because that's superuser. Its just GDM and plymouth is messed up. The VTTY1 asks for a login, correct?

Yes, I get dropped into VTTY1 at times. Not all the time. At any rate, here is the [**_bug#538214_**]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538214") for that.

I notice it got a fairly low priority (milestoned for beta 2), for some reason. Guess the devs expect everyone to know the keystroke to get out of VTTY1 or something?

---

### Post by moore.bryan on 2010-03-14
> **VMC said:**
> I don't think your dropped into a single user mode, because that's superuser. Its just GDM and plymouth is messed up. The VTTY1 asks for a login, correct?

Yes, I get dropped into VTTY1 at times. Not all the time. At any rate, here is the [**_bug#538214_**]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538214") for that.
Thanks, VMC, you're right... it's just putting me into tty1. Strange, still...

> **teh603 said:**
> I notice it got a fairly low priority (milestoned for beta 2), for some reason. Guess the devs expect everyone to know the keystroke to get out of VTTY1 or something?
This is irritating as well, but we *are* using Lucid. ;-) Maybe we can push for someone to put this a bit higher on the scale...

---

### Post by teh603 on 2010-03-15
Got a reply to my comment on the current bug- aparrently we've got  a developer on it, but he isn't sure he can make it in time for the Beta 1 freeze which is tomorrow.

---

### Post by moore.bryan on 2010-03-17
That makes sense...

---

