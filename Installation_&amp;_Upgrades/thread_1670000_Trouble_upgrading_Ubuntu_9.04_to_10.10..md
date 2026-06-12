---
title: "Trouble upgrading Ubuntu 9.04 to 10.10."
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by eitolafatee on 2011-01-18
I have a dell netbook that was previously running Ubuntu 9.04. I wanted to upgrade to the newest 10.10. I mounted the iso on a usb and tried to install. The process was going smoothly until almost at the end I got this message "Unable to install GRUB in /dev/mmcblko' failed". And I was presented with the option to quit, to install at a different location or to continue without installing. I could not select any of the options presented. And now, the computer won't boot at all. I would appreciate any and all help!

---

### Post by Innigo on 2011-01-18
I'm still a bit of a newbie but the impression I've gleaned is that you should upgrade 9.04 to 9.10, then 9.10 to 10.04, then 10.04 to 10.10 (if you can get the Update Manager to offer the next upgrade to you...) Also, there have been some changes to Grub with a few teething issues in the early stages so that seems to me the most likely thing to have gone wrong jumping straight to 10.10 over the top of 9.04

Maybe try running meierfra's boot_info_script and posting the results and a Grub wiz might be able to help you or else start again if you can.

#hosted at: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
# 
#The birth of the boot info script:
#   [http://ubuntuforums.org/showthread.php?t=837791](http://ubuntuforums.org/showthread.php?t=837791)

Hope this helps

---

### Post by akand074 on 2011-01-18
Do you have a separate /home partition or is everything in one partition? If you aren't trying to save any data (they should be backed up regardless) you should format the drive / Ubuntu's filesystem partition before installing.. that should work. If your entire system installed correctly, you could also try just installing Grub2 so you can boot. Check[ this]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") page for information on how to do that.

---

### Post by eitolafatee on 2011-01-19
> **akand074 said:**
> Do you have a separate /home partition or is everything in one partition? If you aren't trying to save any data (they should be backed up regardless) you should format the drive / Ubuntu's filesystem partition before installing.. that should work. If your entire system installed correctly, you could also try just installing Grub2 so you can boot. Check[ this]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") page for information on how to do that.

I am pretty sure everything is on one partition. I formated that drive and tried to reinstall. No go. I then booted from a USB and tried to reinstall grub2. I mounted the drive like the instructions told me but it won't let me install grub2. A note, I am pretty new to the Ubuntu game and I am prolly doing this all wrong!

---

### Post by kansasnoob on 2011-01-19
> **eitolafatee said:**
> I am pretty sure everything is on one partition. **[COLOR="Red"]I formated that drive and tried to reinstall.[/COLOR]** No go. I then booted from a USB and tried to reinstall grub2. I mounted the drive like the instructions told me but it won't let me install grub2. A note, I am pretty new to the Ubuntu game and I am prolly doing this all wrong!

You do know that formatting that drive erased all data, eh?

---

### Post by eitolafatee on 2011-01-19
> **kansasnoob said:**
> You do know that formatting that drive erased all data, eh?

Of course, I formated the drive to clear the way for the new os.

---

### Post by akand074 on 2011-01-19
Do you have more than one hard drive? Do you have a partition for Windows too? If not, try using Ubuntu's auto-installer to "use the whole drive", if you have Windows you can try reinstalling doing a manual install. I can give you instructions if you don't know how.

---

### Post by eitolafatee on 2011-01-20
> **akand074 said:**
> Do you have more than one hard drive? Do you have a partition for Windows too? If not, try using Ubuntu's auto-installer to "use the whole drive", if you have Windows you can try reinstalling doing a manual install. I can give you instructions if you don't know how.
 
I have only one hard drive and I am not duel-booting.

---

### Post by akand074 on 2011-01-20
Did you have Ubuntu use the whole drive during installation? A manual install should fix this regardless. Choose manual install when the installer gives you the option and it will open up a partition manager.

1. Delete the entire drive/every partition you have so that all you have left is just one big block of unallocated space.
2. a) If you don't want a separate partition for /home (config files and your data) make a new partition equal to the size of the entire drive minus the amount of RAM you have. Set it as type EXT4, Primary partition, beginning, choose to format, and give it a mount point of "/".
   b) If you do want a separate partition for /home then do the same thing as step A except just make the partition around 20GB-40GB, and then make a new partition with all the space you have left minus the amount of RAM you have and give it all the same settings except mount point of "/home".
3. Make a new partition with the amount of unallocated space you have left ~= to the amount of RAM you have and set it as "swap" and that's all you have to do for that one.
4. There will be a drop down menu asking where to install GRUB, it should automatically be on your only hard drive.. just make sure it is.
5. Click next and let the installer do it's thing. Once it's done you shouldn't have any problems, I have suggested this to another person before and it solved his issue with GRUB.. though he might have had two hard drives.. I can't remember.

Let me know if you get it fixed or if a manual install doesn't work.

---

### Post by eitolafatee on 2011-02-03
> **akand074 said:**
> Did you have Ubuntu use the whole drive during installation? A manual install should fix this regardless. Choose manual install when the installer gives you the option and it will open up a partition manager.

1. Delete the entire drive/every partition you have so that all you have left is just one big block of unallocated space.
2. a) If you don't want a separate partition for /home (config files and your data) make a new partition equal to the size of the entire drive minus the amount of RAM you have. Set it as type EXT4, Primary partition, beginning, choose to format, and give it a mount point of "/".
   b) If you do want a separate partition for /home then do the same thing as step A except just make the partition around 20GB-40GB, and then make a new partition with all the space you have left minus the amount of RAM you have and give it all the same settings except mount point of "/home".
3. Make a new partition with the amount of unallocated space you have left ~= to the amount of RAM you have and set it as "swap" and that's all you have to do for that one.
4. There will be a drop down menu asking where to install GRUB, it should automatically be on your only hard drive.. just make sure it is.
5. Click next and let the installer do it's thing. Once it's done you shouldn't have any problems, I have suggested this to another person before and it solved his issue with GRUB.. though he might have had two hard drives.. I can't remember.

Let me know if you get it fixed or if a manual install doesn't work.

You are the best! Totally worked!Thanks a bunch!

---

### Post by akand074 on 2011-02-03
> **eitolafatee said:**
> You are the best! Totally worked!Thanks a bunch!

That's great to hear! Mark this thread as solved from the thread tools menu if you don't have any other related questions so that it will be easier for people to find a solution in the future.

---

