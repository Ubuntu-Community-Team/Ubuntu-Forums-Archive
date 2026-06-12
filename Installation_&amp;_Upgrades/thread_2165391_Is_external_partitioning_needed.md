---
title: "Is external partitioning needed?"
date: 2013-08-04
forum: Installation &amp; Upgrades
---

### Post by pyroph2 on 2013-08-04
I'm a noob and I want to install Ubuntu in my Samsung np300e5c laptop. I've already used Ubuntu installed via wubi, but now I want to try it for real.
I've already read some tutorials, and in the tutorial shown [here]("http://www.ubuntu.com/download/desktop/install-desktop-long-term-support") it seems that during installation the partition will be automatically created; my only decision would be to choose how many space I want the new partition to have. 

Is this correct? Because I'm reading a lot of people saying they had to make the partitions before installing ubuntu, and even using software like gparted and others.

Thank you :)

---

### Post by Bashing-om on 2013-08-04
pyroph2; Hi Welcome to the forum.

The installer offers you three options to install.
1) Erase everything on the hard disk and install ubuntu ... requires very little input on your part ... the install wizard sets all partitions up; It do mean what it says ---any other operating system installed is history, period !
2) Install along side another operating system ... again requires little input on your part .. --but do back up any data that is important to you ... power failures and mishaps do happen--and again the install wizard makes all the decisions. Only one physical hard drive -> ... GRUB (GRand Unified Bootloader) you want installed onto the MBR of ..sda. The installer will chainload Windows boot code to allow the choice of which system to boot. 
3) something else... note the advisory ... experienced users may use this option ... and then yes: a) partitions may be set up prior to starting the install, b) partitions may be set up manually during the install ... there is no reason if you are willing to make mistakes and learn from them that you can not use this option. But there is a steep learning curve !.. There is always the option to go back to the partition editor (GParted), erase all that you have done up to that point, and re-do once more ... or in the installer, revert back to the initial partitioning screen and try try try again.

-------
Depending on what you want of your system is what you choose... important to consider if you will never ever require Windows again... new to ubuntu it is recommended to keep Windows until such time as you are comfortable with ubuntu and absolutely certain that you have no need of Windows -> CHOOSE "install along side of" --data backed up ... and let the installer do it's thing ....... no fuss no muss !

Then, once comfortable with the ubuntu operating system in general ... you can make decisions on altering the basic system to suit your needs at that time.

We remain here to guide and help you in any way we can ... installing ubuntu ... a piece of cake .. no sweat.

[INDENT][INDENT]your OS, your choice[/INDENT][/INDENT]

---

