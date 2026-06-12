---
title: "Omnibook XE2"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by Agent9 on 2009-11-23
Hello. My first post here but not my first time working with a Linux distro. Played around with DSL a while back and installed Ubuntu on a Virtual PC image.

I'm going to attempt to resurrect my ancient XE2 from the closet and wanted to use it as a simple web browsing computer. It currently has Windows 2000 Pro installed, 256megs or memory, no built in ethernet or wireless (requires PCMCIA cards for this function). I wanted to get some feedback from people who are familiar with installing XUbuntu on this laptop.

I've downloaded the ISO and plan to burn it to a CD and launch the CD from the laptop. Once launched I plan to install the OS and from there I want to install the drivers for the wireless and ethernet PCMCIA cards. Does that sound about right? Is that all that is required? Any feedback would be much appreciated.

---

### Post by kerry_s on 2009-11-23
full specs please.

> I've downloaded the ISO and plan to burn it to a CD and launch the CD from the laptop. Once launched I plan to install the OS and from there I want to install the drivers for the wireless and ethernet PCMCIA cards. Does that sound about right? Is that all that is required? Any feedback would be much appreciated.

yeap, thats how you do it.
do they need drivers? did you check if they work out of the box? most do.

---

### Post by Agent9 on 2009-11-23
> **kerry_s said:**
> full specs please.

yeap, thats how you do it.
do they need drivers? did you check if they work out of the box? most do.

I'm not at home right now. I'll get you the full specs when I get back. Are you looking for the processor, hard drive, graphics card, and screen size? Anything else?

It's been a while since I installed Win2k on that laptop so I'm not certain if the cards work right out of the box.

---

### Post by kerry_s on 2009-11-23
> **Agent9 said:**
> I'm not at home right now. I'll get you the full specs when I get back. Are you looking for the processor, hard drive, graphics card, and screen size? Anything else?

It's been a while since I installed Win2k on that laptop so I'm not certain if the cards work right out of the box.

processor & graphics card are the other main parts that would effect your performance. 
i think i use to have 1 of those(Omnibook XE2) it had i think 500mhz cpu.

in any case you might want to give straight debian a try, it runs better on the old stuff, every 1 else is optimizing for good hardware. 
i have a 450mhz 256mb ram laptop running lenny gnome with no problems. gnome is easy to tweak for performance.

---

### Post by Agent9 on 2009-11-23
> **kerry_s said:**
> i have a 450mhz 256mb ram laptop running lenny gnome with no problems. gnome is easy to tweak for performance.
Okay, please don't laugh, but does gnome require a DVD to install? My laptop is so old that Jesus carried it around with him. Only a CD player and floppy drive and no option to boot from the USB port.

EDIT: Oops. Just found out you meant Gnome distribution of Debian Lenny. Man, this is getting confusing. Is Debian KDE the same thing as Lenny Gnome or is it a totally different distro?

---

### Post by Agent9 on 2009-11-24
> **kerry_s said:**
> processor & graphics card are the other main parts that would effect your performance. 
i think i use to have 1 of those(Omnibook XE2) it had i think 500mhz cpu.

in any case you might want to give straight debian a try, it runs better on the old stuff, every 1 else is optimizing for good hardware. 
i have a 450mhz 256mb ram laptop running lenny gnome with no problems. gnome is easy to tweak for performance.

Processor: P3 450mHz
Video: Silicon Motion Lynx EM 4MB

I tried installing Debian 5.03 NetInstall from a CD but couldn't get past the install menu. After selecting Graphical Install it starts the install process then goes to a black screen and does nothing. After 20 mins I forced a shutdown. I tried removing quiet and adding the following options:** noapic nolapic noreplace-paravirt**. Still nothing. Have you heard of this problem?

---

### Post by kerry_s on 2009-11-24
nope.

don't use the graphical installer, that uses to much memory, you need as much memory as you got for the install. the text installer is not pretty, but it is just as easy.

---

### Post by chumkila on 2009-11-24
I recently dusted off and installed Xubuntu on an old Toshiba Portege P3 600Mhz with 128Mb RAM and it works a treat. Didn't think it would ever be used again! When installing using the standard .iso i experienced a system freeze and black screen so I reverted to the alternate .iso which flew threw the procedure.

---

### Post by Agent9 on 2009-11-24
I tried installing Xubuntu just now and the installation went fine. After the install I was able to get to the desktop and surf the Internet. I then rebooted and after the mouse sign I get a black screen with a cursor. I can move the cursor around and the power messages show up on the top right hand corner but that's it. If I press cntrl alt backspace I get the change user screen. If I press change usuer the background comes back on and the login screen shows up. If I press cancel or log in with my account it goes back to the black screen with the cursor. It seems like the monitor settings for my login are screwed up or something. Is there an administrator account I can use to fix this? Once I log in with administrator where would I check on my account settings? Thanks.

---

