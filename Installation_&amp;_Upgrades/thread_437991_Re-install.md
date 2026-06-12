---
title: "Re-install"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by sebroberts on 2007-05-09
Hi, 

After installing Ubuntu a couple of weeks back (Version 6.06) it was working fine and i upgraded straight away to the 7.04, It was working great for about a week and then all of a sudden after i changed the login screen when i went to turn on my PC again it does not go to the login screen and just gets stuck on a black screen with the spinning curser. 

I have searched the forums and could not find an answer that will help me, so i have decided just to start over again. I am trying to re-install 6.06 but when trying to partition my HD (i have windows installed aswell) it says that there is not enough space. 

Now i have both Windows XP and Ubuntu 7.04 on there, but i just want it do over right 7.04 as it does not work!! but how do i go about doing this with out reformating the whole HD that will i presume remove XP. 

Or is there a way that i can fix my original problem?

Thanks in advanced for your help, 

Seb.

---

### Post by loserboy on 2007-05-09
i'm gonna guess it's best to re-install because you arent suppose to upgrade from 6.06 to 7.04,
its suppose to go 6.06 - 6.10 - 7.04

---

### Post by sebroberts on 2007-05-09
Sorry, yes i did go from 6.06 - 6.10 - 7.04 just didnt explain that sorry. 

Ok so if im going to re-install, if i was to click the option 'Erase entire disk' will this whipe my whole HD along with XP, or will it just get rid of Ubuntu 7.04

Thanks for your help,

---

### Post by loserboy on 2007-05-09
depends on how many hard drives you have.
If xp and ubuntu is on hda (or sda) then yea its gonna wipe xp.

---

### Post by bulldog on 2007-05-09
When you reinstall,why don't you download Feisty on fore hand and install the 7.04 instead to upgrade twice?
Can't see any benefit to do it your way.

But back to your question.
When you come to the partition section when you do the reinstall,choose manual partition.
This will show you the available partitions.
Choose to mount / as / and set it to reformat ext3
Choose to mount swap as swap and set it to reformat.
If you have a separate /home mount it as /home **don't format it**
**Don't set your windows or any data partition to reformat**

This should do the trick I suppose,but I really should download a copy of Feisty,and reinstall your ubuntu in one time.

---

### Post by loserboy on 2007-05-09
+1 for fresh install with feisty, the upgrade thing is getting alot better though

---

### Post by jerrylamos on 2007-05-09
For re-install I start Firefox and export the bookmarks then go to home and do a 
sudo cp -au * /dev/sdb1
where sdb1 is my USB drive.  It's actually got a volume label casper-rw so this works too:
sudo cp -au * /media/casper-rw
Then I start a fresh CD Live, install, do manual, then edit the partition I want to use
Set it's mount point to /
Then select format
and continue install.  The home directory can then be re-copied, Firefox bookmarks, etc.

This is a quad boot system so I've done this several times, up levelling, back levelling, etc. etc. to whichever partition I choose without affecting any of the other partitions.  Of course I re-install flashplayer, realplayer, and if it's a Kubuntu, firefox.  (Konqueror doesn't do AOL Mail).  Also /boot/grub/menu.lst is on whichever Ubuntu that was installed last and I prefer to edit that too.  And by the way, if it's a Feisty, I do some workarounds as in my post "Workarounds" on "Installation & Upgrades".

Cheers, Jerry:)

---

