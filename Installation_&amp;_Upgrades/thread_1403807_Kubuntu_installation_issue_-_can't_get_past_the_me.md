---
title: "Kubuntu installation issue - can't get past the menu!?"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by toona on 2010-02-10
Hello all! I am a n00b to Ubuntu, been using it under dual boot with Windoze for about a year, and have found this forum to be a great help - so I am hoping someone can help me out with this "mystery".

I wanted to try out the Kubuntu live CD in order to see if I'd like KDE interface better (I used some SuSE 11.2 lately and liked it). I did whatever I do with Ubuntu (under my Win7 environment) 

- downloaded the iso (x64)
- burned it to a CD usinf imgBurner
- checked the CD - seemed active enough, Windows installer popped up
- rebooted the computer

I got the usual language menu, chose English, got the usual "Try kubuntu without...", "install kubuntu"... menu and hit enter to Try and... nothing!? Every option I clicked responded with "nothing" except F keys, and "Boot from first hard disk".

I tried a bunch of things - burning with CDBurnerXP, using it on another computer, downloading an iso from a different mirror... what is going on? I never encountered this before... Please help?

---

### Post by NightwishFan on 2010-02-10
Always check the CD when you download it, and burn at the slowest possible speed. If the CD is verified as correct, try waiting a few minutes for the kernel to boot after you push enter. If that does not work, reboot, then press the F6 to view options, and check the "Acpi=off" option, then push enter.

---

### Post by dazer26 on 2010-02-10
Maybe try the alternate install cd, there is no livecd and it's a text based installation.  When downloading the iso from the Kubuntu site there is a box at the bottomt o check if you want the alternate install cd.

If you just looking to try it out, you could also try installing it with Wubi, this is done from within windows, just browse the cd.

---

### Post by toona on 2010-02-10
Thanks for the reply!

Sadly, no luck. :( It's not even reading the CD, as if it didn't "catch" the enter key (but it does respond to enter when I hit "boot from first hdd")

 I also tried with safe mode graphics, and I forgot to mention that, if I let the language menu alone and the time runs out, nothing happens, even if it should do the "Try..." by default... :(

---

### Post by toona on 2010-02-11
OK, I solved it - in an awkward way. I downloaded and am using 3buntu to check out kubuntu. 

3buntu is a Croatian compilation containing kubuntu, ubuntu and xubuntu, and is aimed to let people taste different ubuntu flavours before choosing theirs. 

For those interested, the link is  [http://iso.linux.hr/3buntu/3buntu-9.10-desktop-i386.iso ]("http://iso.linux.hr/3buntu/3buntu-9.10-desktop-i386.iso") . Only the main menu is in Croatian, everything else is in English, but you'll easily find your way around the Cro menu as it looks exactly like the standard k/ubuntu menu. (if you need a translation, pm me). 

This works just fine, which makes me think - is everything OK with kubuntu .iso CD?! I can't install this one as 3buntu conatins only x86 versions and I need x64... :(

---

### Post by NightwishFan on 2010-02-11
Perhaps your system is not 64-bit compatible. If it is, then temporarily use the 32-bit system for now. The difference is not great. If you need more than 3gb of RAM then use the PAE kernel.

---

### Post by toona on 2010-02-12
sorry, that's not the issue... it's 100% x64 compatibile, and I'm currently running Win 7 x64 and Ubuntu x64 on it... :(

---

