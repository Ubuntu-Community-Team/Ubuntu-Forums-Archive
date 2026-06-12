---
title: "dual boot (probably an easy answer)"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by cessna_89702 on 2007-04-09
Hey I was having trouble with live disks running so I used noaclip or something like that at boot up and it went fine like someone said it would.


Now Im ready for the dual boot with Windows XP and Ubuntu (im not sure which version lol its either 6.10 or 6.06 i didnt label the disk)

This computer should have only Xp installed at the moment. I took a picture of the Partitioner (might be hard to read). 

This is a hundred GB hardrive Im going to let most go to ubuntu. Maybe 60 for Ubuntu and 40 for  XP if that would work good? The pictures are @ the bottom.

1. If I do the first option which resizes automatically and I left it where it is that would make a dual boot with enough room for both and resize wont hurt the windows, right?

2. If I do it manually I need the ntfs and Extended  only right? (I would prefer it done automatically.)

3. Where it says dev/sda5 is that coming from the disk or is that actually on my computer. (this computer has been restored recently so i dont know if its left over or from the disk)

Thanks





[IMG]http://i20.photobucket.com/albums/b214/zach333/LINUx004.jpg[/IMG]
[IMG]http://i20.photobucket.com/albums/b214/zach333/LINUx002.jpg[/IMG]

---

### Post by ffxr on 2007-04-09
that sda5 is a swap partiton, do a custom install, delete that swap   partition & delete that extended partition as well..

so your left with all ntfs & free space.. then resize that ntfs partition to 40gig.. ; & no it wont ruin your xp install, leaving you with about 60gig of space.. then with that free space create a swap partition of 512mb, and then use the rest of the space to create a primary partition of ext3..

ask more questions here if your still struggling to understand what your doing...

---

### Post by cessna_89702 on 2007-04-09
Hey Im creating the swap and I have two choices for it primary or extended. Which one should I choose? If when I create the Extended 3 it asks what would i pick?

thanks for the help

---

### Post by cessna_89702 on 2007-04-09
Oh I see that extended 3 will be primary by reading your post again but I still need some help on the Swap-linux

---

### Post by ffxr on 2007-04-09
there should be an option to make that 512mb swap partition "linux-swap" as apposed to ext3 or ntfs or whatever...

just delete it and create it again if you have to..

---

### Post by cessna_89702 on 2007-04-09
I select as a swap and then it says create as primary or extended while the file type is swap

---

### Post by ffxr on 2007-04-09
oh right, just select primary.. i dont think it matters.. i thought you could select a linuxswap filesystem in that portion of the setup..  it must occur in the next couple of screens in the install routine.. just remember that thats your swap partition when the install asks you to point it out later on..

---

### Post by cessna_89702 on 2007-04-09
Ok but its not resizing my ntfs down to 40 it says an error happened any ideas?

---

### Post by ffxr on 2007-04-09
dear oh dear, what error exactly..? 

do you have access to partition magic or similar tool? it could be an idea to resize the partition in windows,,,

---

### Post by cessna_89702 on 2007-04-09
It just says "error while resizing/moving dev/sda1"

---

### Post by ffxr on 2007-04-09
is there no other partitions on that drive..? i.e you should only have sda1 & free space...until you get it resized, then create the swap...

try that anyway..

---

### Post by cessna_89702 on 2007-04-10
thanks a lot!


I have my ubuntu dual booted with windows and both are running perfectly (except windows is a little bit slower but I will mostly use Ubuntu)

---

