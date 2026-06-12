---
title: "Tried to dual-boot 4 times, still unsucessful"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by Rubix_hax on 2008-05-31
Someone chop my balls off, I am getting REALLY pissed with this dual-boot crap. I installed windows xp. Then popped in my 8.04 ubuntu, installed it using the "manual" option. The pic attached shows what partitions I made before installation. So I install, all happy, restart, then when the computer boots again, an err mssg comes up "windows is missing a file blah blah" So it pretty much erased windows, AND linux didn't even boot. 

BULL F*CKIN S*IT

the 4th time, I installed linux, using the "FULL INSTALL" option, in other words, use my whole 80 gb of hard drive. It did, restarted, and now, I am going to wait until someone tells me EXACTLY what to do.

Also, is it better if I install windows BERFORE linux? I read a few thread hear saying that is is better b/c you don't loose the MBR (w/e the heck that is)

Help this sob....

---

### Post by Rallg on 2008-05-31
Did your computer come with XP already installed? If it did, have you moved the starting point of the Windows partition? It may be that some installations of XP use the partition's starting point as one piece of information used to determine if the copy of XP is authentic. I tell you this because if you later find that your XP registration code is rejected, and if your copy really is authentic, you may have to phone MS fo a new code. Maybe, maybe not. That's for later, now to your problem:

1. Those are strange partition sizes. I believe that swap does not need to be more than 2X the size of your RAM.

2. Why do you need such a large /boot partition? For that matter, why do you need ANY /boot partition? Yes, you CAN do it that way, but I wouldn't go fooling with a /boot partition unless you have already been successful with dual-boot situations (and know what an MBR is).

3. A separate /home partition is favored by many users, but is not required. I asume you have decided based on the advantages and disadvantages from other information.

4. Did the FAT32 partition come with your computer, or did you create it new? If it came with your computer, I suggest that it not be touched at this point.

5. Windows should always be installed before Linux. The reason is that Windows does not recognize a pre-existing system on the hard drive, but many Linux distros (including Ubuntu) know if Windows is already there, and take that into account.

6. Assuming that you can afford to lose all previous information, I recommend that you adjust partition sizes, then re-install XP fresh, from scratch. Get it fully working (has its reg code, updated, functions well). Then try the Ubuntu installer again.

7. When you re-install Ubuntu, you will need to re-format the root (/) partition and (if you use it) /home, as well as linux-swap. After that, allow Ubuntu to install the Grub boot loader on (hd0,0) which is the default location. You can change the location using the "Advanced" button that the installer provides, just before the final installation dialog window. However, unless you have good reason why, leave it at (hd0,0). That will over-write your Windows boot loader.

8. You should be able to re-boot to the Grub screen, which will offer you a choice of operating systems. If you don't choose quickly, you will be booted to Ubuntu, which is what you want at this point. Now, can you get to Ubuntu? If so, run the Administration Update Manager. Some hardware won't run wireless until after update and installation of special drivers, so you might need a cable hookup.

9. If Ubuntu is working for you, then you might want to change which system (XP or Ubuntu) is your default, and how much time the boot loader allows you to think about it. This can be done by manually editing the Grub menu. Within Ubuntu, from Terminal:

gksudo gedit /boot/grub/menu.lst

lets you edit the file, but of course you will also need to know what to edit. You can find info elsewhere on this forum.

10. Be sure that you can boot to either XP or Ubuntu, at will.

11. If, when you boot to Ubuntu, you get a failure to load hardware (typical symptom is hanging, or strange graphics behavior), then you might need to boot to "recovery mode" and after logging in,

sudo apt-get update && sudo apt-get upgrade

with Internet connection. If that works, try re-boot to normal Ubuntu.

12. If you ever re-size or re-format a partition, then its UUID (identification) will change. The Grub loader finds partitions by UUID. So, if you ever do that in the future, you will need to discover the new UUIS and edit the Grub menu.lst

13. Dual-booting is not for people who have anger management issues.

---

### Post by Pioneer5000 on 2008-06-01
This is how i got Vista and Ubuntu working, guess it should be the same for XP.


This is what i did but I'm not sure if this will be what you want to do. I reformatted Vista using the Vista disc and then created partition when installing Vista. So pretty much:

1. I just put in Vista disc that came with laptop and rebooted. Formatted current partition(s) and then deleted it.

