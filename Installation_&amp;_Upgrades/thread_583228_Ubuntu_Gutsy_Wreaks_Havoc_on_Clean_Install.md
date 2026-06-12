---
title: "Ubuntu Gutsy Wreaks Havoc on Clean Install"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Glunn11 on 2007-10-20
Hello Ubuntuforums!
After much combat with the upgrade feature from Feisty to Gutsy on a dual-boot with Vista Home Basic, I've decided to clean install it myself. I've decided it would have been better to wait for the ridiculously long 9 hour download on a 500Mbit DSL connection, instead. But, hindsight is 20/20.

After cleaning the Ubuntu Feisty partition, GRUB spazzed out with Error 15. Well, that was expected: GRUB doesn't exist anymore.
So, I plop in my first Ubuntu: Gutsy Gibbon live CD. This one won't boot in normal graphics mode, so I go into Install. After finishing the configuration steps, installation ensues. I used the Use Largest Amount of Free Space option, as I did before. However, I was greeted by a loving error that said some files could not be copied. My error? I didn't use ISO Recorder to erase the disk. OOPS! So, I assume I will have to re-wipe the partition.
I make a second one. Lo and behold, BAD BURN! (set it to 10x instead of 4x and won't load any options on the beginning menu)
Third one: this is when I found out my first one wasn't erased properly, so I erased it properly and re-burnt. Guess what? It locks up on the Loading Linux Kernel screen.

HELP! My computer is currently useless!

---

### Post by hlmuller on 2007-10-20
A little more information please.

What are you installing on?  Desktop or Laptop, make, model, processor, video card, etc.  The more information you can provide, the better.

---

### Post by Glunn11 on 2007-10-20
Desktop - eMachines W3611 with Intel 945G chipset.

---

### Post by hlmuller on 2007-10-20
Ok, you should be able to use either the Gutsy i386 or amd64 isos.  I would recommend the i386 iso.  Which iso have you been trying to install?

In what operating system (i.e. windows, linux, etc) are you burning the iso?  And what application are you using?

---

### Post by Glunn11 on 2007-10-20
I've been using the i386 image and ISO Recorder for Vista. Both have worked great in the past. I'm trying a never-been-used-before CD, and hopefully it will work this time.

---

### Post by hlmuller on 2007-10-20
Ok, now I understand you have been unsuccessfully trying to reuse a cd.  I always use new CDs for ISOs, and never use RW anymore.  Let me know how the new LiveCD works.

---

### Post by Glunn11 on 2007-10-20
All worked well, and I'm typing this very message successfully in Gutsy Gibbon! Thanks for coping with my stupidity! :)

---

