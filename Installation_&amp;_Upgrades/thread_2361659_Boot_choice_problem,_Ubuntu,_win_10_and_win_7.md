---
title: "Boot choice problem, Ubuntu, win 10 and win 7"
date: 2017-05-19
forum: Installation &amp; Upgrades
---

### Post by Vic_Paine on 2017-05-19
Not really a Ubuntu problem but started of with win 10, added win 7 (have some software that won't run on 10) then added 16.04.  Al three running fine initially but now if I choose win I only get 10, the win boot choice doesn't show any more so I can't run 7.  Any ideas please?

---

### Post by yancek on 2017-05-19
I would suggest that you boot Ubuntu and go to the link below.  From there download the boot repair software to Ubuntu and run it per instructions on the page and make sure you select the Create BootInfo Summary option and do not try any repairs.  When it finishes, you should have a link to the output which you can post here and someone should be able to advise.

If your windows 10 was pre-installed, it was probably uefi and if you had no problems dual booting 10 with Ubuntu, they were probably both uefi.  A default install of windows 7 will not be uefi so that 'may' be the problem.  Posting the boot repair output should allow someone to verify that.

---

### Post by Vic_Paine on 2017-05-20
Thank you for reply, my PC is a home build that uses BIOS not UEFI.  Strangely I found a workround whilst reading about UEFI.  You can access this by holding down shift and clicking restart.  I tried this forgetting that I had BIOS but it came up with the screen which had the choice of restart into win7.  It actually worked after the Grub screen even though it said Win 10 on the menu.  A long winded process but as I only ocassionally use 7 it's bearable.

Addition.
Since I did that if I choose Win from the Grub menu I now get the MS choice menu every time, result.

---

### Post by Vic_Paine on 2017-06-01
The addition in last post only works once, second time win is booted there is no win boot menu.  However I had another (apparently) unrelated problem in that I couldn't read a separate win data partition in Ubuntu.  In another thread here ```
https://ubuntuforums.org/showthread.php?t=2362087
``` I discovered via Kagashe that Win 10 doesn't actually shut down, it hibernates.  If Win 10 is shut down in a command prompt with ```
Shutdown /s /t 0
``` then you always get the Win boot menu if Win is chosen AND you can read a win data disk in Ubuntu.  Win 10 shuts down faster with this command but takes twice as long to  load, small price to pay.

---

### Post by oldfred on 2017-06-01
If both Windows are in primary partitions, you can copy Windows boot files & move boot flag & run repairs to make second partition bootable.
Whichever primary NTFS partition that has boot flag is the Windows boot partition. But grub searches for boot files, not boot flag, so then grub can find both Windows to add to menu.

        [http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products](http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products)
louieb's suggestion:
Just a note about dual booting 2 MS products. When you install the 2nd one - the installer will put its boot loader in the partition with the boot flag on (usually the partition holding the 1st MS product). And the 2nd product can only be booted thru the boot loader in the 1st product. 
   To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/](http://www.multibooters.com/)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)

---

### Post by Vic_Paine on 2017-06-01
Thank you oldfred, some good info there, don't think I'll change it at the moment as would need to reload Win 7.  I'll certainly keep the links in case I have to reload things again.

---

