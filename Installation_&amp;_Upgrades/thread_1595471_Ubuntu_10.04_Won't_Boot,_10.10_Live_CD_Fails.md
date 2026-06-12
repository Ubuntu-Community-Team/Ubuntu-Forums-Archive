---
title: "Ubuntu 10.04 Won't Boot, 10.10 Live CD Fails"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by imjustsomeguy72 on 2010-10-13
Hi all,

My problem is essentially one problem that developed into another problem, and I'm 99% sure both have the same cause.

Basically, I tried to boot my 10.04 install today, and it failed to boot. Grub works fine (I'm using Legacy), but when it passes it on to the OS, and says 'Starting up', or whatever, my PC clicks and reboots instantly, no errors, nothing. 

Reminds me of a CPU overheating issue, but I'm fairly certain it's not that, **because I can run my Windows install with no observable issues**.

Figuring it was just that installation, I burnt a 10.10 live CD, and tried to boot off that (being fully prepared to format and install 10.10). However, I get EXACTLY the same problem. The CD starts to boot, it comes up with the purple screen with the box, the equals sign and the man in a circle, and then reboots in exactly the same fashion. To reiterate,** this is when using the LIVE CD.**

**I can run an 8.04 Live CD**, but with curious errors. The number keys on the line above the alphabetical keys ALWAYS produce characters rather than numbers, whether caps lock is on or off. There also appears to be mouse oddities as well (selecting whole web pages by merely clicking, etc). This problem does not appear in Windows. Could it be related? I'm sure I've used the CD without problem in the past.

I have not (to my knowledge) updated anything in my 10.04 install since the last time the Ubuntu partition worked (less than 24 hours ago). I distinctly remember NOT running the Update Manager.

I have not tried accessing the Linux partition to check it's intact, mostly because I can't Live CD my way in. I may install an ext driver into Windows to do so. My Windows and Ubuntu 10.04 partitions are on the **same hard drive**, and Grub is what I use to boot into Windows.

The only possible **cause** I could find is, when running Ubuntu in safe mode, it comes up with some interesting messages right after checking the CPU. It says something like "Checking processor #1" or somethin (I can't recall the exact message), and then says Not responding. Occasionally, the 2nd processor will reply with Stuck?, but on the 2 occasions I've done this, it's been different. 

First time in recovery mode, it rebooted, second it just stopped after the processor commands. Could this be the issue? (All four cores on my CPU appear in Windows Device Manager.)

I've tried pulling the CMOS battery, and going back to the default BIOS profile. No cigar.

**Specs** are: Intel Core 2 Quad Q6600 @stock, 4GB ram, EVGA GTX275, Gigabyte P35-DS3p mobo. Windows 7 64-bit, Ubuntu 10.04 32-bit.

And sorry for the long post :) I hope the bolding has helped find the most important bits

Thanks for any help you guys can offer!

---

### Post by imjustsomeguy72 on 2010-10-13
Bump!

Does anyone have any ideas? This is obviously a killer for Ubuntu on my machine, atm, and I would really like to get it working.

PS: I love you all!

---

### Post by imjustsomeguy72 on 2010-10-16
Ok, I fixed the problem. It was because I had legacy USB storage (and possibly also USB mouse support), enabled in the BIOS. I'd had another issue recently where I had to reset the BIOS, and then went in and turned those back on again because I'd though I had them enabled. Clearly, it was not the case.

The problem was an APIC failure on loading, which seems to crash Ubuntu every time. Hence why it affected the Live CD as much as installed versions.

Seems a peculiar thing to crash the system with, though, especially as Windows had no issues. Oh well, can't complain. :)

---

### Post by ReTheOff on 2010-10-16
Interesting.  I have the same issue, only if I disable apic options at the F6 option and have nomodeset checked, I still crash on boot. I will try the legacy USB bios thing though.  Just to note I am trying this with 10.10 amd64.  This system has an nvidia chipset nic and graphics onboard. (zotac board). I had the same issues with 10.04.

---

### Post by ReTheOff on 2010-10-16
Nevermind, it was the add-on wifi card for the Zotac. I couldn't see the code trace on the panic, but when I added "xforcevesa" to the boot line and removed quite and splash, I could see the panic error. "NetworkManager tainted".  I took out the tiny little add-on for the wifi, which I don't use anyway, left APIC on and defaults at boot, it all worked great!

---

