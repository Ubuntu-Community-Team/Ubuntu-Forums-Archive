---
title: "Dual booting Ubuntu 12.04 LTS and Windows"
date: 2014-09-30
forum: Installation &amp; Upgrades
---

### Post by kellyjmorris on 2014-09-30
I am running a computer with 64-bit AMD FX-8120 Eight-Core Processor x 8, 7.9 GB memory, and Ubuntu 12.04 LTS on a 500 GB hard drive. (For reasons that I can only attribute to an extended illness at the time I installed the OS, I installed the 32-bit version on a machine with a 64-bit processor.)

I have been trying to install 64-bit Ubuntu 14.04.1 LTS on a 1 TB unformatted hard drive but have been entirely unsuccessful in spite of advice from a variety of sources. (As a matter of fact, it has been driving me crazy). My main source of tech support -- my computer "jack-of-all-trades" son -- issued me an ultimatum: if I want him to be my tech support, I've got to switch to an OS that he can deal with, i.e. Windows 7 or 8. So, I've decided to give up on trying to install Ubuntu 14.04.1 and install Windows on the 1 TB hard drive. I desperately need to get settled and productive.

I haven't dual-booted in ages. I assume that after installing Windows on the 1 TB hard drive and upon rebooting, grub will offer me the choice of which OS to boot into. Is this correct?

I assume that if I want to then change the grub configuration to make Windows the default OS on start-up, I can do so. Is this correct? Is there a GUI for this?

Back when I was multi-booting, I seem to remember that Windows had to be first in the boot sequence. Is this still true? If so, how do I accomplish this? Can I simply switch the physical order of the two hard drives?

Any advice would be greatly appreciated.

TIA kellyjmorris

---

### Post by mastablasta on 2014-09-30
> **kellyjmorris said:**
> 
I have been trying to install 64-bit Ubuntu 14.04.1 LTS on a 1 TB unformatted hard drive but have been entirely unsuccessful in spite of advice from a variety of sources. 

what part was unsuccessful? troubleshoot that first before you attempt another install as same thing will happen again only in a more complicated set up.

does the live session boot ok (i.e. the try it option?).


> 
I haven't dual-booted in ages. I assume that after installing Windows on the 1 TB hard drive and upon rebooting, grub will offer me the choice of which OS to boot into. Is this correct?

Yes.
> 
I assume that if I want to then change the grub configuration to make Windows the default OS on start-up, I can do so. Is this correct? Is there a GUI for this?

Yes and yes, although you only need to edit a file and move windows where you want it. [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

go to second answer here : [http://askubuntu.com/questions/52963/how-do-i-set-windows-to-boot-as-the-default-in-the-boot-loader](http://askubuntu.com/questions/52963/how-do-i-set-windows-to-boot-as-the-default-in-the-boot-loader)

or:

use grub customizer: [https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

> 
Back when I was multi-booting, I seem to remember that Windows had to be first in the boot sequence. Is this still true? If so, how do I accomplish this? Can I simply switch the physical order of the two hard drives?

not anymore. long time ago you had to have it in the first part of hard drive. however it is still true that it is easier to install Ubuntu into dual-boot if windows is installed first. less steps...if you have windows installed in MBR (not uefi mode) you need to have max 3 primary partition and designated empty unallocated / unformatted disk space.

---

### Post by kellyjmorris on 2014-09-30
> **mastablasta said:**
> what part was unsuccessful? troubleshoot that first before you attempt another install as same thing will happen again only in a more complicated set up.

>I tried everything (nomodeset, etc.) that was recommended in various fora, but I could never get past the installation welcome window. Once I got there, the keyboard & mouse were not operating.

does the live session boot ok (i.e. the try it option?).

>I get a bit farther in the "live" "try it" session, but once I get to the 14.04 screen with the intention of installing from there, the keyboard and mouse don't work there either.



Yes.

Yes and yes, although you only need to edit a file and move windows where you want it. [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

go to second answer here : [http://askubuntu.com/questions/52963/how-do-i-set-windows-to-boot-as-the-default-in-the-boot-loader](http://askubuntu.com/questions/52963/how-do-i-set-windows-to-boot-as-the-default-in-the-boot-loader)

or:

use grub customizer: [https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

>Thanks. I'll take a look at these links.


not anymore. long time ago you had to have it in the first part of hard drive. however it is still true that it is easier to install Ubuntu into dual-boot if windows is installed first.

>I don't think that this is an option, unless I could 1) shut down; 2) disconnect both hard drives, 3) move the 1 TB HD into first position, 4) reboot & install Windows, 5) shut down again, and 6) reconnect the 500 GB HD but this time in 2nd position. I don't know if this makes any sense or not.

 less steps...if you have windows installed in MBR (not uefi mode) you need to have max 3 primary partition and designated empty unallocated / unformatted disk space.

Thanks very much.  kellyjmorris

PS Excuse me for screwing up the formatting of my reply.

---

