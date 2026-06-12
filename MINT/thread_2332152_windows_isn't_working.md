---
title: "windows isn't working"
date: 2016-07-28
forum: MINT
---

### Post by medalgamer on 2016-07-28
Osprober is installed and has been run multiple times. Grub has been updated (update-grub ... update-grub2), and boot repair tool has been run and also hasn't fixed the problem... The windows files are listed in the file manager, and shown to exist... but grub refuses to allow to boot to windows (windows 10 64 bit)... the partition for windows is on Sda3... and the bootrepair tools mentioned that linux mint is far from the start of the disk and the bios might have trouble detecting it... nothing seems to be working.


It finaly showed in grub after manually adding it and directing it to sda3 (i think)... it would open but would say BOOTMGR is missing press Ctrl + Alt+ del to restart.

---

### Post by QIII on 2016-07-28
Are you running Ubuntu or Mint?

---

### Post by medalgamer on 2016-07-28
mint

---

### Post by QIII on 2016-07-28
OK.  Moved to the MINT sub-forum, as there may be some minor differences that will be better handled here.

---

### Post by medalgamer on 2016-07-28
ok thanks.
so i should just copy and paste what i wrote?

---

### Post by QIII on 2016-07-28
I have already moved your thread to the Mint sub-forum.

---

### Post by medalgamer on 2016-07-28
oh. thnx though you said move not moved. *facepalm*

---

### Post by deadflowr on 2016-07-28
> **medalgamer said:**
> ok thanks.
so i should just copy and paste what i wrote?

What you need to do is re-run boot-repair and at the end of the boot-repair's run it'll show something with paste.com/12345, or something like that.
that's a link to the output of what it did and what it saw and is what will be of real help.

So you need to copy that link down somewhere and then add it to here, so others can see what boot repair did and did not do.

---

### Post by medalgamer on 2016-07-28
so i had a friend do this for me and im not a genius when it comes to doing all this stuff is there a youtube video for it? or something i can simply follow.
he said it was better then windows (which it is) but there are some games i cant play on here that i can on windows.

---

### Post by medalgamer on 2016-07-28
i think this is it? it poped up when it was done 
[http://paste2.org/B6fG0MOp](http://paste2.org/B6fG0MOp)

---

### Post by yancek on 2016-07-28
> it would open but would say BOOTMGR is missing 

That is one of the windows files necessary to boot windows and you cannot repair that with boot repair, Ubuntu or any Linux.
Have you mounted that partition (sda3) to see if the bootmgr file is actually there?  If you mount sda3, it should be in the root of that partition.
Is this a new install of windows 10?  Has it ever booted?  Do you have a copy of a windows installation DVD?

---

### Post by oldfred on 2016-07-28
Grub does not use Boot Flag.
You need to move boot flag (Windows active partition) to sda3 for any Windows repairs to work.

And as Yancek points out you are missing bootmgr & /boot/BCD. They may have been in a separate 100MB partition you deleted. But do not have to be a separate partition.
A full set of Windows repairs should add the missing files, but will also put the Windows boot loader back onto system. Then restore grub.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System

[/URL]
 f8 to get to repair install screen, if you can start to boot
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html) 
      
 Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html) 
    


[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
[/URL]

---

### Post by medalgamer on 2016-07-29
I just thought, I don't know if it would have any effect, but originally it was windows 7 then i upgraded it to windows 10. could have have to do with anything. since it says windows 7 professional and doesn't boot

---

### Post by yancek on 2016-07-29
> but originally it was windows 7 then i upgraded it to windows 10. could  have have to do with anything. since it says windows 7 professional and  doesn't boot 		

The fact that the system is identified as windows 7 after you have updated to 10 is inconsequential and would have nothing to do with the ability to boot.  The problem is related to not having the windows partition marked active and required boot files missing.  You should be able to replace them with the instructions in the link posted by oldfred.

---

