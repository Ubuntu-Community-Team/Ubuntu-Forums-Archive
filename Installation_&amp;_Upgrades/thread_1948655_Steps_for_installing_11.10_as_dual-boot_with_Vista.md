---
title: "Steps for installing 11.10 as dual-boot with Vista (Please correct my mistakes)"
date: 2012-03-28
forum: Installation &amp; Upgrades
---

### Post by mercedes on 2012-03-28
Greetings from a chronic newbie.

I've been using Ubuntu on and off since 2003, but it's been a long time since I had to install it myself, because my last two computers came with it already installed. The more recent of these (Zareason Terra HD) is in the shop with a fan issue, so I bought a refurbished Thinkpad T61 (2.0 GHz, 2GB RAM, 80GB HDD) so I could keep working in the meantime. It has Vista Business installed--sigh. I've been doing my best to work with it for a few days, but I think this will make a better long-term backup computer if I get Ubuntu working on it now.

Unfortunately I sometimes need to use Windows for work. On the Zareason I run XP in Virtualbox. On this T61, I figured it would be better to just leave Vista alone and dual-boot Oneiric. I just don't want to wipe out the ThinkVantage capabilities, even though I hope I'll never need them. 

I've been ferreting around the internet for awhile trying to figure out the best way to install Oneiric as a dual-boot. I just want to make sure I have the steps right before I do anything irreversible.

So, below, I made a list of the steps I think I should take. Please correct me at any step...

1. I've already burned recovery discs of Vista using Thinkvantage Rescue and Recovery, just in case.

2. In Windows, use the Disc Management tool to defrag, then shrink the main partition, thus creating free space for Ubuntu. Reboot in Windows a couple times.

3. Boot from Oneiric live USB.

4. At the “Installation Type” screen, select the “Something Else” option.

5. Select “free space” and click “add.” I think Windows is already using two or three partitions, so I'll have to make a logical partition for all the Ubuntu partitions.

6. I want to make four Ubuntu partitions, for /boot, swap, / and /home. Given that I've got about 40 GB free, I'll allocate 258 MB to /boot, 2 GB to swap, 15 GB for / , and the rest for /home.

7. Install the boot loader in the /boot partition.

8. Finish installation and reboot in Vista.

9. Install EasyBCD and add GRUB2 to Windows' boot menu. Change boot default to Ubuntu. 

10. Boot Ubuntu and enjoy, using Vista only when I really have to...

I would greatly appreciate it if someone who knows more than I do (and that would be most people on the forums) would look at what I plan to do and tell me what I've got wrong. I'm really hoping to get this installed without a hitch so I can get back to work! Thanks for taking the time to look at this.

P.S. I know I could also do a clean install of Ubuntu and run Vista in Virtualbox using the recovery CDs. If anyone thinks that would be a significantly simpler/safer solution, please say so.

---

### Post by darkod on 2012-03-28
The plan is very good.

The only things I would change:
6. Do not create a separate /boot partition. There is really no need for it especially on a desktop system.
7. Install the bootloader to the MBR of the disk, in other words to /dev/sda not to any partition. Grub2 is not as easy to chainload as the older grub1. Use it as main bootloader if you don't mind instead of using EasyBCD to add an entry in windows bootloader.
9. In case you take the advice above, you don't need step 9 too.

---

### Post by Mark Phelps on 2012-03-29
If you want a recoverable image of Vista that won't require you to reinstall all your apps and apply (possibly) hundreds of Windows Updates again, then consider the following alternate approach:

1) Download and install the FREE version of Macrium Reflect (MR) in Vista
2) Shrink the Vista OS partition using the Disk Management utility
3) Reboot Vista a couple of times
4) NOW ... connect an external drive and image off the Vista setup to that drive using MR
5) Also use the MR feature to create and burn a Liunux Boot CD

NOW, you have the ability to restore Vista to its current state -- so you won't have to reinstall any apps or apply lots of Windows Updates (again).

---

### Post by mercedes on 2012-04-05
Thanks, Darko and Mark. I followed your advice and I'm now dual-booting without a hitch. Here the steps I took, in case anyone's interested:

1. Burn recovery discs of Vista using Thinkvantage Rescue and Recovery, just in case.

2. Download and install the FREE version of Macrium Reflect (MR) in Vista.

3. In Windows, use the Disc Management tool to defrag, then shrink the main partition, thus creating free space for Ubuntu. Reboot in Windows a couple times.

4. Connect an external drive and image off the Vista setup to that drive using MR.

5. Boot from Oneiric live USB.

6. At the “Installation Type” screen, select the “Something Else” option.

7. I think Windows is already using two or three partitions, so I'll have to make logical partitions for all the Ubuntu partitions. Given that I've got about 40 GB free, I'll allocate 2 GB to swap, 15 GB for / , and the rest for /home.

8. Install the bootloader to the MBR of the disk, in other words to /dev/sda 

(I didn't take the time to figure out how to use Macrium Reflect to make a boot CD, but the program worked just fine for creating an image of Vista.)

---

### Post by bcarlowise on 2012-04-05
> **Mark Phelps said:**
> If you want a recoverable image of Vista that won't require you to reinstall all your apps and apply (possibly) hundreds of Windows Updates again, then consider the following alternate approach:

1) Download and install the FREE version of Macrium Reflect (MR) in Vista
2) Shrink the Vista OS partition using the Disk Management utility
3) Reboot Vista a couple of times
4) NOW ... connect an external drive and image off the Vista setup to that drive using MR
5) Also use the MR feature to create and burn a Liunux Boot CD

NOW, you have the ability to restore Vista to its current state -- so you won't have to reinstall any apps or apply lots of Windows Updates (again).


I have found that Clonezilla works really well for either full disk backup or partition backups. I use it to backup my dedicated linux disk as well as my Windows partitions on my 2nd disk.

---

### Post by Mark Phelps on 2012-04-05
> **bcarlowise said:**
> I have found that Clonezilla works really well for either full disk backup or partition backups. I use it to backup my dedicated linux disk as well as my Windows partitions on my 2nd disk.

While I won't debate that ... MR gives you features that Clonezilla does not -- one being that you can "mount" a backup image and browse it. This is useful for comparing files or for extracting files from backup images.

Also, MR will allow you to perform the image backup while still using MS Windows.  You don't have to boot using a CD, and you don't have to boot into a separate backup program.

Given that BOTH MR and Clonezilla are free, and that MR has more to offer to MS Windows users, the MR choice should be apparent.

---

### Post by bcarlowise on 2012-04-10
> **Mark Phelps said:**
> While I won't debate that ... MR gives you features that Clonezilla does not -- one being that you can "mount" a backup image and browse it. This is useful for comparing files or for extracting files from backup images.

Also, MR will allow you to perform the image backup while still using MS Windows.  You don't have to boot using a CD, and you don't have to boot into a separate backup program.

Given that BOTH MR and Clonezilla are free, and that MR has more to offer to MS Windows users, the MR choice should be apparent.


You make some good points. I rarely use MS Windows though so I prefer to have apps that do not depend on booting into MS Windows so Clonezilla works nicely for me in that regards.

---

