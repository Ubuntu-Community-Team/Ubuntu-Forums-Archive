---
title: "First time boot..."
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by sbalick on 2008-08-06
I am a newbie stuck with Ubuntu stalling out at first boot.  Grub begins running and the screen clears. The next screen presents itself with "Starting Up...". Then nothing, blotto, zilch - for hours.  I did have some initial problems getting Ubuntu installed on my system as it is rather old (probably about 6 yrs), but adequate - AMD 900MHz 640MB PC133 RAM 250GB HD - generally speaking has done me VERY well, and I'd like to think that it can sustain me for a while longer.  I had some problems getting GRUB to install due to the HD size - that darned Error 18.  All of the forum information and help docs directed me to set up a few partitions on the drive during install setup.  I configured the system with a 4GB / partition, 4GB swap space, with the remaining used as /home.  Install completed, and when the system rebooted to first launch, I was left with "Starting Up..." , and nothing else.

Did I partition the HD correctly?  What am I missing?  The system only responds to the power switch at this point. I have searched all of the forum info and docs - can't find anything to instruct me further...

- Desperately seeking Ubuntu....

---

### Post by meindian523 on 2008-08-06
From details you have given,it doesn't look like there is a partitioning issue,of course considering that your / partition is at the start of the HDD.But,my suggestion would be to create a /boot partition at the start of the HDD(approx 100 Mb is quite enough) and ensure Grub is installed on the MBR.

---

### Post by logos34 on 2008-08-06
> **sbalick said:**
>  4GB swap space

mega overkill...with only 640 mb ram all you need is ~1 gb max. 

I agree with meindian--doesn't sound like a bios/cylinder limit boundary problem--IF, that is, your / is sda1.  ca. 2003 should rule that out.  So I doubt if a separate /boot will help, but never know, you can try

---

### Post by sbalick on 2008-08-06
Thanks for the response.

I didn't notice that the /boot partition was specifically necessary - nor do I recall anything in the docs section of the site, but I will certainly try that.

On the Grub topic, how I install Grub on the MBR? - My only guess here would be to download an app that self installs from a floppy or something in BIOS.  Then, how do I verify it?  Are there readers for sector 0? (MBR) - usually you can't directly read this area.

---

### Post by logos34 on 2008-08-06
see '[COLOR=DarkOrange][Restore Grub from Live CD]("http://ubuntuforums.org/showthread.php?t=224351")[/COLOR]' in my signature

---

### Post by sbalick on 2008-08-06
Logos: thx.  I'll try that in a few hrs.

---

### Post by meindian523 on 2008-08-07
sbalick:
You can read the MBR(or any part of your HDD) by using the dd command and giving the destination as a file.

---

