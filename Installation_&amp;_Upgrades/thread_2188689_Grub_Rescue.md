---
title: "Grub Rescue?"
date: 2013-11-18
forum: Installation &amp; Upgrades
---

### Post by frank18 on 2013-11-18
Hi guys:i have run into a problem with my Xubuntu12.04! the other day 
when i started up the PC,a Dell pentium4 with Xubuntu installed only OPS,
i Had a black blank screen on boot with< Grub Rescue > tried to  use the CD to boot no avail then i tried to reinstall Xubuntu No  Avail,then since i keep many CDs different Distros around i tried Linux  Mint 14 Nadia i struggled a little bit at first but at second try it  booted up then it installed smoothly,
today i was inquiring about this Grub Rescue problem and came across  this Blog about the solution,since i did not try it and don't know if it  works ,I'd like your opinion on this for a future problem of this  arising in the future!  

[http://xubuntu.wordpress.com/2008/01...the-grub-menu/]("http://xubuntu.wordpress.com/2008/01/25/howto-fixing-grub-after-a-windows-installation-and-fixing-the-grub-menu/")

---

### Post by grahammechanical on 2013-11-18
Some of the information in that link is out of date. Ubuntu and the flavours of Ubuntu do not use menu.lst. We have moved on from what is now called Grub legacy to Grub 2.0 and it has a different way of setting up the Grub configuration files. We get the Grub rescue prompt when Grub cannot find the necessary files or when the configuration written in the files does not match what is on the hard disk.

What was the problem with re-installing Xubuntu? Have you tried using Recovery mode from the Grub menu? Have you tried booting one of the earlier kernels that are available from the Grub menu?

Regards.

---

### Post by frank18 on 2013-11-18
> **grahammechanical said:**
> Some of the information in that link is out of date. Ubuntu and the flavours of Ubuntu do not use menu.lst. We have moved on from what is now called Grub legacy to Grub 2.0 and it has a different way of setting up the Grub configuration files. We get the Grub rescue prompt when Grub cannot find the necessary files or when the configuration written in the files does not match what is on the hard disk.

What was the problem with re-installing Xubuntu? Have you tried using Recovery mode from the Grub menu? Have you tried booting one of the earlier kernels that are available from the Grub menu?

Regards.

thank bro for your help: there is no recovery if the cd never booted up   i put cd in the drive changed the boot drive it wouldn't even boot at all kept stalling like an old music  scratched record, then after some minutes of trying i gave up and put there a Mint 14 Nadia cd  and  at first try kinda had only half graffics but i rebooted again and this time it booted up and installed great.
I also run Xubuntu 12.04 on my other Pemtium M desktop and it never did that, maybe it has to with the graffics,

---

