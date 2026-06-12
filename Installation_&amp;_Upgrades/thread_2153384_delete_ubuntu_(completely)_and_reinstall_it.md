---
title: "delete ubuntu (completely) and reinstall it?"
date: 2013-06-10
forum: Installation &amp; Upgrades
---

### Post by mreyna16 on 2013-06-10
I was having problems earlier with ubuntu becuase I had installed gnome 3 and did not like it. after uninstalling it, i was having some gnome files still there so i decided to reinstall ubuntu. the way i did it was i created a bootable usb stick (uefi) and when i came across the option to either "install it alongside ubuntu", "delete ubuntu", etc., i used the "something else" option. after i pressed on that option i deleted all partitions and created one big unallocated space and then re did the swap and root partitions. now that i have my ubuntu up and running again, i think i still have some old gnome stuff on here.

so, what is the correct way of COMPLETELY removing ubuntu and reinstalling it so its a fresh copy?

---

### Post by 73ckn797 on 2013-06-10
If you created a separate /home, you can install and save your files. If not and the drive has nothing else on it then you can just choose to let the installer make the decissions. I would recommend chosing the option to designate a separate /home and the date partition / to be created. The data partition doesn't need to be larger than 10Gib max. If this all sounds confusing look here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by mreyna16 on 2013-06-10
i really dont care about home partition because all my files are in a seperate ntfs partition that i use with windows and ubuntu (i dualboot) so correct me if im wrong, the procedure in the first post is right?

---

### Post by Cheesehead on 2013-06-10
> **mreyna16 said:**
>  i think i still have some old gnome stuff on here

Like what?

---

### Post by deadflowr on 2013-06-10
The correct way to  wipe off and reinstall Ubuntu would be,  
do the something else option in the installer
Locate your Ubuntu partition
Select and choose edit or change (forget what it's called)
Select Mount point (The root mount point is /)
Select filesystem ( filesystem ext4 is usual the default)
click on format checkbox
Press Ok or enter or whatever.
Reformatting will clear the partition and start fresh.

But aside note, Ubuntu is Gnome based, so it'll always have gnome packages.

---

### Post by fantab on 2013-06-10
> **mreyna16 said:**
> I was having problems earlier with ubuntu becuase I had installed gnome 3 and did not like it. after uninstalling it, i was having some gnome files still there so i decided to reinstall ubuntu. the way i did it was i created a bootable usb stick (uefi) and when i came across the option to either "install it alongside ubuntu", "delete ubuntu", etc., i used the "something else" option. after i pressed on that option i deleted all partitions and created one big unallocated space and then re did the swap and root partitions. now that i have my ubuntu up and running again, i think i still have some old gnome stuff on here.

so, what is the correct way of COMPLETELY removing ubuntu and reinstalling it so its a fresh copy?

Why do you think you "still have some old gnome stuff"?
If you have deleted the Ubuntu partitions and re-created them then you will NOT have any 'old gnome stuff'. 

However the simpler way would have been to just reformat the Ubuntu partitions, except the SWAP and reinstall. You didn't have to delete the partitions, unless off course you wanted new size and arrangement for partitions.

---

### Post by cincinnatus13 on 2013-06-10
As long as you formatted (and since you deleted the old partitions, you did in essence) then you're fine.
Unity is still based off of Gnome so it will have Gnome packages by default.

Also recommend doing a separate /home partition in the future.

---

