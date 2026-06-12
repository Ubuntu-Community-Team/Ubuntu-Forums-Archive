---
title: "install ubuntu 9.10 over a old version with dual boot"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by isagarran on 2009-11-21
Hello,

I've a Windows XP partition. Ans i created a ubuntu 8.10 partition. This ubuntu worked fine until i try to upgrade it to 9.04.
The upgrade was succesful but at reboot time, the screen was dark and i got "saw signal 11" in X11. I wasn't able to reoover from this error and my ubuntu partition is unusable.
I would like to install a ubuntu 9.10 (the last one) over this failing partition.
Do you know how to do that ? Is there some guidelines or do you know some tips where i need to be aware ? I wouldn't like to lost my XP partition as i'm not totally familiar with ubuntu.
Thank you for your help.
isagarran.

---

### Post by ajgreeny on 2009-11-21
You can do this easily by running the live CD install as usual, but when you get to the disk partitioning stage choose Manual, where you can manually set your partition use.

The installer will then look at your disk and show you what partitions are already there.  Assuming you used the default last time, you will have a larger ext3 partition which you will need to set as ext4 this time and mount it as / (root).  There will also be a smaller swap partition which should show and you can use that the same as swap this time.

Just make sure that the NTFS or FAT32 partition(s) that is windows is not used for anything and not formatted, and you should be fine.

---

### Post by isagarran on 2009-11-21
Thanks for your quick answer. I'm not sure to fully understand.
My partitions are today :
sda1 ntfs   (windows primary) 30G
sda2 extended (windows logical parttition)
sda5 ntfs   30G (windows second logical disk)
sda6 ntfs   30G (windows third logical disk)
sda7 reiserfs  / 14Go Linux
sda8 reiserfs /tmp 2Go Linux
sda9 reiserfs /home 4Go Linux
sda10 linux-swap
sda3 reiserfs /boot 250Mb Linux
Where do i have to do ? Do i have to refrormat them to ext4 ?
Do i have to do the same with the /boot partition ?
The linux boot partition is the first thing that i see at boot time. And the default one is Linux. If i want Windows, i have to scroll down on the boot menu. I don't know if it is important.
Could you tell me if i have to reformat all of them to ext4 (i don't know what is this) and to reinstall on top the 9.10 ?
Thank you very much for your help.
I appreciate greatly.
Isagarran

---

### Post by ajgreeny on 2009-11-21
WOW!  That's a complicated partition table you have there, and it does add the the possibilities of a mistake, I have to admit, but it should still be possible to do it right.

> sda7 reiserfs  / 14Go Linux
sda8 reiserfs /tmp 2Go Linux
sda9 reiserfs /home 4Go Linux
sda10 linux-swap
sda3 reiserfs /boot 250Mb Linux
Which of these is your ubuntu 9.04 which is un-usable?  They all appear to be for another distro, not ubuntu, but that may just be your labeling of partitions.

If you have no personal files on your ubuntu or other linux partitions or you have everything backed up, and just want a new ubuntu install without all the other partitions you show for linux you could simply boot to the live CD, run gparted and delete all the partitions showing in that list I copied, ie sda3, 7, 8, 9 and 10.  You could then start again with a simpler partition table, probably with a / (root) partition, a /home partition and a swap partition.  Those three are probably the most common way to do things other than just including the home folder in root, which is what happens if you let the installer do the job to a new disk, when you end up with a / and a swap partition, nothing else.

Ask again if you are still a bit confused and I'll try to help more, but it is difficult to be certain what all your partitions really are without a lot more info from you.

---

### Post by isagarran on 2009-11-21
This  kind of partitionning (/tmp,/home, etc) has been done by me manually. I thought that it was a good idea.
I hope that i won't enter in problem with the dual boot. I don't see how ubuntu 9.10 will see Windows XP after installation. I'm going to backup my windows data and follow your procedure.
Thank you for your advices and for your help,
Isagarran

---

### Post by ajgreeny on 2009-11-22
Just delete the various linux partitions, and make sure you don't touch the windows partitions sda1, 2, 5 and 6.

I'm totally sure that ubuntu 9.10 will find your WinXP when you install it, and add XP to the grub menu, so don't worry about that.  However, yes, it is definitely a very good idea to backup your windows XP files before doing any partitioning on a disk, even if in theory you are not going to do anything to those particular partitions.

---

