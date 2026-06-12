---
title: "Problem after installing Ubuntu 6.06 LTS"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by mmcdonald11987 on 2007-08-05
Okay, so i'm not a total newbie to Linux, I have used it in the past, but I have never come across this problem before.  I got Ubuntu installed on my laptop, and it's on it's own partition.  I have GRUB up to dual boot XP and Ubuntu.  Now, 9 times out of 10 Ubuntu will not boot up.  It just goes to the loading screen, and then just turns to a black screen when it reaches the end of the loading bar.  That other 1 time out or 10, It will load just fine.  I don't know what I can do to fix this.  If anyone has any ideas, let me know please?

Thanks.

---

### Post by JudasReanimated on 2007-08-06
I had a similar problem and I had it boot into recovery mode, and for some reason that fixed the problem. Not sure how, but you could give it a try.

---

### Post by mmcdonald11987 on 2007-08-06
Thanks for the advice.  I will try that and see if it works.  I'll let ya know.

---

### Post by eapache on 2007-08-06
In grub, select the ubuntu option and press 'e' to edit. Then go the the second line and press 'e' again. Remove 'splash' and 'quiet' and press escape and then 'b'. Ubuntu will now boot without the splash, and you should see what happens to it when it dies.

---

### Post by mmcdonald11987 on 2007-08-06
Okay, Eapache... I did as you said, ran linux without the splash, and when It runs, I get this this error:  

[4294668.033000] Kernal Panic - not syncing: IO-APIC + timer doesn't work!  Boot with apic=debug and send a report. Then try booting with the noapic option.  

I would try this, but I don't know how to boot with apic=debug.  Anyway, i'm frustrated and it's time to go to work.  Hopefully i'll have some answers when I get home.

---

### Post by mmcdonald11987 on 2007-08-06
bump

---

### Post by eapache on 2007-08-07
to boot with apic=debug and noapic, add them to the boot list the same way you removed the splash.

---

### Post by PryGuy on 2007-08-08
Tell us please in which order you've got partitions on the drive? Something like 'Primary NTFS WinXP, Primary EXT3 Ubuntu, Extended NTFS Docs'.

---

