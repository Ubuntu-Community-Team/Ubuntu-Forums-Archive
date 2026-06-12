---
title: "Virtual Box Install problem"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by Coach_Mark on 2009-11-19
I have downloaded VB 3.0 in order to load up windows XP to run a couple things that don't run on anything else.  i have downloaded an XPsp3 ISO file.  I have put it on both a CD and my hard drive, with the same results.  attached are two screen shots of how i have set VB to look at the file.  these shots are with the ISO on the desktop.  i tell VB to look for the ISO, but when I try to launch, it tells give me the message "no bootable medium found."  can any one help me figure this out?

---

### Post by snowpine on 2009-11-19
Can you boot from the CD regularly (not in virtualbox)? If not, I would recommend contacting Microsoft customer support directly and requesting a replacement CD for the defective one they sold you. If the CD has a "check md5sum" or "check CD integrity" feature (like Ubuntu does) that is worth trying as well.

---

### Post by mocoloco on 2009-11-19
Your VB setup looks right.  It might be that the disc actually isn't bootable, try booting from your CD on your actual system to find out.

---

### Post by Coach_Mark on 2009-12-30
I finally had time to get back to this.  Turns out there were a couple of issues.  First, the ISO download was apparently bad.  I borrowed a disc from someone and it loaded just fine.  Second, I could not get the F8 agreement to work.  an issue I had elsewhere provided the solution.  There was a setting in the BIOS on the Dell which had the function keys set to do multimedia first, instead of the function.  I changed the setting, and everything worked great.

---

