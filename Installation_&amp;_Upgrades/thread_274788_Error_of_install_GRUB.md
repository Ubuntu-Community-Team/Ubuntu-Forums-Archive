---
title: "Error of install GRUB"
date: 2006-10-10
forum: Installation &amp; Upgrades
---

### Post by misatran on 2006-10-10
I've already install win XP, and linux redhat in my PC, so I've had GRUB somewhere in my PC. But when I install Ubuntu, it appears to install GRUB again from the CDROM, and has errors there, when I tried to reinstall it, then reboot, my PC cannot boot to any OS, but a black screen with white word GRUB appears to full screen.
I dont know how to fix the problem, that's why I used partition magic to format the partition in which I installed ubuntu, but the problem still remains
Please help. Thanks.

---

### Post by Kateikyoushi on 2006-10-10
You can try [this guide]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub") to fix your grub.

---

### Post by misatran on 2006-10-10
I've said that none of my OSs can boot, that's why I cant gain access to any desktop, so no command can be typed. It only appears the word GRUB and flashing...

---

### Post by randoj on 2006-10-11
hey. i had the same problem and took me ages to find a solution but i finaly did. You have to make a swap drive of atleast 256mb. so when on instalation it ask to edit the partitions choose edit partions Manually. then resize the Ubuntu partition by 260mb min. and then make it a swap drive. you will notice if you have done it right that the windows partition will say Fat32 or NTSF the swap drive should say SWAP or it will not work.

---

### Post by misatran on 2006-10-11
I've made a swap drive of 350mb too..As I already said before, I have Win XP and Redhet Linux installed in my PC, and GRUB was working properly, But problems appear when I tried to install Ubuntu.
One more thing, when I try to install Ubuntu again, I receive an alert like this(It has already alert me before at the first time of trying to install): **No installable kernel was found in the defined APT sources. You may try to continue without a kernel and install for own kernel later. This is only recommended for experts, otherwise you will likely end up with a machine that doesn't boot. Continue without install kernel?**

Anyone can help me with this??? Or at least please make the PC boot to my Windows XP. Great thanks.

---

### Post by Predius on 2006-10-11
What version of Ubuntu are you trying to install?

---

### Post by misatran on 2006-10-11
I'm trying to install Ubuntu 6.06, downloaded from the ubuntu.com, if there are many problem, is it caused by corrupted download?

---

### Post by Predius on 2006-10-11
> **misatran said:**
> I've said that none of my OSs can boot, that's why I cant gain access to any desktop, so no command can be typed. It only appears the word GRUB and flashing...

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

This link was posted before. Try using the LiveCD to fix GRUB, and come back to tell us how it went.

---

### Post by misatran on 2006-10-11
It said when u get to the desktop, open a terminal???
I'm new to linux, so could u explain it more clearly, where's the desktop, where's the terminal?

---

### Post by Kateikyoushi on 2006-10-11
> **misatran said:**
> I've said that none of my OSs can boot, that's why I cant gain access to any desktop, so no command can be typed. It only appears the word GRUB and flashing...

Use the live ubuntu cd to boot your computer, do not click install on the desktop. 
To open a terminal, go to applications on the top bar >> accessories >> terminal.

Then follow [these]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub") instructions.

---

### Post by gn2 on 2006-10-11
If it's possible to fit an extra hard drive, this option might make things simpler for you in the future:

[http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

