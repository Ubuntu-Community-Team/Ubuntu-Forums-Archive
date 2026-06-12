---
title: "Upgrade from 10.10 to 11.04 freezes on startup"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by Chepe on 2011-05-03
I just tried to upgrade from ubuntu 10.10 to 11.04 (64bit). Everything went fine until the machine tried to reboot. Now it stops while booting on the screen where the ubuntu logo and five red dots appear. I'm unable to open a terminal (alt+ctrl+f1 does not result in anything) and the only thing I've been able to do is to reboot the machine.

 If I reboot by pressing ctrl+alt+delte I see some information for a short while, it seems that the boot stops on "checking battery state" I've googled this, and it seems that quite a few other have had the same problem, but they have been able to open a terminal, any ideas on how I can do this? Or any other suggestions on how to fix this? 

My system is a dekstop with a Nvidia GTX 260 graphics card. I recently installed the newest Nvidia driver. 

Regards

Edit: I forgot to mention that I did an online upgrade

---

### Post by Dutch70 on 2011-05-03
Have you tried other boot options?
[[COLOR="Red"]How to set NOMODESET and other kernel boot options in grub2 [/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by lechien73 on 2011-05-03
If you press the Shift key when the computer is booting (before the Ubuntu "dots") and access the Grub menu, then select "Recovery Mode", can you boot in using Failsafe-X? If so, then try re-installing the graphics drivers when you get in.

---

### Post by Chepe on 2011-05-03
Thanks for the responses guys. I've tried both setting various bios options and reinstalling the driver (didn't know how to get grub up), but still I get the same problem when trying to start up the system..

---

### Post by andrewcow on 2011-05-03
same thing is happening to me. If you go FailsafeX then RestartX I can get in, but it is no permanent solution.

---

### Post by andrewcow on 2011-05-03
Wait I am working again:) I an running Ubuntu in a Virtual Box so I logged in using the FailsafeX method, updated everything and when I restarted, it worked.:)

---

### Post by Chepe on 2011-05-03
> **andrewcow said:**
> Wait I am working again:) I an running Ubuntu in a Virtual Box so I logged in using the FailsafeX method, updated everything and when I restarted, it worked.:)

Cool! How did you update everything, just run sudo apt-get update?

---

### Post by Chepe on 2011-05-04
I was able to solve the problem by starting the system up in failesafeX mode. There I activated the NVIDIA driver that Ubuntu recomended (System - drivers) Now it works like a charm!

---

### Post by lechien73 on 2011-05-04
Great. Could you please mark the thread as [SOLVED] using the "Thread Tools" menu at the top of the page.

Glad it's working ok for you now :)

---

