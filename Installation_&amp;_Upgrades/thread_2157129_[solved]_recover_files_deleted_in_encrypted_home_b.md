---
title: "[solved] recover files deleted in encrypted home before a failed upgrade"
date: 2013-06-24
forum: Installation &amp; Upgrades
---

### Post by turbo weasel on 2013-06-24
this question is asked on another board but i havent had much luck with a response so i will ask here aswell.
feel free to ask me more info if i have missed anything.


[COLOR=#333333][FONT=UbuntuRegular]Im going to give you real breakdown of events to clarify what has happened.
Ive just rebuilt a rig i havent used for almost a year, its running windows7 and ubuntu 10.40. I couldnt remember the login for windows so was recovering files in ubuntu and prepairing to wipe windows 7, i recovered some files and deleted some files.
I got a popup syaing ubuntu is ancient and needs upgrading as its not supported so i clicked upgrade via update manager, it did its thing and started to download the files. this was unsuccessful at the install stage, it was stuck for hours so it got shutdown at 3am. next day i boot up and it says on start screen ubuntu 11.10 with the little dots but doesnt boot, i tried previous linux versions in grub with same result.
To make matters worse i remember my windows login and boot it up to be confronted with a temporary profile as some of the files removed/deleted are needed for the profile.
im using a live usb of 12.04 lts and have used ecryptfs-recover-private and have access to the encrypted home folder from 10.40 but i cannot find these deleted files, ive checked in user/.local/share/trash and the three folders are empty. so i may have emptied the trash bin, i cannot remember,but i know there are techniques to recover it still.
so after all this, i would like to a; recover my 10.40 lost in limbo edition of ubuntu or b; recover the lost data, copy and save all the important files from /home and fresh install 12.40
sorry that was so long :D


[/FONT][/COLOR]

---

### Post by TheFu on 2013-06-24
Sorry, but I don't have any good news for you.  If the files where stored on an encrypted partition, they are basically gone since file recovery tools work at a low level.  The difficulty in recovery is beyond most peoples' skills. If you really need the data, you can probably find a data recovery company and pay them $3,000-$10,000 to recover most of it.

If the files where not located on encrypted partitions, it is still a huge pain to recover them using the **testrec **tool.  It is much easier to just restore from the backup you made and start over, being more cautious and NOT doing any system-wide updates until all the data is moved over.  Last time I used testrec, the recovered file names were all jumbled. Looking through 2,000 files trying to figure out the name isn't fun.

Backups are much easier to restore than trying to recover deleted files.  I'm just sayin'.  I got backup religion after losing 80% of my data because I was stupid and didn't think it could happen to me. Hopefully, this is the time you also learn that lesson.

---

### Post by turbo weasel on 2013-06-25
Thanks for the reply TheFu,
I dont know how but i have fixed it.
I can only assume that i didnt delete these items from the trash. After i decrypted home to temp on a live cd i copied the entire folder to a seperate hdd.
Installed a fresh 12.04 and then copied the folder with my decrypted to desktop. i found i couldnt unmount the hdd and then noticed that the trash was full, opened it and found all the items i had deleted from windows 7, copied those back to the root of that drive rebooted amd hey presto windows works again (albeit after a few restarts and 10 million updates)

todays lesson, back everything up. 1 hdd for linux,1 data and 1 for back ups
Thanks for taking the time to read that and respond, ive been very lucky this time and hope others can learn from this.

BACKUP!

---

