---
title: "Ubuntu upgrade problem"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by You bunt to? on 2010-07-21
Dual-boot system: Win XP Pro / Ubuntu
Hardware: HP Compaq

Upgraded 9.04 to 10.04 LTS,
but the Grub menu has not been updated, and
still shows:

= = = = 
Ubuntu 9.04, kernel 2.6.28-17-Generic
Ubuntu 9.04, kernel 2.6.28-17-Generic (recovery mode)
Ubuntu 9.04, memtest 86+
Other operating systems,
Microsoft Windows XP Professional
= = = =

Selecting Ubuntu 9.04 shows (after pages of text) the
familiar desktop, but both mouse and keyboard are
frozen and the only option is to power down.

Selecting 9.04, recovery mode, shows "fsck from 
util-linux-ng 2.17.12 /dev/sda1 has been mounted 22 
times without being checked, check forced."
I went away for an hour and came back to see the
same screen. If ESC is pressed, I get a purple screen
with "Ubuntu 10.04" in white, and 4 dots below which
change color continuously.. red..white..red etc.
No other key is functional, powerdown is the only exit.

Obviously,  9.04 is gone - but what to do ????

I have my original Ubuntu install CD, version 5.10
"The default installation will erase all existing software
and data from your computer. However an expert
installation is available. If you want to keep your existing 
files alongside Ubuntu follow the instructions carefully
during installation."

If I use this 'expert installation' will I be able to repair
the Grub menu? (I wouldn't want to lose XP too <grin>)

tia
Alan

p.s. posted also in alt.os.linux.ubuntu and alt.os.windows-xp

---

### Post by mikewhatever on 2010-07-21
9.04 doesn't offer upgrading to 10.04, so how did you do it?

---

### Post by You bunt to? on 2010-07-21
> **mikewhatever said:**
> 9.04 doesn't offer upgrading to 10.04, so how did you do it?

You're asking the wrong guy (I'm no expert) - I'm just old and gray and forgetting more than I learn <grin>. The fact that it happened, is beyond me. But thanks for replying!!

---

### Post by DougieFresh4U on 2010-07-21
You could try updating grub from the terminal and reboot

```
sudo apt-get update-grub2
```

---

### Post by mikewhatever on 2010-07-22
Interesting situation. I think the best way to go about would be to reinstall 10.04. Is there any way you can get the cd?
The expert installation mode lets you choose what components to install, but it would still format the Ubuntu root partition. Regardless, neither the expert not the regular installation remove Windows XP, unless instructed.

---

### Post by You bunt to? on 2010-07-22
> **DougieFresh4U said:**
> You could try updating grub from the terminal and reboot

```
sudo apt-get update-grub2
```


Thanks for your reply. I remember during the upgrade, was asked if I wanted to upgrade to grub2 to which I declined. As I was given a choice - I assumed that the current grub was ok to keep.

---

### Post by You bunt to? on 2010-07-22
> **mikewhatever said:**
> Interesting situation. I think the best way to go about would be to reinstall 10.04. Is there any way you can get the cd?
The expert installation mode lets you choose what components to install, but it would still format the Ubuntu root partition. Regardless, neither the expert not the regular installation remove Windows XP, unless instructed.

Thanks for your reply. As to getting a CD I'm downloading it, now!

---

### Post by You bunt to? on 2010-07-23
[QUOTE=You bunt to?;9619333]Dual-boot system: Win XP Pro / Ubuntu
Hardware: HP Compaq
<snip>

Further investigation of this system reveals that besides multiple CPU's, it has multiple hard-drives, so it was very easy unallocate the Ubuntu drive, and have WinXp quickly start without all that BIOS and grub involvement. It wasn't as if I was doing anything different in Ubuntu, than I was doing in WinXP. Rather than using grub (thinking out loud) maybe I can install a switch on this PC that starts one drive or the other to completely isolate WinXP from Ubuntu.

Anyway thanks for all your help. Bye.

---

### Post by You bunt to? on 2010-08-09
> **mikewhatever said:**
> Interesting situation. I think the best way to go about would be to reinstall 10.04. Is there any way you can get the cd?
The expert installation mode lets you choose what components to install, but it would still format the Ubuntu root partition. Regardless, neither the expert not the regular installation remove Windows XP, unless instructed.

Hi Mike,

I wiped Ubuntu, installed the original cd (version 5.10) but then found that 5.10 is not updateable to 10.04, so I downloaded 
"Ubuntu-10.04-desktop-i386.iso", 716,230Kb, copied it to a CD, but the CD doesn't boot (even thought it is 1st to boot in the BIOS boot order).

Help please.

Alan

---

