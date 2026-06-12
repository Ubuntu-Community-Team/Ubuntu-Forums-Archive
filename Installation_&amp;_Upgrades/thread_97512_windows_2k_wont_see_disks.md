---
title: "windows 2k wont see disks"
date: 2005-12-01
forum: Installation &amp; Upgrades
---

### Post by jockjunior on 2005-12-01
Hi gang,
got my cd's yesterday and installed Ubuntu to a second empty drive with 10gig , 6gig and 2gig partions (approx figures) installed ubuntu to 10 gig and swap to 2gig and left 6gig as fat32. used partion manager to set root and swap  and then installed ubuntu. Grub menu comes up on reboot and Ubuntu boots OK and runs OK. but windows loads very slowly then throws up check disc message then continues if I press enter takes forever to load then cant see drives in my computer then freezes.

What have I done wrong? I got back to windows by using fdisk to delete partions and fdisk/mbr to repair boot record so I am back to win 2K

thanks for any help

Jock

edit  win 2k on 5gig drive formatted ntfs ( I dont have a lot of progs on it )

---

### Post by akiro.yamamoto on 2005-12-01
win2k is just looking for the drives and not finding them.... 
Use win2k system administration tools and delete the partition your going to install ubuntu to... JUST DELETE THE PARTITION, DO NOT FORMAT IT!!
When done reboot back into win2k (just to make sure there are no problems) ..
Then restart and re-install ubuntu...
Hope that helps....

---

### Post by bwog on 2005-12-01
You didnt do anything wrong, but windows needs a lot of space to operate comfortable. Do not use windows progs to partition, use the ubuntu install disk. In my opinion you dont need a fat 32 partition, use explore2fs to read ext3 from windows.

Tell us, if this doesnt answer your question.

---

### Post by jockjunior on 2005-12-01
Thanks guys
will try that and fingers crossed

jock:smile:

---

### Post by akiro.yamamoto on 2005-12-01
True....but win2k has a problem with dealing with dynamic changes to the disc management system...
That's why it's better to create the space with win2k and then format with linux...
Of course if you've got something like partition magic....well :smile:
It's also possible that win2k has created a swap file on the partition you want to use for ubuntu... check that as well..
Hope this info helps you..

---

### Post by jockjunior on 2005-12-01
Hi guys,
 back again . Win 2k on 5gig with 480-960meg paging file on same disk. approx 2gig free space left.

Ubuntu on 2nd HD formatted ext3 and running ( using it now)
Win 2k now booting but still seems slower than before installing Ubuntu. Only disk C:
and cdrom and cd/rw show up in my computer. 2K seems to be running OK once booted up.  

Thanks for the help  ( I may be back );)

---

