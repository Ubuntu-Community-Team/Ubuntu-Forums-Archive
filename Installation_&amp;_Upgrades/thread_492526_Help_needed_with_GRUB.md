---
title: "Help needed with GRUB"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by deviouskoopa on 2007-07-04
So I had windows XP pro and ubuntu on dual boot, then i just straight-up deleted the ubuntu partition using PartitionMagic (of course i backed up my stuff first). After rebooting, i get a black screen with "Press any key to boot from CD.....GRUB loading stage1.5. GRUB loading, please wait... Error 22" but pressing a key does not work even though i have a windows XP reinstallation disc in cd drive. 

When i boot from CD before it gets to the GRUB screen, the normal Welcome to Setup menu appears but pressing R to bring up the recovery console only brings me to a screen saying "Setup did not find any hard disk drives installed in your computer ............. Setup cannot continue. To quit Setup, press F3".

I have a Gateway tablet with Windows XP, and i'm wondering how to fix this hard drive booting problem. Thanks for any help!

---

### Post by ubuntu.daemon on 2007-07-04
when you deleted your ubuntu you messed up grub, bc grub is usually installed in the same area as ubuntu, so if i am understanding right you still have windows and your trying to boot from cd, if you can get on go enter in the command in the same thing you put regedit into, not dos prompt, but put fixmbr, and that should straighten things out.  Btw why do you have 2 threads?

---

### Post by deviouskoopa on 2007-07-04
well i read somewhere to try that except that when i load the reinstallation cd, it says no hard disk drives are detected and doesnt give me a chance to run the recovery console... is there anything else i should do or do i have to reinstall windows completely?

---

### Post by ubuntu.daemon on 2007-07-04
hmm have you tried making a floppy bootup disk to get into windows??  Did you try to reinstall ubuntu?  bc that will fix grub, then you can go into windows, and do fixmbr then you can use whatever program to delete the ubuntu, but wait, u never said why you deleted ubuntu in the first place.....  did you want ubuntu gone or were you going to do a reinstall?

---

### Post by deviouskoopa on 2007-07-04
I tried to get rid of ubuntu, so that sounds like it should work, reinstalling ubuntu then uninstalling it the right way haha instead of just deleting the partition. i'll see if that works...

---

