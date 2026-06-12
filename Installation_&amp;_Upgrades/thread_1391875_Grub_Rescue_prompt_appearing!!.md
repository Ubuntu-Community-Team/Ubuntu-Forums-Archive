---
title: "Grub Rescue prompt appearing?!!"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by asn_knight on 2010-01-27
Hey all!
I have a 250 GB HD which is partitioned in to a 65 Gb with Win 7 and the rest in other.
But  couldnt install Ubuntu 9.10 in my comp as whenever i used to shrink the other partition, it used to be recognised as unusable.
Consequently I tried installing Ubuntu into my external 320 Gb HD. I made a 6gb ext4 partition and a 512 mb swap area. The installation was completed subsequently. 
After Installation, I rebooted from the external HD (changing it from BIOS) but there came only a cursor on the left top corner blinking for like 10 min after which i pulled off the USB cable of my ext HD and rebooted.
Now when I start the comp. A screen appeared like this :
Grub loading...
No disk found.
grub rescue>_
and the cursor keeps on blinking like a command prompt.
I tried some commands and searched for some online help but all i got was command not found.
I also came across this article which was similar to mine.( actually all symtoms are same - though the solution didnt work for me)
[http://ubuntuforums.org/showthread.php?t=1326788](http://ubuntuforums.org/showthread.php?t=1326788)
But as the solution explained in steps by the asker (in page 2)
I got command not found each time.
Pls help. I dont want to reinstall Windows but just need to have good old Windows working back again. I'll try and install Ubuntu within it later.
Thanks.

---

### Post by darkod on 2010-01-27
Unplug your external hdd. Boot with the ubuntu cd, Try Ubuntu option, and load the live desktop. In terminal execute:
sudo fdisk -l

to see your disks and partitions. If you have only one internal disk, named /dev/sda, you should be able to restore windows MBR with the following commands in terminal:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore any warnings. Reboot without the cd and see how it goes. Hopefully it will load your windows right away. Don't expect to see grub menu.

---

### Post by asn_knight on 2010-01-27
@darkod
Thanks a ton!!! :D
Comp back to normal again!!!!!

Enjoy
--asn_knight--

---

### Post by darkod on 2010-01-27
Glad it worked. As for shrinking the windows partition, it's better to use win7 Disk Management which has resize tool. Just defrag the partition few times, and use disk management to shrink as much as you want. That should work. After the shrink ALWAYS boot windows few times to make sure it's happy with the shrink and it will probably want to do some disk checks.
DO NOT create any parttion into the newly created unallocated space, especially from within windows (linux doesn't work on ntfs).
Boot with the ubuntu cd, Install Ubuntu, in step 4 tell it to Use Largest Available free space (the unallocated space you created), and job done. At least it should be.

---

### Post by darkod on 2010-01-27
And just to remind you, you still have working ubuntu on the ext hdd that you can use if you want to. The thing is that grub2 went to the MBR of the int hdd and since grub2 config files are on the ext hdd in the ubuntu partition, booting without the ext hdd gives an error about the missing files.
You could just add grub2 to the MBR of the ext hdd and you can always boot with it plugged in and selecting USB to boot before HDD (otherwise windows will boot from int hdd). If you want to know how to do this, just ask.

---

### Post by asn_knight on 2010-01-27
Wow! U read minds!!!
And here I was about to create a new thread for it!!! :D
Thanks I'll try and let u knw.

Enjoy
--asn_knight--

---

### Post by darkod on 2010-01-27
How to reinstall grub2 on MBR of a disk:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Make sure you follow the procedure for 9.10 and you use 9.10 cd, because 9.04 and earlier use grub1, not grub2. You will need your ext hdd plugged in for the procedure.

---

### Post by asn_knight on 2010-01-28
Nope didnt work.
Pls take a look here. I hav explained that prob with more detail.
And Thanks for all the help.

[http://ubuntuforums.org/showthread.php?t=1392453](http://ubuntuforums.org/showthread.php?t=1392453)

Enjoy,
--asn_knight--

---

### Post by AlanRogers on 2010-11-10
@darkod You're a diamond. I have vague recollections of people talking about lilo but I've never used it. You've got me out of the same hole as the OP and it somehow feels very right using old-skool tools to rescue the bleeding edge. A bit like using an old fashioned wooden block plane to smooth wood. Kudos!

---

### Post by windrider42 on 2010-12-24
> **darkod said:**
> Unplug your external hdd. Boot with the ubuntu cd, Try Ubuntu option, and load the live desktop. In terminal execute:
sudo fdisk -l
 
to see your disks and partitions. If you have only one internal disk, named /dev/sda, you should be able to restore windows MBR with the following commands in terminal:
 
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
 
Ignore any warnings. Reboot without the cd and see how it goes. Hopefully it will load your windows right away. Don't expect to see grub menu.
 
 
You Sir are a God!!!  I had the same problem as OP, and tried what you said above.
Worked perfectly for me as well.  :D
 
I had tried all the usual bootrec /fix mbr stuff with Windows 7 and nothing worked, only your fix above. 
Had even tried reinstalling Linux and still could not get the proper Grub Menu
 
Now I should be able to reinstall Linux again... Thank you very much.

---

### Post by xcorpion on 2011-01-06
"darkod"
i just step in
i m having a problem with my hp compaq cq41-208au help me out plz plz
i was using win7 and then i install ubuntu 10.10 via internet.
after installing ubuntu it asks me for update and i accept it buh after it also ask me smthng grub and didnt notice what it says and just click restart
after i got a screen which says 
error : no such device : bed4e5bc-7d2e-486e-a365-14e5de8d236c
grub rescue>

<Note: i have two partitions sda1 sda2 both are HPFS/NTFS
and my win7 is install in sda1 and ubuntu in sda2 and sda1 is boot*

help me out plz

---

### Post by reveldor on 2011-07-01
Solved by consulting "ubuntu documentation>community documentation.burninghowto."  I reinstalled Windows 7, then followed the advice to use a 700mb cd for a new install download instead of the earlier attempts with a 4.7gb rewrite disc. The cd launched immediately, overwriting Windows and giving a first class install of Unbuntu 11.04. :p:p:p

---

