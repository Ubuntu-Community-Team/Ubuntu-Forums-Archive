---
title: "Installation impossible on acer aspire X3995"
date: 2012-09-06
forum: Installation &amp; Upgrades
---

### Post by snarf77 on 2012-09-06
Hi all,

I just bought new desktop from acer (aspire X3995) which come preinstalled with Win7 64bits.

I  would like as usual to install ubuntu alongside (12.04x64) but I just discovered what appeared to be the EFI new bios mode. 

I am now  indeed absolutely unable to boot either with a usb key or live cd of ubuntu  12.04x64. 

When plugging them into the system and booting, I access to the ACER boot media selection  menu and I have two entries (EFI and normal for each of my inserted media).

Choosing EFI mode gives me an unreadable screen during what seems to be an install trial but can't see nothing so just give up?

Choosing non EFI mode, gives me the classical ubuntu live cd selection (install, try...) but whatever the choice I made, the system remains for life with a black screen and a blinking prompt...

I have checked on the Acer support site and discovered there is two type of BIOS (A01-A2 and A01-A2L (for linux)). For now I didn't dare to try as I also need my win7 partition... 

What is strange is that every boot media I had with previous version of ubuntu (10.10, 11.04...) works fine. But I didn't dare to install a 11.10 and jump in the upgrade to 12.04 as I forecast the same kind of reboot problem.

Does someone know what could be those bios revision difference ?

If I test the linux one, does someone know if my win 7 partittion will still boot ?

At last, does someone know any workaround to perform a ubuntu (>11.10) install on this X3995 machine ???

I'm out of trials

Thanks in advance for your help

Snarf

---

### Post by snarf77 on 2012-09-06
Hi some update:

I didn't want to give up too early so I made the two following trials:

- download and try the EFI dedicated ubuntu remix: ubuntu secure remix...
        ==> same result boot ... choose install or try... black screen with blinking prompt...game over

- try to change the BIOS with the Acer Linux BIOS recommended on their support website (using FreeDOS method) and after booting FreeDOS, the bios file installation returns:
        ==>BIOS file not compatible (don't remember the exact wording...)

I start believing this machine has really been designed in order to protect microsoft against Linux !!!

I'm stuck with this machine I can't do nothing with it ...

Please help the pinguin to survive

---

### Post by black veils on 2012-09-06
try nomodeset: [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by snarf77 on 2012-09-07
Many thanks black veils,

It "seems" to work ... indeed it appeard to be more a graphical problem than a EFI problem, and the nomodeset option allowed me to boot normally  on the live USB.

BUT, the installation returns "Ubuntu 12.04 has detected an internal error" concerning a lot of file. I have sent the details of the problem during the installation step and I'm currently trying to go through the end of installation but I'm not confident...

I will revert if the install finally succeed or fails in approx 1 hour....


Thanks anyway for this first step.

Snarf

---

### Post by black veils on 2012-09-07
as the tutorial says, you will need to do it again when booting new system for first time, because the drivers still won't be there, you will need to install them once in the system, using the additional drivers app. 

if it were me though, I would see if I can solely use the Intel integrated graphics, so as to avoid any nvidia or ati graphics driver issues. Do this by looking in your BIOS or EFI configurations.

---

### Post by snarf77 on 2012-09-07
Thanks for your help black veils...


My installation has gone til the end, I have rebooted, edited the grub command line to replace quiet_splash by nomodeset and ubuntu booted normally. I was quite happy at that time but...

...Unforntunately, I have mouse working but no keyboard, and I check the additionnal driver but found none of them so couldn't use graphics drivers.

I think my installation was corrupted related to the error message I got and as during my boot with live USB I had two choices (EFI mode or Not), I decided to restart a fresh new installation and test the other one (EFI mode).

With EFI mode the live USB detected no error and installation went smooth til the end... I was very confident witht this trial but rebooting the computer gave me no GRUB menu but a simple prompt: 
error: invalid arch independent 
ELF magic
     GRUB rescue>

Is that serious doc ??

Snarf

---

### Post by Epodx64 on 2012-09-07
Can't you turn off the EFI Secure boot? I thought that was a requirement of new pc's based on x86_64 (you can't disable it on ARM processors)

---

### Post by snarf77 on 2012-09-07
Indeed, I thought initially that it was a EFI problem but the problem is simply a graphic driver issue with the graphic card GeForce 605.

To finalise my procedure, I have escaped from my grub rescue problem using the boot repair live cd ([http://sourceforge.net/projects/boot-repair-cd/files/boot-repair-disk.iso/download](http://sourceforge.net/projects/boot-repair-cd/files/boot-repair-disk.iso/download)) with the default option (recommended) that has fixed the grub boot.


After that the pc can load grub normally but the linux entry can't be started as is and required to edit the grub entre and add the "nomodeset" option.

Ubuntu was then started normally but the graphics was limited to 1204 * 768 due the default ubuntu driver and the non recognised graphic card.

I have finally "apt-get update && upgrade" and downloaded from package manager the latest nvidia proprietary driver and install them.

Rebooting the pc once again has suceeded. I can now find my Win7 entry and Ubuntu and both are accessible and runnable in normal condition.

For my configuration (Acer Aspire X3995 including nvidia GeForce 605) it saved me.

Thanks to all for your help

---

