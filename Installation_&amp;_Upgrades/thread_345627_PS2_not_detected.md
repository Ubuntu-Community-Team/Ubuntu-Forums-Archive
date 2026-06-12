---
title: "PS/2 not detected????"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by DarkStarAeon on 2007-01-24
Hi,

 I installed Ubuntu on my HP Pavilion a1440n computer using the PS/2 keyboard that came with it. It installed just fine. But as soon as it rebooted the keyboard failed to function anymore.

So, I tried another one, and another one, and another...no PS/2keyboards are working, only wireless keyboards. Problem is, the wireless keyboard I'm using right now to type this belongs to another computer where it is needed.

I did go into System > Preferences > Keyboard and I tried every single layout on the list for 4 different PS/2 keyboards...but nothing worked.

So, how is it I can install Ubuntu using a PS/2 keyboard but can't use one after install?

I know it's not the PS/2 port because I also have PC-BSD and WIndows XP onthis computer and the PS/2 keyboard works fine on both, and it works during start up and in the BIOS.

Does Ubuntu have problemswith PS/2 keyboards?

If so, can anyone recommend a wireless keyboard that works well with Ubuntu?

---

### Post by louieb on 2007-01-24
Now that just weird. I've seen some posts about USB keyboards and GRUB problems.  And I have had trouble with right enter key when using DSL Linux. But yours is the first PS2 keyboard just not working at all problem.  My wild as guess of the day:  The installer burped and scrambled some bits in xorg's keyboard module. 

Just wondering can you boot to recovery mode and see if the keyboard works when just running a command line interface. If the board works there then something went wrong when xorg was installed. and maybe the  fix is to just reinstall the xorg package.

---

### Post by DarkStarAeon on 2007-02-12
It is weird, first time I've ever seen it happen on any OS.

I gave up and just went and got another wireless keyboard.

Note: the Logitech S-510 Cordless Desktop keyboard seems to work on just about every OS/Distro I've tried it on.

---

