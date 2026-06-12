---
title: "Installing ubuntu on a particular partition"
date: 2005-08-14
forum: Installation &amp; Upgrades
---

### Post by passyspam on 2005-08-14
Helo, im new with ubuntu, im trying to install but i have some doubts... 
i have one hdd and 2 partitions, one where i have win xp, and the other ready for linux (not formatted), when i get to the part of the partitions in the installation menu, what fs do i have to choose for the free partition?, what partition should i choose to install the grub or lilo

i tried to follow the steps in this page [http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html) but, this is not exactly my case because, the partition free for linux doesnt appear like free space (maybe cause it has no format, i dont know).

i thank any help =)

---

### Post by OrchidMix on 2005-08-14
[QUOTE=passyspam]Helo, im new with ubuntu, im trying to install but i have some doubts... 
i have one hdd and 2 partitions, one where i have win xp, and the other ready for linux (not formatted), when i get to the part of the partitions in the installation menu, what fs do i have to choose for the free partition?, what partition should i choose to install the grub or lilo

i tried to follow the steps in this page [http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html) but, this is not exactly my case because, the partition free for linux doesnt appear like free space (maybe cause it has no format, i dont know).

i thank any help =)[/QUOTE]

Hello, Im pretty new with Linux, but I have a good friend, who adviced me, how to do the partititions. He is a student of informatics, so You can trust him. 
The basic rule is, to make a difference between system-programs, that stay what they are and other often changing documents. 
So follow this list: 

5GB: / (there come the ubuntu-programs) 
100MB: /boot (the programs to start Your machine) 
10GB or more: /home (Your personal documents, music-titels, etc...) It is possible to save linux-documents on the windows-partitition, so Your home-partitition does not have to be too great.
2 to 10GB: /var (often and quick changing documents, eg. what You want to print) 
2GB: /temp (same like var, but quicker changing) 
And dont worry about primary or logical: This is only important for old computers, that can only boot from primary partititions. 

I hope this does help You with Your question. Good luck with installing! :)

---

### Post by passyspam on 2005-08-14
i apprecciate your help, but the problem i have is during the installation, how do i specify where to install linux whitout risking the partition with winxp? and at the same time being sure the grub/lilo is installed ok or i'll be  having trouble booting windows

---

### Post by transactionlogfiller on 2005-08-14
If you select "manually partition disk" during the Ubuntu install you should see the Windows partition farmatted with FAT or NTFS, just chose to leave this partition unchanged and format the other one.

Mount the Windows one as something user defined (like "Win" - just make sure you don't select to format it) and mount the other one as "/".

I would recommend grub over lilo unless you have a fondness for lilo, whether you install it on the MBR or in it's own partition doesn't really matter - it will still pick up your windows install as well. The only thing is, if you remove linux at a later date you might have to reactivate your MBR to make windows boot, but it's not hard to do.

Personally. I just have a / and a /home partition for Ubuntu and don't bother with /usr, /var etc.

Edit: format your linux partitions with the EXT3 filesystem.

---

### Post by passyspam on 2005-08-15
thanks i did it like that and it's working ok.

---

