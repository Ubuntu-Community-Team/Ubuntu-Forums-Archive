---
title: "Installation loops at manually edit partition table"
date: 2006-12-20
forum: Installation &amp; Upgrades
---

### Post by Benchrest on 2006-12-20
I'm trying to install 6.06 on top of 5.10 . I want to keep the same partitions, just install 6.06 in the same space. I select manually edit partition table thinking I can just accept the partitions already defined. From the PREPARE DISK SPACE screen, step 5 of 6 I select MANUALLY EDIT PARTITION TABLE. hit enter. After about 3 minutes I get the screen PREPARE PARTITIONS still step 5 of 6. At the bottom of the screen I get a message warning me of a minimum partition size required for root and swap. Then the harddisk and cd drive whirl and turn off and on and nothing ever happens. Seems tobe in some kind of a loop. Any ideas?

This is an old  laptop, IBM Thinkpad I1460 from 1997. I have to specify acpi-off noapic nolapic to get it to boot. Also used that with 5.10 but i don't think that has anything todo with this problem. Nothing gets altered on the disk as Ubuntu and 98Se still run. I am using the 6.06 live CD I received from Ubuntu some time ago.

---

### Post by budgie9 on 2006-12-20
> **Benchrest said:**
> I'm trying to install 6.06 on top of 5.10 . I want to keep the same partitions, just install 6.06 in the same space. I select manually edit partition table thinking I can just accept the partitions already defined. From the PREPARE DISK SPACE screen, step 5 of 6 I select MANUALLY EDIT PARTITION TABLE. hit enter. After about 3 minutes I get the screen PREPARE PARTITIONS still step 5 of 6. At the bottom of the screen I get a message warning me of a minimum partition size required for root and swap. Then the harddisk and cd drive whirl and turn off and on and nothing ever happens. Seems tobe in some kind of a loop. Any ideas?

This is an old  laptop, IBM Thinkpad I1460 from 1997. I have to specify acpi-off noapic nolapic to get it to boot. Also used that with 5.10 but i don't think that has anything todo with this problem. Nothing gets altered on the disk as Ubuntu and 98Se still run. I am using the 6.06 live CD I received from Ubuntu some time ago.

Are you actually telling the partition program you want to keep the drives as is. I think you need to still set the  root as root  and home as home. If I recall correctly it does not overwrite the files unless you tell it to format again. but the partition program still requires  that info, as to what parttiion is which. I do this but I also back up all the home directory before hand. Perhaps you may find it better to do a fresh install I think I have read this is advised anyway.
Hope this helps.

---

### Post by Benchrest on 2006-12-20
I never get to see the partitions. The partition manager seems to load, but at the point it  should display my partitions it loops, with the harddrive and CD accessing. I am guessing there is something weird with my partitions. I have 5. HDA1 is 2.1 GB for SE98. HDA2 is 5.1GB  windows partition I share with Ubuntu. HDA3 is 8.3GB Root partition. HDA4 is 1GB Swap partition. HDA5 is a duplicate of HDA2. The loop is not inteeruptible.I have to turn off the PC to kill the loop. I have a 6.10 cd I am going to try.

---

### Post by K.Mandla on 2006-12-20
Can you escape out of the installation process, and move forward in the sequence? If you hit escape you should get a list of all the steps in installation. I was thinking you might be able to step over that loop, if it's a problem.

---

### Post by Benchrest on 2006-12-21
Esc did not work either. 

I went ahead and  downloaded a Edgy 6.10 disk and it worked perfectly! There must have been a problem with the 6.06 disk I had. Thanks for your ideas. Closed

---

