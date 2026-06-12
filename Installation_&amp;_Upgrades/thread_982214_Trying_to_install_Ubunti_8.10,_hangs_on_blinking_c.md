---
title: "Trying to install Ubunti 8.10, hangs on blinking cursor"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by siaco on 2008-11-14
Hi,

I'm currently trying to install Ubuntu server 8.10 on my old Pentium 3 computer. Main board is Abit BE6 with HPT 366 ATA 66 disk controller. I'm trying to boot the installer CD, but it hangs after the first boot menu where you can add extra boot options by pressing F6 etc. When I'm pressing install in this menu, I get a blank screen with a blinking cursor, and thats it.

I belive the problem is the ATA controller. So far I have managed to get somewhere by doing this:
[LIST]
[*] If I unplug my hard drive from the ATA66 controller, the system boots. But, as I *do* want my ATA66 to work (and doesnt have any ATA33 cables which fits atm (the ATA66/100 cable which I do have is "missing" one hole)).
[*] If I pass the boot param pci=off (as found in [http://ph.ubuntuforums.com/showthread.php?t=891220]("http://ph.ubuntuforums.com/showthread.php?t=891220")), the system boots too, but now (not surprisingly) it doesn't find my CD-rom etc.
[/LIST]

The thread which I linked to is indeed solved, but without stating exactly how it was solved, so I was hoping that anyone could please help me :-)

---

### Post by siaco on 2008-11-15
No one can help me with this problem? :-(

---

### Post by asenine on 2008-11-15
IIRC, you can do this with gparted. I'm a newb though, and since others haven't answered I assume that it is harder than I am thinking it is.

That said, sometimes the most obvious answer is the right one.

---

### Post by Guitar John on 2008-11-15
> I would suggest trying some more boot options like:
[LIST]
[*]idle=poll
[*]acpi=force irqpoll
[*]pci=off
[/LIST]


What he is saying - as I understand it - is to press F6 at the 1st screen in the live cd.  Then type one of these options at the end of the line that appears at the bottom of your screen.  If that does not work, you re-boot and try the next one and hopefully, one of them works for you.  

It can be a little frustrating finding the one that works and sometimes - [as is the case with me]("http://ubuntuforums.org/showthread.php?t=982291") - you find out that you have a hardware problem.

I feel your pain.  I'm not nearly an expert, but I will do what I can to help.

---

### Post by siaco on 2008-11-15
Thanks for answering! :-)

I did try F6 -> add option: *pci=off*, which did indeed get me a step in the right direction. But now, on the next step on the installation, I got an error message telling me it didn't find the CD-ROM (which I just booted on). All other options given in the forum post I linked to got me nowhere.

I do not think that I have a hardware problem as I have managed to set up Gentoo on the same computer and ran that for a couple of years now (updating it regularly and running the latest kernels.) I did want to install Ubuntu on it now, as that is what I'm using on my desktop computer. It seems to me to be harder to get Ubuntu up and running on this computer, than getting Gentoo to work :p (Even though gentoo was my first encounter with Linux hehe)

---

### Post by Guitar John on 2008-11-16
My tower computer - the one giving me grief - has a CD drive and a DVD drive.  For some reason, I can boot the live CD from the DVD drive but not the CD drive. 

If you have both, perhaps if you try the other drive.

---

