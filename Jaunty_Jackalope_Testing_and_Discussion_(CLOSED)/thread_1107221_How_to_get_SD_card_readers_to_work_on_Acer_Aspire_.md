---
title: "How to get SD card readers to work on Acer Aspire One running Jaunty"
date: 2009-03-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by stchman on 2009-03-26
Hello all, I recently installed Jaunty on my AA1.  I must say it runs very well.

I do however want to get the two SD card readers working.  I know it has something to do with the pciehp kernel module.

I have read the community documentation and it seems fuzzy at best on Jaunty.

Has anyone got these card readers working on the AA1 running Jaunty?  It is the final piece of the puzzle.

Thanks.

---

### Post by albinootje on 2009-04-02
> **stchman said:**
>  I do however want to get the two SD card readers working.  I know it has something to do with the pciehp kernel module.

I installed Jaunty Beta on my AAO today, and noticed the same problem.
I'm gonna see whether this helps :
[http://ubuntuforums.org/showpost.php?p=6625550&postcount=193](http://ubuntuforums.org/showpost.php?p=6625550&postcount=193)

---

### Post by albinootje on 2009-04-02
That solution works for me! :)

---

### Post by pjalegria on 2009-04-02
My SD card readers both work, left i have allways SDHC 8gb has HOME, and right works but i have to restart with the SD card inside, no problem for me...

---

### Post by stylishpants on 2009-04-02
What about installing jaunty on an SD card within the AAO, for a dual-boot configuration?  Has anyone successfully done this?

On my AAO, I tried to leave the factory install of linpus in place while installing jaunty on an SD card for a test.

The OS install went OK, but then the boot loader installation failed. I can't boot the newly installed OS.

Next I'll try to manually add the jaunty install info into the linpus grub/menu.lst config.

---

### Post by markbuntu on 2009-04-02
Bootloader installation failure is ususally caused by migration assitant crashing ubiquity before grub can be installed when using manual partitioning. 

The workaround is to run the live cd open a terminal and

ubiquity --no-migration-assistant

The installer will run as usual.

---

