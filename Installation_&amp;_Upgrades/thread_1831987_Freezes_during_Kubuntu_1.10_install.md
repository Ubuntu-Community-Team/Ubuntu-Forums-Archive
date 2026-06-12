---
title: "Freezes during Kubuntu 1.10 install"
date: 2011-08-24
forum: Installation &amp; Upgrades
---

### Post by Sprigglekin on 2011-08-24
I am new to Linux and am trying to install Kubuntu 1.10. I've tried booting from Live CD and Live USB, and tried loading from inside Windows 7 with Wubi but end up with the same problem. The GUI loads and I select start Kubuntu from the menu, a loading screen appears, then the screen freezes with static on the screen.   No error messages have popped up. I have run the memory test from the installation menu with no problems. I use a 64-bit HP with a 3GHz processor.  I really want to try Ubuntu but have been stuck on this problem for a few days. Can anyone help?

---

### Post by ritchie-w on 2011-08-24
Hi,

you may mean 11.04 or 10.10?

I had problems with the kernel 2.6.38.x. It crashed my system during startup as well.

When I am using the kernel 2.6.35.x I can run the system.

The actual version will have the 2.6.38 on the live cd, so you have to use the 10.10 cdrom and update to the actual version via upgrade.

System will crash again, when the kernel is updated to 2.6.38.

Select an older kernel and remove him from software list.

Hope this helps
R.

---

### Post by Sprigglekin on 2011-08-24
It's version 10.10, and I've also tried 10.04.1. So you're saying that v10.10 comes with kernel 2.6.38.x and I need to use 2.6.35.x for it to work on my computer? How do I switch kernels before installing? Again, I have never used Linux before so this is all new to me.

---

### Post by ritchie-w on 2011-08-25
Hi,

if you have used 10.10 of the 64bit, version, it comes with the 2.6.35 kernel. I have installed this version first and upgraded to 11.04 via internet.

Have you just try the one of 32bit version of 10.10 or 11.04 ?

Best regards

R.

---

### Post by SeijiSensei on 2011-08-25
After booting from the CD, you'll be presented with the initial textual Ubuntu installation menu.  Hit F6 and select "nomodeset" from the list, then hit Enter to boot Ubuntu.  Does that help?

---

### Post by Sprigglekin on 2011-08-30
After 4 days of downloading a new ISO it seems as if I've been using 32-bit ISOs on my 64-bit computer. Problem solved, thanks guys :)

---

### Post by ritchie-w on 2011-08-31
Hi,

you will need the 64bit version only if you need more the 4GB RAM.
The 32bit version is much easier to handle and has the same functions.

R.

---

