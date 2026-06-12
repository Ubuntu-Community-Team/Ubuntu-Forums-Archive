---
title: "Noob Can't Boot for 2+ Weeks"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by documentarytt on 2010-12-11
Dear Ubuntu Community:

I installed the latest Ubuntu version about 3 weeks ago. Everything worked fine, even the design looks great.

I did this while I still had Windows 7 on it because I wanted to see if I could completely switch to Ubuntu in the long run.

However, after installing some auto-updates, I wasn't able to boot any more. I keep receiving the GRUB RESCUE ERROR MESSAGE (NO SUCH DEVICE).

I admit that I am completely desperate, I have no idea what to do and can't stand the fact that I can't use my laptop.

I have no idea on how to write commands in Linux, nor do I have a "Live CD".

I don't want to throw the laptop away, it was expensive but frustration is building up.

Thanks in advance,
Tom

---

### Post by ryadav on 2010-12-12
1st download a liveCD, boot into rescue mode, then reinstall GRUB

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

this is a great time to learn some linux

---

### Post by sikander3786 on 2010-12-12
Yes that seems like re-installing Grub2 to the _*proper*_ device might fix the problem. If you don't feel confident, post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would give us a better look of your setup and we'll be able to give the *_exact_* commands to follow.

While posting, click the # icon in post menu and paste your text in between the generated code tags to make it easy to read.

---

### Post by Rubi1200 on 2010-12-12
Hi documentarytt and welcome to the forums :)

Posting the results of the boot info script as sikander3786 suggested would be a very good idea before you go about installing/reinstalling anything.

We also need to know if this is a Wubi install or a regular install to the hard-drive.

Thanks.

---

### Post by bcbc on 2010-12-12
+1 on what Rubi1200 said.

However, you said you don't have a live CD, so likely you have a wubi install. And... if you just want to get windows booting, just install the windows bootloader. This will work whatever Ubuntu you installed.

For win7 you'd boot from windows disc to a repair command prompt and run: bootrec.exe /fixmbr

Oh and PS, welcome to the community. And please don't consider trashing or reinstalling anything. It's likely a very easy fix despite the appearance (we see these all the time... unfortunately :( )

---

### Post by documentarytt on 2010-12-12
Thank you for the fast replies.

I downloaded Unbuntu and installed it within Windows, so I had Dual-Boot.

As I said before, I don't have the LiveCD, nor do I have a repair disc. Since the laptop does not boot, I am not able to use Boot Info Script.

However, tomorrow I will have the chance to burn a CD. Should I burn the ISO to a CD and just reinstall?

---

### Post by Rubi1200 on 2010-12-12
No, do not reinstall.

Burn the ISO to CD at the lowest possible speed.

Then, boot the computer with it, after setting BIOS to boot from the CD drive, and choose to try Ubuntu not install.

Then, you can run the script we mentioned before and post the results here.

Your Wubi install is most likely affected by one or other of the problems outlined here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

These issues can be fixed and there is no need to reinstall.

Post the results of the script and we can advise you further.

Thanks.

---

