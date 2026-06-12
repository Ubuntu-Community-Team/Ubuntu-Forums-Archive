---
title: "&quot;Upgraded&quot; to Windows 7 and now I can't see GRUB and Lucid"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by shuukazedojo on 2010-05-16
Hello all. I'm at my wit's end with Windows this morning. I upgraded to Lucid a few days ago. Everything went very smoothly. Then I spent the greater part of Friday and Saturday "upgrading" to Windows 7 from Vista. I chose the "update" option which was only supposed to update to 7 rather than overwrite the entire HD. Now, GRUB doesn't load and I don't see my Linux partition. HOWEVER, it appears as though the partitions are still there! When I look in Winbloze at the HDs, it shows the Windoze HD as the partition size I made it when installing Ubuntu. 

Any ideas on how to recover the awesomeness that is Ubuntu from this situation? Or do I need to install it fresh?

BTW, I DID backup my home folder :D. 

THANKS FOR THE HELP!!!!!!!!!!!!!!!!!!

---

### Post by darkod on 2010-05-16
Don't worry, win7 just overwrote grub2 on the MBR. Look here how to reinstall grub1/grub2:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

But be careful. Since you did upgrade to 10.4, it depends whether you need grub1 or grub2. If your previous install was clean install of 9.10, it started shipping with grub2. So you have to use a 9.10 or 10.04 cd and reinstall grub2 as per those instructions.

Of you originally had a clean install of 9.04 or earlier, and then upgrade to 9.10 and later to 10.04, grub1 stays the same unless you specifically upgrade it too.

So use the instructions from that link depending what you are using.

---

### Post by shuukazedojo on 2010-05-16
Perfect! Worked like a charm! 

No more Windoze for this guy. If I need to dual boot anything after this, I'm going to have to try OS X. 

Thank you again for the help. I truly do appreciate it!!!

---

