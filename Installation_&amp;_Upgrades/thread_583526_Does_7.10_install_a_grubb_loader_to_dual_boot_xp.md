---
title: "Does 7.10 install a grubb loader to dual boot xp?"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by tmcarson1 on 2007-10-20
I installed 7.10 on my 2nd hard drive, the install went just fine, but now when the computer starts up it goes right to windows and does not allow me to choose between Ubuntu or XP.

Any thoughts on what I did wrong?

I manually did the partitions one /, one /swap and the rest /home.

Any advice is appreciated.

---

### Post by Can+~ on 2007-10-20
I was particularly careful when installing gutsy, and I noticed that, in the end of the installation (via LiveCD) when you were presented with all the settings, there was an "Advanced button" on the bottom right. There was something like "Where to install grub" and "Do you want to participate in the popularity program?".

If you don't mind reinstalling all again, maybe you should check that out; but if you want to install only grub, I'm sure there is a good tutorial around here (*searching*).

*edit*: [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html)
*edit2* [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by tmcarson1 on 2007-10-20
> **Can+~ said:**
> I was particularly careful when installing gutsy, and I noticed that, in the end of the installation (via LiveCD) when you were presented with all the settings, there was an "Advanced button" on the bottom right. There was something like "Where to install grub" and "Do you want to participate in the popularity program?".

If you don't mind reinstalling all again, maybe you should check that out; but if you want to install only grub, I'm sure there is a good tutorial around here (*searching*).

*edit*: [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html)
*edit2* [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Thanks I will give that a try, I didn't see that either.

---

### Post by tmcarson1 on 2007-10-20
> **Can+~ said:**
> I was particularly careful when installing gutsy, and I noticed that, in the end of the installation (via LiveCD) when you were presented with all the settings, there was an "Advanced button" on the bottom right. There was something like "Where to install grub" and "Do you want to participate in the popularity program?".

If you don't mind reinstalling all again, maybe you should check that out; but if you want to install only grub, I'm sure there is a good tutorial around here (*searching*).

*edit*: [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html)
*edit2* [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)


I tired a fresh install and it installed fine but failed to install a boot loader even though I checked the box for MBR under the advanced tab.

Not sure what the issue is but my computer goes straight into xp without an option to boot ubuntu.

---

### Post by tmcarson1 on 2007-10-20
As it turns out, I tried unplugging the hard drive that has windows installed on it and started the computer, the grub loader comes up fine and gives me the option of starting XP or Ubuntu, but of course the XP drive is not connected so I cannot start XP this way.

Why did it install this grubb loader onto the same drive it put ubuntu onto and not on the hard drive that has windows and I guess the MBR on it already?

Any advice is appreciated.

---

### Post by Can+~ on 2007-10-20
> Why did it install this grubb loader onto the same drive it put ubuntu onto and not on the hard drive that has windows and I guess the MBR on it already?

I didn't understand what you said there but; grub must be installed in the hard drive that starts first, usually, the one set as master (your windows hard disk in this case), it won't replace anything.

Another way, should be entering the BIOS and try changing the order.

---

### Post by jag2000 on 2007-10-20
I also have 2 physical hard drives in my pc.I just put the cd in .. rebooted and it loaded up. I installed 7.10 and rebooted removed cd and i did have a grub menu. i am unsure why it didnt work for you.
(btw i am dual booting XP pro and 7.10

---

