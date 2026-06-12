---
title: "Installed 7.04, windows no longer bootable"
date: 2007-10-09
forum: Installation &amp; Upgrades
---

### Post by travm on 2007-10-09
I am alittle experienced with linux, and very much so with windows.  
First shot at dual booting.
I used partition logic to resize my hdd, (probably a mistake) which took about 5hrs.
then I foolishly didnt test it to see if the resize worked non-catastrophically.  Xubuntu alternative install worked fine, aside from not detecting windows and putting an entry into grub.
As it sits now i have a partition NTFS with winxp on it, a partition ext2 for swap, and a partition ext3 for xubuntu.  I havnt tried using super grub disk to boot windows but will try that next.  
Supposing it works do i just edit grub to point it towards my windows partition (hd0,0)?  Ive read several posts like this but they dont seem to quite be the same deal as what ive got.  Also I never got a choice to put grub anywhere else other than the mbr,  seems that doesnt work anyway.

---

### Post by jnorthr on 2007-10-09
So what happens when you reboot ? Do you see a grub menu showing your available operating systems ?

---

### Post by travm on 2007-10-09
yah sorry,  It shows the normal (I only installed Ubuntu) options, there are 3, i cant remember what they all are, one is ubuntu, one is ubuntu (recovery console?), and the 3rd one is something else.  either way, none of them are windows xp.  Basically grub is doing just fine, but it didnt detect windows xp when I installed.

---

### Post by jnorthr on 2007-10-09
then it can only be because there is no windows partition there or that partition on hd0,0 no longer has a valid format, i.e., it's been lost. Hope you have a backup.

Perhaps we can look at this a different way. Do you have a windows recovery diskette or CD that might let you reboot into the ntfs partition ?

Or:
if you can start ubuntu, in the System menu option, it may show you all the partitions with valid file system formats on it. You just might be able to see if your ntfs file system shows up there.

---

### Post by travm on 2007-10-09
well, it basically was a clean install.  i backed up like 3mb of files.  If all is lost then oh well.  In fact if i could get my wireless usb working i would abandon windows completely.  but im struggling there, anyway thats another post.
Partition Logic shows it as a valid NTFS partition.  Possibly I did something inadvertantly to remove the primary flag.  I will have a look at this stuff as soon as i get home.
From what i understand if i go and re-install windows, it will overwrite grub in my mbr, not ideal.  Should i do this?  or should i just start bugging people to help me get my wireless USB adapter working?

oh and ubuntu works fine...  I didnt set up my network during install, so i did some of it manually, but i cant get it to turn my usb wifi adapter on. the manufacturer claims unofficial linux support, however the drivers arent on their website like they said they were.

---

### Post by travm on 2007-10-09
ok, so i figured out how to turn on my wireless card, now
how about trying to save my data, 
Super Grub Disk will not boot windows.
file manager (xubuntu) shows the 10gb volume, with 3.5gb free space 6.5 gb used.
partition logic shows it as an NTFS filesystem,  
ubuntu shows nothing, aside from the fact that it clearly has something on there.
I would use my windows cd to try to rescue it, but i really dont want to break ubuntu for the sake of saving windows.
What can I do?

---

