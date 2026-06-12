---
title: "freeze-up during boot"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by qaanaaq on 2010-01-29
I am new to Ubuntu as of last week. I am assuming that daily lock-ups of my desktop where the mouse pointer moves but will not click are not anything to be concerned with (but i would appreciate a help here as well). The problem To which I seek a solution concerns boot-up. I am running a dual boot with Windows XP.  After the OS selection screen disappears and Ubuntu 9.10.17 begins loading the system is wont to lock up...before the mouse pointer appears. Are these problems related? Does this mean I need to reinstall grub? And how do I do that? I this I can master Ubuntu, but I need some help for this.

THanks.

---

### Post by oldfred on 2010-01-30
It is having a problem somewhere. Did you let it run for a while as sometimes it will finally get thru it.

You can try manually editing the boot line in grub2 to remove the quiet and splash commands so it will output every line as it boots. Where it stops or gives a error message - post back with error.

Instructions on manually editing grub boot:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

---

### Post by qaanaaq on 2010-01-31
Thank you.  I did edit GRUB2 as you suggested. It hasn't acted up again. I will post the error when it does. For now, it might be relevant that the floppy drive light often stays on when it freezes.

---

### Post by qaanaaq on 2010-02-03
The final line prior to freeze-up (at least once) is/was 

dev/sda5: clean 172186/945553568 files 5328911/37800937 blocks.

---

### Post by oldfred on 2010-02-03
That sounds like it was doing a filecheck. With ext4 it is very quick or runs in the background With 9.04 I would get after every 30 boots a file check and it would tell me and show the progress.

---

### Post by qaanaaq on 2010-02-06
It's happened exactly once in the past week (as opposed to perhaps 3x per boot)  so maybe some irregularity in the file structure solved itself. Thanks for your help. Any ideas on the non-response of the mouse when i'm in a program? The clock even freezes!

---

### Post by oldfred on 2010-02-07
I had a runaway process or combination with 9.04 I think, something was indexing files and gave a error message and that version of nvidia had issues, I never knew which it was for sure. You can go into terminal and run top which lists the processes and see what is consuming resources. I added system monitor applet to the the very top panel so I can track cpu use and know if it is running at 100%.

---

