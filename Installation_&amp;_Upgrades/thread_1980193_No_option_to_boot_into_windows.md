---
title: "No option to boot into windows"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by Tuna_Can on 2012-05-14
64bit, gnome BT5, windows 7

I installed a dual boot of Backtrack 5, but when I start my computer there wasn't even a grub menu or any menu. So there was no way to boot into windows. I tried BootRepair so now I have a grub menu but still no option to boot windows. The windows partition is still there with its files.

[http://paste.ubuntu.com/987990/](http://paste.ubuntu.com/987990/)

---

### Post by darkod on 2012-05-14
Did you create the /dev/sda2 swap partition?

That was your win7 boot partition with the boot files. Now it seems it's type swap, not ntfs. No boot files to detect, no win7 entry in grub menu.

Can you open /dev/sda2 and look what's inside? Do you see /bootmgr or /Boot/BCD?

---

### Post by wilee-nilee on 2012-05-14
[FONT=Verdana, sans-serif][SIZE=1]I just noticed darkod had posted so check through their advice and questions first.
[/SIZE][/FONT]

---

### Post by Tuna_Can on 2012-05-15
Yes, I did something with the partitions when installing. It said something about needing a swap partition or something, idk what I did.
Now I made a repair usb and did fixboot and all those cmds.
I got this error
[img]https://photos-1.dropbox.com/btj/f8485016/7YRTNtKGJT-YGtPR52db_g0i92m1v6Q7iPszPJ8bp9k/IMG-20120514-00009.jpg?size=800x600[/img]
Now when I start the laptop it says "No operating system"

Idk how to view the partitions.

---

### Post by wilee-nilee on 2012-05-15
> **Tuna_Can said:**
> Yes, I did something with the partitions when  installing. It said something about needing a swap partition or  something, idk what I did.
Now I made a repair usb and did fixboot and all those cmds.
I got this error
[img]https://photos-1.dropbox.com/btj/f8485016/7YRTNtKGJT-YGtPR52db_g0i92m1v6Q7iPszPJ8bp9k/IMG-20120514-00009.jpg?size=800x600[/img]
Now when I start the laptop it says "No operating system"

Idk how to view the partitions.

Can you post that where a account is not needed here is a free image link.  
[http://imagebin.org/index.php?page=add](http://imagebin.org/index.php?page=add)

Here is a free text one as well.
[http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Key thing with these fixes are that any changes and the system is not working need a new bootscript posted.

Here is a link and command to run it straight. Extract the tar to your desktop and run the command for the results.txt.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

If you are in root with backtrack sudo is not needed.

---

### Post by Tuna_Can on 2012-05-15
Error from the picture is:
The volume does not contain a recognized file system.
Please make sure that all required file system drivers are loaded and that the volume is not corrupted.
[http://paste.ubuntu.com/988499/](http://paste.ubuntu.com/988499/)

---

### Post by wilee-nilee on 2012-05-15
> **Tuna_Can said:**
> Error from the picture is:
The volume does not contain a recognized file system.
Please make sure that all required file system drivers are loaded and that the volume is not corrupted.
[http://paste.ubuntu.com/988499/](http://paste.ubuntu.com/988499/)

Lets wait and see what darkod is thinking, the sda2 was the boot  partition it is the right size, and really to small for a swap. I  believe that the missing windows boot files can be put back in but the  challenge I believe is having the Windows set up after the backtrack on  the hard drive.

Windows is best generally at the beginning of the disc, and especially with repairs.

You are basically missing these highlighted files for the windows boot.

```
**/bootmgr /Boot/BCD** /Windows/System32/winload.exe
```

---

### Post by Tuna_Can on 2012-05-15
Thanks for helping

---

### Post by darkod on 2012-05-15
You should make /dev/sda2 ntfs before trying the windows repair. Boot with the BT cd in live mode (I assume it has one too), open Gparted or similar partitioning tool, and format /dev/sda2 as ntfs.

After that repeat the win7 repair commands. That should work.

Note that the repair will make win7 boot automatically, grub2 on the MBR is already deleted by the /fixmbr you did. So, you will need BT live mode again to reinstall grub2 to the MBR.

PS. Also, formatting the swap partition as ntfs will probably create error with BT because it will keep looking for swap. You can comment out the swap line in /etc/fstab temporarily until you decide if you will make new swap partition or not. There is also the option to simply use a swap file which might be easier in this situation.

---

### Post by Tuna_Can on 2012-05-16
Now it is saying BootMGR is missing. Press ctrl alt del to restart.

I googled it and tried re-creating the bcd store
Bcdedit /export C:\BCD_Backup
ren c:\boot\bcd bcd.old
Bootrec /rebuildbcd 

But that didn't work.

---

### Post by darkod on 2012-05-16
Did you use the repair option booting with the win7 dvd? If you use the auto option, you need to run it 3-4 times until it fixes everything, that's how windows does it.

Or you can open the command prompt after booting with the win7 dvd and run the commands manually, like:
bootrec /fixmbr
bootrex /fixboot
bootrec /scanos
bootrec /buildbcd

If you need help to open the command prompt, look here but run all the commands from above. Only two of them are mentioned in this link:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

That link also has instructions to reinstall grub2 to the MBR after win7 is booting correctly. You will need to do it with the ubuntu cd.

---

### Post by wilee-nilee on 2012-05-16
> **Tuna_Can said:**
> Now it is saying BootMGR is missing. Press ctrl alt del to restart.

I googled it and tried re-creating the bcd store
Bcdedit /export C:\BCD_Backup
ren c:\boot\bcd bcd.old
Bootrec /rebuildbcd 

But that didn't work.

Run the bootscript again, extract it to the desktop with the link and run the command.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```The commands in the above post may get you all set as well.

---

### Post by Tuna_Can on 2012-05-16
I was messing around in dos. I copied c:/boot/bcd over to e: where windows is and stuff like that. I doubt that helped but then I ran the startup repair(the automatic one) and windows started. Thanks alot!

---

