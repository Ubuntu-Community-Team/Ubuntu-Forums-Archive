---
title: "Does windows 7 install remove my multi boot?"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by Syncan on 2010-03-31
I plan to clean install Windows 7 on my system ( currently windows XP ).
At  the moment I have Windows XP professional together with Linux Ubuntu  and I want to keep using Ubuntu.
When I do the clean install for  Windows 7 Professional, does it leave the multi-bootloader in place?
If not, what should  I do to bring the multiboot-loader back?
I have a CD of Ubuntu 9.10.2.6.31.14. My installed Ubuntu is version 9.10.2.6.31.18.

---

### Post by sxmaxchine on 2010-03-31
i think if you install win7 into the xp partition you should still be able to use ubuntu however it might remove the grub bootloader and replace it with the microsoft version. not to sure this correct as i have never installed 7 and also have always installed windows before ubuntu.

---

### Post by Random_Dude on 2010-03-31
I did something similar (remove Vista and install 7) and Grub disappeared without being replaced for other bootloader.
There is a way of bringing Grub back on, but I was too lazy so I just installed Ubuntu again.:biggrin:

---

### Post by Syncan on 2010-03-31
Thanks both of you for the quick response :)
I have done a lot of work to install all things in linux that I wanted  and it would be a shame if I loose all of it again. I will not gamble with it, so I think it's a better idea to wait if somebody else knows how to bring back grub after installing.

---

### Post by oldfred on 2010-03-31
Windows will only overwrite the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you install to a new partition it will combine its boot with XP, then when you delete XP it will also delete win7 boot files. So be sure to install to the XP partition. It should not even see the linux partitions. Only wubi users would also lose the Ubuntu install. 

Of course with any system changes, you should have good backups of important information.

---

### Post by Syncan on 2010-03-31
Thank you. Yes I will clean install Windows 7 in place of my current Windows XP.
If I understand it correctly, after installing Windows 7, my bootloader will be gone and then I should boot from my Ubuntu disk and do what that article says:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Is that correct? Sorry, I am not very skillful in Linux... :)

---

### Post by oldfred on 2010-03-31
Yes, If you did a clean install of Karmic be sure to follow the instructions for grub2.
If you have an upgrade then you have grub legacy (0.97) and follow those directions.

---

