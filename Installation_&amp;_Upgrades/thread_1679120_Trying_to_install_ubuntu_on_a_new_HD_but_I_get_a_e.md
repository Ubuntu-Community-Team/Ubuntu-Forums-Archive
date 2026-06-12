---
title: "Trying to install ubuntu on a new HD but I get a error message"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by Buying_Some_Time on 2011-01-31
Can someone please help me, i brought a brand new HD today since my old one failed, and now i can't get ubuntu to install (ubuntu 10.10). i continually get the error "no init found, Try passing init=bootarg" then after the error message i have the "busybox" terminal and i don't know what to do. Any ideas?

---

### Post by irv on 2011-01-31
> **Buying_Some_Time said:**
> Can someone please help me, i brought a brand new HD today since my old one failed, and now i can't get ubuntu to install (ubuntu 10.10). i continually get the error "no init found, Try passing init=bootarg" then after the error message i have the "busybox" terminal and i don't know what to do. Any ideas?

If you can boot into the live CD and goto System>Administration> gparted you cant setup the drive from there. Maybe your new HD has never be setup. Another thing to check is to make sure your HD is being seen in your CMOS.

---

### Post by Buying_Some_Time on 2011-01-31
@Irv: No, i can't get that far after grub loads this error is the only thing i get, is there any other way to setup my new HD? Also how would I check to see if it shows up in my CMOS?

---

### Post by irv on 2011-01-31
> **Buying_Some_Time said:**
> @Irv: No, i can't get that far after grub loads this error is the only thing i get, is there any other way to setup my new HD? Also how would I check to see if it shows up in my CMOS?

What you need to do to get into the CMOS is as your PC is booting up you need to hit a key to get to the CMOS. Different PC's have different keys to hit. You should see something like hit the “F2” to get in to the CMOS or maybe the “Delete” key or some other one. Watch the screen at boot up.
Also when you said you can't get that far after grub loads, you are doing it wrong to boot from the CD. If this is a new HD you shouldn't even have a grub on it yet. Did you start an install on it and abort at some point?
When your PC is booting up I think you need to hit the F12 key and choose to boot from the CD drive. Make sure you have the Ubuntu CD in the drive and then select try first to get into the live OS off the CD.

---

### Post by Buying_Some_Time on 2011-01-31
Thanks, Irv! That helped a lot! Once i got my boot order setup right everything worked perfectly!

---

### Post by irv on 2011-02-01
> **Buying_Some_Time said:**
> Thanks, Irv! That helped a lot! Once i got my boot order setup right everything worked perfectly!
Glad I could help.

---

