---
title: "Ubuntu 11.04 boot loader problem"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by calmness on 2011-05-08
I have Windows dual boot machine running XP and 7 in one HDD.  In another HDD, I installed Ubuntu 11.04 beta 2.  When I was installing, I had to choose the location of the linux boot loader and I chose the second HDD instead of the first, since I was afraid of messing up the existing Windows boot loader.  Incidentally, Ubuntu recognized only 7 and not XP.  

Now after successfully installing U 11.04, I am unable to boot into it.  Since 7 was not working anyway, I removed it and now I have only XP.  When booting, I am still presented with Win boot loader showing both XP and 7, though the latter was removed.  Ubuntu doesn't turn up at all.

In XP, I am now unable to access the partitions I used to instal linux and the swap partition.

I am no geek and was able to come this far through trial and error.  What can be the solution?  May I should re-install linux and the boot loader in the first HDD?  Will it interfere with my existing XP insallation?

---

### Post by kansasnoob on 2011-05-08
Please download and run the Boot Info Script by running these commands (please copy-n-paste):

```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'
```

```
sudo bash boot_info_script.sh --gzip RESULTS.txt
```

That will download the Boot Info Script to your home folder, run the script and create a file titled **RESULTS.txt.gz**. That is the file we need to see.

It can be attached using the paper clip at the top of the reply box. Just click on Browse, then select your home/username from the list on the left, locate and double-click the **RESULTS.txt.gz** as shown here:

[ATTACH]191550[/ATTACH]

Then click on Upload, minimize the Manage Attachment window, click on the paper clip again, and attach that file :)

---

### Post by calmness on 2011-05-08
Thanks for the response.

I seem to have lost those two partitions and even Partition Magic is unable to help.  It shows that there are errors on the second HDD and even refuses to format the HDD.

Guess I'll have to use a linux Live CD to access those partitions and format them, so that I can start over.

---

### Post by calmness on 2011-05-08
> **kansasnoob said:**
> Please download and run the Boot Info Script by running these commands (please copy-n-paste):

```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'
``````
sudo bash boot_info_script.sh --gzip RESULTS.txt
```That will download the Boot Info Script to your home folder, run the script and create a file titled **RESULTS.txt.gz**. That is the file we need to see.

It can be attached using the paper clip at the top of the reply box. Just click on Browse, then select your home/username from the list on the left, locate and double-click the **RESULTS.txt.gz** as shown here:

[ATTACH]191550[/ATTACH]

Then click on Upload, minimize the Manage Attachment window, click on the paper clip again, and attach that file :)

I tried to instal Ubuntu again and this time I made sure that the boot loader was installed on the 2nd HDD and not on any specific drive therein.  After installation, I was asked to restart the system.  I did that and the results are the same.  

Though Win 7 was removed, since this version of Windows had probably overwritten the MBR, I still get the same old boot menu: Win XP or 7.  No Ubuntu.  

I am unable to run the commands you have specified, since I am not able to access the linux partition.  It has disappeared in Windows and I unable to boot into Linux since the bootloader doesn't show linux.  I tried to run the same linux CD in Live CD mode and it doesn't help. ](*,)

Guess I'll have to give up the linux experiment.  I have tried over a period of years to install and run both linux and windows in a dual boot mode and have failed.  It didn't work with Red Hat (both the normal and enterprise editions), Ubuntu and another distro whose name I have forgotten.  And I had all sorts of trouble with the hardware configuration with linux.  I have a Knoppix Live CD dating back some years and it still works, though without support for soundcard and some other hardware.  I think I will stick to that and leave aside the "install-and-run" versions of linux.  

Good day and sorry for the rant.  

Thanks again, kansasnoob !

---

### Post by kansasnoob on 2011-05-08
You can run the BIS using the Live CD :)

---

### Post by satriosesat on 2011-05-13
i am confuse

---

### Post by oldfred on 2011-05-13
You are only showing one 100GB drive. With Ubuntu in sda1 and windows in sda2 (boot/recovery) and the windows main install in sda3.

It does not look like you created a swap partition. Were you confused by windows refering to c: drive and d: drives? That could be two drives or just two partitions, windows does not tell you just from that info.

You need to install grub2's boot loader to the MBR of sda.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda1 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda1 if not correct:
sudo fdisk -l
#confirm that linux is sda1
[COLOR=DarkRed]sudo mount /dev/sda1 /mnt[/COLOR]
sudo grub-install --root-directory=/mnt/ /dev/sda
If grub 1.99 with Natty uses boot not root
[COLOR=DarkRed]sudo grub-install --boot-directory=/mnt/ /dev/sda[/COLOR]
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
[COLOR=DarkRed]sudo update-grub[/COLOR]

---

