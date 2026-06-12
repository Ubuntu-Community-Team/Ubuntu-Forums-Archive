---
title: "wont boot poroperly after failed install"
date: 2006-02-19
forum: Installation &amp; Upgrades
---

### Post by borisattva on 2006-02-19
i experienced a problem with grub and dualbooting dapper giving me error 21. i followed one of the walkthroughs here and did root (hd0) command to no avail. i reverted to just doing fixmbr and fixboot.

now there is a strange glitch. if i have no bootable floppy or cd i get a message saying boot fail insert bootable media or select a drive to boot from.
if i have any bootable cd and simply choose not to boot from it, it then automatically goes to continue loading windows from the hard drive.
i have checked my bios settings (althought nothing was changed there) and sequence is proper. on fail of floppy go to dvd, and then hd. but it wont go into the hd boot unless there is a bootable. cd. anyone know whats going on?

---

### Post by Robgould on 2006-02-20
You still have an issue with your mbr.  Your disk is bypassing that.  You need to restore your mbr.  I see you already did fixmbr, but I would do it again.

---

### Post by borisattva on 2006-02-22
i tried it again

both fixmbr and fixmbr c:
strangely i get a wraning tha mbr is unrecognized only when i do fixmbr.
with fixmbr c: it acts as if no probelms were encountered.

i also did fixboot c: seemingly succesfull but the probelm persists.

i cant boot unless i have a bootable cd.

please advise

---

### Post by Robgould on 2006-02-22
What version of windows are you running?  And what boot cd are you using?

---

### Post by borisattva on 2006-02-22
i'm booting into xppro, and ANY bootable cd works.

i even tried reinstaling a dual boot with linux hoping gurb wll over write whatever is wrong but it didnt. 

the splash screen prompting for bootable media occurs in the exact instant the floppy is getting chckec. if there is nothing in the floppy or cd rom the message persist. if i have anything bootable in cdrom and i choose not to boot from it (likepress any key to boot from cd in xp) then i get my grub menu and everything works.. but only if i have a bootable cd.

i tried doing fixmbr a: as well to see if something was messed up in the mbr. only other command i did that i remember now was root (hd,0) or something like that when i was following instructions trying to fix grub after a borked dapper install. after that command the problem began

---

### Post by Robgould on 2006-02-22
I don't know why you are doing fixmbr c: or fix mbr a:
 
If you use your winxp install disk, boot to rescue mode.  You will have to choose the windows installation you want to access and give the administrator password.  This will access the system.  From there jsut type
 
fixmbr
 
there should be no options or switches or anything else....just "fixmbr" all by itself. 
 
You should then get an "Are you sure?" prompt.  Say yes.
 
Then it should tell you it was successful and return you to a prompt. 
 
Type "exit" and hit enter
 
This will reboot your computer.
 
Windows should boot normally.
 
If you do not have your winxp install disk, you can use an older dos boot disk, but the command is different.  In this case it is -
 
fdisk /mbr
 
I hope this helps you.  If this is what you are already doing, then forgive me.  But your command in wrong if you are using fixmbr c:

---

### Post by borisattva on 2006-02-22
yes, what youve described is what ive been doing. i tried the device name as an option after the regular format (which merely assumes the devices to be used) did not work,  as per MS document on fixmbr usage decsribed [here]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx").

though still to no avail.

---

### Post by Robgould on 2006-02-23
Sorry, I am all out of suggestions. Did you try using the map command referenced in your link above? Did you try a format like this:
 
**fixmbr \Device\HardDisk0**
 
instead of fixmbr C:
 
If you can't get this solved soon, it might be easier to jsut back up your data and re-insall windows. Then use you linux CD to re-install grub.

---

