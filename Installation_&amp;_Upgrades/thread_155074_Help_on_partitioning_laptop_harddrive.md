---
title: "Help on partitioning laptop harddrive"
date: 2006-04-04
forum: Installation &amp; Upgrades
---

### Post by massivevoid on 2006-04-04
I'm trying to install Ubuntu 5.10 on my HP Pavilion dv5000 laptop (with Windows XP) and I ran into a problem I don't understand.

IDEI master (hda) - 80.0 GB FUJITSU MHV2080AH
        #1 primary   79.8 GB  ntfs   /media/hda1
             pri/log    222.1 MB      FREE SPACE

What I don't get is why is there 222MB of free space?

Also, when I try to partition the #1 primary, it doesn't change anything.

---

### Post by massivevoid on 2006-04-04
What should I do?

---

### Post by RRS on 2006-04-05
I've used [this guide]("http://users.bigpond.net.au/hermanzone/index.htm") for 2 succesfull dual boot installations and have since noted it's highly recommended thruout the forums here.

The site also has several helpfull post-installation tips.

Welcome to the world of Ubuntu :)

---

### Post by massivevoid on 2006-04-05
The "pri/log 222.1 MB FREE SPACE"... I cannot delete. 

The "#1 primary 79.8 GB ntfs /media/hda1"... I cannot configure a partition from it.

I have no clue what to do. The only option I can thing of is to erase the drive, but I don't want to get rid of Windows XP Media Center.

When I go into "Disk Management" in Windows, it shows C: 74.32 GB NTFS (blue line) and the 212 MB Unallocated (black line).

---

### Post by towsonu2003 on 2006-04-05
check out this one: [https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo) -- Also see the section titled "Issues with Windows XP and NTFS". 

Before resizing, boot Windows in safe mode and do defragmentation twice. The end result will show you a graphic. the amount of white space at the end of that graphic thing is the amount of ntfs you can resize/shrink. but don't forget to spare some free space for windows... 

Don't worry about that 222MB free space. you will be incorporating that into either ubuntu's root partition (/), /home, or swap during partitioning. 

**very important: make a backup of your files and make sure the back up is working.**

---

### Post by massivevoid on 2006-04-05
Ok, I'll give it a go. Thanks. :)

---

### Post by massivevoid on 2006-04-05
When I ran qtparted and try to resize the partition, it gave me:

"Filesystem check failed! Totally 1 cluster accounting mismatches." :confused:

---

### Post by towsonu2003 on 2006-04-05
[QUOTE=massivevoid]When I ran qtparted and try to resize the partition, it gave me:

"Filesystem check failed! Totally 1 cluster accounting mismatches." :confused:[/QUOTE]
go back to windows and do a filesystem check there. I think you right click on the drive and click on tools. wow I don't really remember it anymore... anyway. it will ask you to reboot. do so. when reboots and checks the filesystem, reboot again and use **safe mode** this time (google on how to do that, I really don't remember). In safe mode, do defragmentation (under tools again) twice and than reboot and resize. 

**important note:**before filesystem check, make a back up. Once, I did a filesystem check in Windows (2 years ago) and it borked itself totally. All data lost, but I had some backup.

---

### Post by massivevoid on 2006-04-05
Sorry for the long wait. I have everything up and running. Thanks for the help! :D 

Now the next thing on my "to-do" list is to fix the Broadcom wireless adapter.

---

### Post by n0ah420 on 2006-04-06
Its too bad I am just seeing this thread.  That partition is for the DVD quick boot feature that lasptop *used  *to have.  Its a small 200MB partition that allows the laptop to play DVD's/cd's without booting into a *real OS.   *It was accessed by pressing the dvd button on the top of your keyboard.  I am triple booting a smimiliar laptop with Dapper32/winxp/win64.

---