2. Then created new partition i just choose size 58000 (guess this will depend on how big your HDD is and how much you want to dedicate to Windows) for partition and installed Windows onto it.

3. After doing that and having Windows fully installed, restarted computer now with Ubuntu disc in, choose the install Ubuntu option.

4. When it came up to the partition part of the installation i just simply choose " Use largest contiguous free space" (not sure if it says free or empty) And since i had used half for windows the other half was free. Installed Ubuntu onto that and then i was done.

Now when i boot up comp it has both Ubuntu and Windows options and both working.

Not sure if this will help as you may not want to reformat HDD.

Please take note that i am no Linux pro but this is what i did and it seems to be working. Good Luck i know how frustrating it can be.

Also maybe try this? :

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by Rubix_hax on 2008-06-01
> **Rallg said:**
> Did your computer come with XP already installed? If it did, have you moved the starting point of the Windows partition? It may be that some installations of XP use the partition's starting point as one piece of information used to determine if the copy of XP is authentic. I tell you this because if you later find that your XP registration code is rejected, and if your copy really is authentic, you may have to phone MS fo a new code. Maybe, maybe not. That's for later, now to your problem:

1. Those are strange partition sizes. I believe that swap does not need to be more than 2X the size of your RAM.

2. Why do you need such a large /boot partition? For that matter, why do you need ANY /boot partition? Yes, you CAN do it that way, but I wouldn't go fooling with a /boot partition unless you have already been successful with dual-boot situations (and know what an MBR is).

3. A separate /home partition is favored by many users, but is not required. I asume you have decided based on the advantages and disadvantages from other information.

4. Did the FAT32 partition come with your computer, or did you create it new? If it came with your computer, I suggest that it not be touched at this point.

5. Windows should always be installed before Linux. The reason is that Windows does not recognize a pre-existing system on the hard drive, but many Linux distros (including Ubuntu) know if Windows is already there, and take that into account.

6. Assuming that you can afford to lose all previous information, I recommend that you adjust partition sizes, then re-install XP fresh, from scratch. Get it fully working (has its reg code, updated, functions well). Then try the Ubuntu installer again.

7. When you re-install Ubuntu, you will need to re-format the root (/) partition and (if you use it) /home, as well as linux-swap. After that, allow Ubuntu to install the Grub boot loader on (hd0,0) which is the default location. You can change the location using the "Advanced" button that the installer provides, just before the final installation dialog window. However, unless you have good reason why, leave it at (hd0,0). That will over-write your Windows boot loader.

8. You should be able to re-boot to the Grub screen, which will offer you a choice of operating systems. If you don't choose quickly, you will be booted to Ubuntu, which is what you want at this point. Now, can you get to Ubuntu? If so, run the Administration Update Manager. Some hardware won't run wireless until after update and installation of special drivers, so you might need a cable hookup.

9. If Ubuntu is working for you, then you might want to change which system (XP or Ubuntu) is your default, and how much time the boot loader allows you to think about it. This can be done by manually editing the Grub menu. Within Ubuntu, from Terminal:

gksudo gedit /boot/grub/menu.lst

lets you edit the file, but of course you will also need to know what to edit. You can find info elsewhere on this forum.

10. Be sure that you can boot to either XP or Ubuntu, at will.

11. If, when you boot to Ubuntu, you get a failure to load hardware (typical symptom is hanging, or strange graphics behavior), then you might need to boot to "recovery mode" and after logging in,

sudo apt-get update && sudo apt-get upgrade

with Internet connection. If that works, try re-boot to normal Ubuntu.

12. If you ever re-size or re-format a partition, then its UUID (identification) will change. The Grub loader finds partitions by UUID. So, if you ever do that in the future, you will need to discover the new UUIS and edit the Grub menu.lst

13. Dual-booting is not for people who have anger management issues.

dood,

i love you. it worked.

:popcorn::popcorn::popcorn::popcorn::popcorn::popcorn::popcorn::popcorn:

---

### Post by meierfra. on 2008-06-01
> i love you. it worked. The best way to thank somebody is to click on the blue ribbon with the gold star at the bottom right  corner of a post.

---

### Post by Rubix_hax on 2008-06-01
I just thanked everyone!!!!!!!!!!

RALLYG U THE MAAAAAAAAAAAN!

now....time to crack my neighbors WPA :D

---

