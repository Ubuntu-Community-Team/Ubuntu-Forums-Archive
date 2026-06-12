---
title: "MAJOR FORMATTING problem!"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by mike_302 on 2007-10-13
I used the partition managing thing in the Ubuntu 7.04 to resize my partition and create a new one. The thing is, I resized my XP partition to 25.5GB where as it was using almost 21 GB already!!!! I didn't realize that the percentage that I was selecting was changing the XP partition until it was too late! I thought it was the size of the "New partition" like it said... 

Anyways! XP wont boot anymore. It goes to the screen with the blinking line, then goes blank, and the loading light on my laptop keeps going like its loading (not a solid light, but blinking). Am I doomed!? This is a MAAAJJJOOOR problem for me. I did have an image of the h/d (mind you, from a month or two back) on a portable h/d but if i can get this thing back without doing that, Id much prefer that method.

---

### Post by PmDematagoda on 2007-10-13
Can you access the Windows part using the live CD? And did you defrag the Windows drive before the resizing?

---

### Post by mike_302 on 2007-10-13
using the LINUX live CD? Not sure, how would I go about doing that? Using an XP CD? I'm trying to do something about that right now but... can't seem to get it to boot. maybe im not doing it right. 

I DID defrag it before partitioning, but... only using hte windows defragger. When I analyzed the disk after defragging, it still showed a few small chunks of blue on the right side of the ... line?

---

### Post by Pumalite on 2007-10-13
Boot from XP Installation CD>Hit 'r' for Recovery>FIXMBR>FIXBOOT
If there still is an XP, that will do it.
You can reinstall Grub later if there is an Ubuntu: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
If you want to recover data, boot Live CD, mount partition: [http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
And save your data, reformat and start again.

---

### Post by mike_302 on 2007-10-13
See, I hit r, then it asks for admin password. I'm not sure what it is :s I didnt think I MADE one, but wheni  just leave it blank and hit enter, it cancels
how do i get past that?

---

### Post by Pumalite on 2007-10-13
Just advance to the Recovery option and there enter the commands

---

### Post by mike_302 on 2007-10-13
I cant advacned past the "type admin password part, after hittign r for the recovery console.

---

### Post by Pumalite on 2007-10-13
Don't hit 'r'. Just advance through the installation until you are giving the option to Recover the system installed.

---

### Post by Pumalite on 2007-10-13
[http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console](http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console)

---

### Post by mike_302 on 2007-10-13
So.. When it says "Install on this partition, then, it says do oyu want to install a second OS on this same partition, ... do i jsut keep going thorugh?

---

### Post by Pumalite on 2007-10-13
You better get a good look at the link I gave you.

---

### Post by mike_302 on 2007-10-13
lol, sorry but that link is no help because: I don't have this administrator password. The page specifically has a line: "Enter the administrator password if prompted.

I'm being prompted and I don't know how to answer.

---

### Post by PmDematagoda on 2007-10-13
Now did you let the windows installer start up without pressing r?

---

### Post by mike_302 on 2007-10-13
Lol, which way are we taling about going? One way (the link) explains that, as soon as the XP Setup CD loads, i hit r to start a recovery console, then i enter a password which I don't know.

The way YOU seem to be going is for me to tell the disk to install a second OS on the same (25GB) partition as the other system, and just keep ignoring hte warnings that im making a "bad decision" to install 2 OS's on 1 partition.... im confused.

---

### Post by PmDematagoda on 2007-10-13
No, the Win installer does not do anything except do some detecting and loading until you tell it to install XP, just let the XP installer start and you will be brought to a menu where you can choose your next move.

---

### Post by mike_302 on 2007-10-13
When I put hte XP disc in, I let all the things at the bottom (Setup is loading file .... yadda yada yada..) then 3 otpions come up. One to "Setup XP now" one to repair a windows XP installation and another to Quit setup.

---

### Post by PmDematagoda on 2007-10-13
Try the repair thing.

---

### Post by mike_302 on 2007-10-13
lol, thats what I said I can't get past. Don't know hte password.    And I've gotten to the point in the installation process thing where its scannign my hard drives.

---

