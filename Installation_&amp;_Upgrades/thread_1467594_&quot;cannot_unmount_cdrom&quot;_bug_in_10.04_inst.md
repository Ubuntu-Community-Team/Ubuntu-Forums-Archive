---
title: "&quot;cannot unmount /cdrom&quot; bug in 10.04 installer!"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by zsero on 2010-04-30
I tried installing 10.04 from hard drive, just as before, but I couldn't install it from hard drive! 

1. I copied the official 32-bit iso to a FAT32 partition with Lili BootCD  creator (used it many times before). 
2. Install/liveCD starts, wizard works  well, but when the install actually starts, in about 5 seconds i get an error  of
"**cannot unmount /cdrom**" > click OK.
3. I did not use or want to use the cdrom at all.
4. Clicking OK takes back to Step 6! Another try to install, but now it goes back to step 6 without any warning or error!
5. Step 7, Step 8, Finish> again Step 6!
6. Infinite loop to Step 6!

I have never seen anything like this before!

BTW, is it a known bug that when I click advanced before start, it defaults to "sda" for the bootmanager location, even if in the wizard I selected "sdc"? I mean it says advanced, but even then it's just so easy to destroy a multiboot scenario.

---

