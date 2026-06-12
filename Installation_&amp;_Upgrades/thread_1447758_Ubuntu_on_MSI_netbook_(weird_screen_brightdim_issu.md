---
title: "Ubuntu on MSI netbook (weird screen bright/dim issue)"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by purebuilt on 2010-04-05
When I boot into Ubuntu on my MSI netbook there is an black meter device appears and the display goes from bright to dim and back and forth. I can only get rid of it by opening up the terminal or some other application, but even that does not always work. How can I turn this off?

Thanks.

DB

---

### Post by gordintoronto on 2010-04-05
Is this part of Ubuntu, or part of your BIOS? Have you checked your computer manual?

If it's Ubuntu, what do you have in Preferences/Startup Applications?

---

### Post by purebuilt on 2010-04-05
It is part of Ubuntu. It has nothing to do with the BIOS. I don't know what program it is to turn it off. That's what is frustrating. A black meter with a brightness symbol and meter bar shows up on the screen and goes back and forth adjusting the brightness. I've look at all the settings and don't know what is doing it to turn it off.

Thanks.

DB

---

### Post by Aleks` on 2010-04-18
I have exactly the same problem on my MSI Wind U100. I've tracked the problem down and I think that it is somewhere in the notify-osd daemon. 

Whenever I kill it (while the display is oscillating) it stops oscillating but then (after a few seconds time) the notify-osd daemon comes back online and the oscillations continue.

Any help would be greatly appreciated.

---

### Post by purebuilt on 2010-04-18
There are two issues. The flickering but once that is stopped with the workaround, then the brightness will go down and have to be raised. This is a separate issue. Not sure exactly the cause. It could be a BIOS issue.

Here's the link: [http://www.ubuntu.com/getubuntu/releasenotes/910#Brightness%20flickering%20on%20MSI%20Wind%20netbooks%20with%20KMS](http://www.ubuntu.com/getubuntu/releasenotes/910#Brightness%20flickering%20on%20MSI%20Wind%20netbooks%20with%20KMS)

Look for these two:

"No Xv support for Intel 82852/855GM video chips with KMS

When using the default kernel-mode-setting (KMS) option in Ubuntu 9.10, users with Intel 82852/855GM cards will find that they are unable to use the Xv extension for playing videos. This may show up as high CPU usage or stuttering during video playback, or a failure to play videos at all with some applications. As a workaround, users can add the option nomodeset to the kernel boot options in the grub config (for GRUB 2: edit /etc/default/grub and add nomodeset to GRUB_CMDLINE_LINUX, then run sudo update-grub; for GRUB 1: edit /boot/grub/menu.lst and add nomodeset to the line beginning with # kopt=, then run sudo update-grub), to disable the use of KMS. (395932) 
Brightness flickering on MSI Wind netbooks with KMS

A bug in the kernel-mode-setting (KMS) brightness handling on certain MSI Wind netbooks, including the U90, U100, and U120, results in a bad flickering effect whenever the brightness is changed on the desktop, as the brightness is repeatedly raised and then lowered. Users affected by this issue can use the same workaround as described in the previous note to disable KMS. (415023) 
"

---

### Post by Aleks` on 2010-04-19
When I disable KMS (nomodeset in grub) and when I boot the system, the ubuntu startup logo is squashed (problem with resolution I guess) and the UNR interface is slow as hell and eventually it freezes.

But, lol, the flickering problem is gone. Now, how can I revive my UNR environment ???

---

