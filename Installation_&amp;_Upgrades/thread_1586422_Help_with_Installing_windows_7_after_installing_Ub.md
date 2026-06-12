---
title: "Help with Installing windows 7 after installing Ubuntu"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by Sugadevan on 2010-10-02
Hello im new to Ubuntu..

       Im using windows 7, i decided to try Ubuntu and i tried to install it through live CD.. i wanted windows 7 and Ubuntu in dual boot..

    I installed Ubuntu in a separate partition..installation gone well and after reboot i cannot access windows 7.
Im familiar with windows so i thought reinstalling windows, but on the windows 7 setup it doesn't showing the hard disk.. what can i do.. i will try Ubuntu:), but now i need windows 7 to work:(..

What should i do with Ubuntu to correct the problems?

Please help me..

---

### Post by drdos2006 on 2010-10-02
Boot with the liveCD. 
Run gparted from System => Administration => gparted, and check if the Flag section of the windows partition is marked boot. If it not then change the flag in the Ubuntu section and change the flag in the Windows partition to "boot".

That might help.
regards

---

### Post by Peter09 on 2010-10-02
This is most probably just a grub configuration problem, grub is the boot loader for Ubuntu and should have picked up all the bootable O/S available. I am not too familiar with Grub. I tink the command grub-update should help but it may be worth waiting until someone more familiar with grub can help.

Windows, in genera, does not recognise any other O/S so installing windows will stop Ubuntu from booting.

---

### Post by Rubi1200 on 2010-10-02
@drdos2006

changing the boot flag will not help here.

@Peter09

updating GRUB often helps, but here the OP installed Ubuntu _after_ Windows, meaning that GRUB should have automatically added an entry to the GRUB menu. The fact that it apparently did not indicates a problem, possibly with where GRUB was installed.


@Sugadevan

Use the Ubuntu CD to boot the computer and choose to try in live mode.

Then, post the results of the boot-script linked at the bottom of my post please.

---

