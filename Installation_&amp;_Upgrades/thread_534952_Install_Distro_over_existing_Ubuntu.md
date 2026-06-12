---
title: "Install Distro over existing Ubuntu"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by BeastoftheEast on 2007-08-25
Hey guys, Hoping to install another distro (BackTrack2)  over my existing ubuntu partition, so as to avoid having to completely remove ubuntu and start from scratch. Anyone had to do this before?

thanks!

---

### Post by Pumalite on 2007-08-25
You can re-install Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Or use Super Grub.

---

### Post by BeastoftheEast on 2007-08-25
Ok, well i went ahead and (probably foolishly) installed, after formatting the ext3 ubuntu partition via Gparted livecd. the Windows partititon is still intact, but it seems backtrack didnt install a bootloader. will super grub go back and do this for me? or do i have to blow the whole thing out again and start anew?

thanks again for the quick response puma.

---

### Post by Pumalite on 2007-08-25
Super Grub can do just about anything for you. Just read the documentation so you know how to use it.

---

### Post by BeastoftheEast on 2007-08-26
Ok, well upon closer look, i found that "lilo" is popping up, but nothing else, so i went to the sudo liloconfig and after the rest of the steps, told it to install to MBR. That's where its been for the last hour and a half. Is this normal? Also will it hurt if i tell it to quit now, and from liveCD configure grub? or supergrub. The fan is spinning at high speed, and i can get to all the menus, but it doesn't appear that anything is happening besides "installing Linux BootLoader" on a blue window, and i really dont want to kill my "bootability" again.

---

### Post by Pumalite on 2007-08-26
You have Lilo working? Can you get to boot all your OS's? Then you are fine. Otherwise I don't understand your question.

---

### Post by BeastoftheEast on 2007-08-26
Ok got it! :roll: Lilo config had appeared to be stuck on the install, when really it had finished and popped the prompt up right below it. It is now working great, thanks again!

---

### Post by Pumalite on 2007-08-26
You are welcome and welcome to Ubuntu too.

---

