---
title: "[SOLVED] cold boot fail ubuntu studio 8.04"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by Eric06 on 2008-05-20
Hello, I have installed unbuntu studio on my acer machine (i wiped our the vista image)
Since the install i have a bizzare boot behavior, as I am not a grub expert, i need help finding out what is wrong.

machine config: 2 hdd (one has linux+swap, the other is for data/backups) The machine is an ACER aspire 5610 (dual core quad intel) with 2 giga. no dual boot on vista, i asked the install cd to remove all windows partitions on the drive 0

problem description: when i power on (cold boot), after the Grub timer (to allow entering the menu) the screen is cleared, there is a starting message ('Starting up...'), then nothing happen at all (I tried waiting for 10minutes). If from there i reboot the machine (by holding the power on psysical switch for 20 seconds) the machine reboots and it passes the starting message, loads linux and everything is fine after this (ubuntu works perfect). in summary my machine will not cold boot, but will warm boot, the problem is solid

what i tryed so far:
1) reinstall grub from a root console: no change
2) remove second hdd: no change
3) check the disk with tools like ctrlpart...: no change, no error log
4) scanned the systems messages for errors : no message showing any error

On june 23rd after the latest ubuntu updates download from the internet the systems now boots OK: this was probably a kernel issue at boot statup
I am glad this is gone, but I cannot tell if this is fixed forever.

---

### Post by jtrindle on 2008-05-20
I wonder, if you do a down arrow/up arrow (to stop the grub countdown timer and re-select your default kernel), then wait 30 seconds, and  press enter... would the system boot?

If so, it means one of your drives is taking a little longer to spin up, and you could just increase your grub timeout in an attempt to allow it to catch up.

---

### Post by Eric06 on 2008-05-21
as Grub is running out of the disk, there was a very little possibility to get a change by waiting. Nevertheless I tryed: no change
There must be a difference between a cold and a war start that gets my grub hanging at 'Starting up....'http://ubuntuforums.org/images/smilies/confused.gif
Help wellcome to point me in the right direction (i searched grub manual, ubuntu forum witout luck)

---

