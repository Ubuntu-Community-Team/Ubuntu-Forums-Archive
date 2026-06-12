---
title: "[SOLVED] Can't install Extreme OS, goes to BusyBox..."
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by ntbutler on 2008-08-23
Hi all.

I have just recently bought some newer gear, including a Gigabyte motherboard, 8800GT graphics card etc. I am trying to install the PC user Extreme OS Ubuntu 8.04, and each time, when i tell it to either install straight on to the (empty) HDD or boot (try) first, it shows the PC USER title page with a 'progress' bar, but then it goes to the BusyBox (v1.1.3) built-in shell.
I cannot seem to get any further than this.

Does anyone have any ideas as to how to get this thing booted/installed, and does anyone think that this particular distro is not worth installing (last update i bothered doing was 7.04 i think...)

Thanks :)

---

### Post by livestockPimp on 2008-08-23
what model motherboard is it?
where abouts in the install does it crash, straight after the menu or is it where the partitioner is and you select the drive to install on?

---

### Post by ntbutler on 2008-08-23
Heya. Thanks for fast reply.

The motherboard is a Gigabyte GA-EP45-DS3P.
The installer doesn't actually se3em to reach any stage. Again, i tell it to either install or boot from the CD, and in both cases it next shows a PC USER splash screen, then after about 10-15 seconds it shows the busybox shell...

---

### Post by livestockPimp on 2008-08-23
I think off memory the first terminal is for logs,
use ctrl + alt + f1 and change to the first terminal, once you are here you can see any errors more verbose.

you can also use "shift + pageup" I think to go higher than the screen is showing.

---

### Post by ntbutler on 2008-08-23
Ok. I pressed ctrl+alt+f1 and it took me to a terminal that just said loading, please wait...

The dvd drive has stopped spinning and it doesn't seem to be doing anything.

it seems the busy box terminal is on terminal 8 (ctrl+alt+f8 ), and there is nothing on any other terminals (f2-f7)...

---

### Post by livestockPimp on 2008-08-23
Ok, well from what I can see there is limited support for the p45 chipsets at the moment!

They might be supported in a 2.6.25 or 2.6.26 kernel, maybe have a google on that, but to get it working this way you would need to install on another PC, compile the kernel and then move the drive back across, either that or make a custom install CD with an updated kernel..

---

### Post by ntbutler on 2008-08-23
Ahhh, i see.
damn...

do you have any suggestions for a particular distro that would be compatible (i was only going for extreme os to try it out...)

anyway, thanks for the help.

---

### Post by ntbutler on 2008-08-24
SOLVED!!!
After combing ubuntu forums for the last 2 days I found someone who said that they had problems similar and changed the bios settings for the Sata to be raid. I am not running raid, but it worked, so now i am typing this on my newly installed 8.04 Extreme OS.
Hope this makes things easier for anyone else with siwilar problems.

If you are using a SATA board, try switching the SATA bios settings to raid (just one thing, but helped alot)!

Happy again!

---

