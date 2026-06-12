---
title: "What settings are good to partition with?"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by hgfdsa on 2008-08-06
Step 4 of the installation process was confusing for me and I want to do it in manual because it is supposedly better, but don't know what settings to use. I also want to put /home on a different partition in case i ever need to reinstall ubuntu

---

### Post by Partyboi2 on 2008-08-06
make a root partition (ext3) with the mount point set as / (this is where all the system files will be kept)
Make another partition (ext3) for your home with the mount point set as /home (this is where all your data etc will be kept) 
Then make a swap partition (swap) (which should be roughly about x2 the amount of onboard ram)
so for example if I had a 40 gig space and 1 gig ram I could make something like this:
10 gig /
28 gig /home
2 gig swap

---

### Post by xen-uno on 2008-08-06
If your doing it manually then you can set the -noatime switch, which tells Ubuntu not to write the last access time for any file to disk. I used that option on all my ext3/NTFS partitions.

---

### Post by hgfdsa on 2008-08-07
> **Partyboi2 said:**
> make a root partition (ext3) with the mount point set as / (this is where all the system files will be kept)
Make another partition (ext3) for your home with the mount point set as /home (this is where all your data etc will be kept) 
Then make a swap partition (swap) (which should be roughly about x2 the amount of onboard ram)
so for example if I had a 40 gig space and 1 gig ram I could make something like this:
10 gig /
28 gig /home
2 gig swap

I already installed ubuntu when no one replied last night. Is there still a way to repartition it, or do I need to reinstall ubuntu? If i need to reinstall, how do I do so? I also have 71 gb of hard drive space and 512 ram, so I would have a 1 gig sswap but / increase or stay at 10 gig?

---

### Post by Partyboi2 on 2008-08-07
You can use the resize tool in gparted. Boot the live cd and open partition editor (system>admin>partition editor) use the resize function to resize your partitions. This can take some time. Also make sure you back up your important stuff before working on partitions.

---

### Post by hgfdsa on 2008-08-07
> **Partyboi2 said:**
> You can use the resize tool in gparted. Boot the live cd and open partition editor (system>admin>partition editor) use the resize function to resize your partitions. This can take some time. Also make sure you back up your important stuff before working on partitions.

Will gparted also allow me to split / and /home into different partitions? what size should my partitions be if I have 70gb for linux?

---

### Post by Partyboi2 on 2008-08-08
If you currently have your /home as part of the / partition and want to put it onto its own partition you can follow [[COLOR=Blue]this[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome") guide. But it probably be quicker to reinstall and make the partitions.
15 gig  /
54 gig /home
1 gig swap

---

### Post by hgfdsa on 2008-08-09
> **Partyboi2 said:**
> If you currently have your /home as part of the / partition and want to put it onto its own partition you can follow [[COLOR=Blue]this[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome") guide. But it probably be quicker to reinstall and make the partitions.
15 gig  /
54 gig /home
1 gig swap

This is going to sound really stupid, but how do I reinstall ubuntu? When I turn my computer on, it gives me 6 choices, where as before I had nothing. When I pick XP from the list, it brings me to a second list asking me to pick between xp and ubuntu again. I believe the reason for the second list is my first failed installation of ubuntu, so how do I completely remove ubuntu and also fix my bootloader or whatever it's called? Thanks.

---

### Post by |Eric| on 2008-08-09
well XP install with linux is touchy a bit (for windows not for linux :P ) 
there is a few things you can try:

#1: 
- cleanup the /boot/menu.lst
erase what you dont need keep your XP install & your main Linux install
(the one you use to boot)
- resize with Gparted or PQmagic



#2:
- boot direcly from CD then reinstall formating the partitions (exept the XP one & your personal files) you can also resize the partition here since you re formating everythig

in both cases loss of data may occur if not done properly 
use manual mode while instaling with CD since automatic is so crapy :P




To make a /home from an existing partition 
- just create a folder with your username as name  in the target partition (at the root of the partition that will become /home ) 
 & do  "sudo cp /etc/skell/*.* /media/(target partition)" or "sudo cp /home/(username) /media/(target partition)/" <<< this is better as you keep your settings

  (ex: mrbigdude = /home/mrbigdude   "sudo cp /home/mrbigdude /media/sdc2/ " )
   Note: you may need to change ownership with chmod (username):(usergroup) /media/(target partition)/(target user) -R

   ex: ~$ chown eric:eric /media/sdc2/eric -R


- obtain the target part with blkid (type it in terminal it gives somthin like the following )
~$ blkid
/dev/sdb1: UUID="5533e990-43d3-4426-b7bb-8a270a6958a1" TYPE="ext2" 
/dev/sda1: UUID="6f1a841d-2341-403f-8776-1aeb0bacbf78" TYPE="ext2" 
/dev/sda2: UUID="95396b5e-f893-46bf-acfb-c34a3d6e1663" TYPE="swap" 
/dev/sdc1: UUID="bbd9ec31-4bef-4de0-b556-ddae00473358" TYPE="ext2" << uuid is what is in the "" after the "UUID="
/dev/sdc2: UUID="55d2ab5a-64e6-49b0-96cf-54954075a43f" TYPE="ext2" 
/dev/sda5: LABEL="DATA_FAT" UUID="4702-D681" TYPE="vfat" 
/dev/sda6: UUID="4ECA4C12DF2D1C24" LABEL="DATA_NTFS" TYPE="ntfs" 


- add the uuid in the /etc/fstab (its a file "sudo mouspad /etc/fstab" to edit) 
add the line UUID=(uuid obtained from blkid) /home ext2(or ext3 if its your case) defaults 0 0


- go take a break & watch dirty movies :-)

---

### Post by Partyboi2 on 2008-08-09
An easier way maybe, is to backup any stuff you want to keep from your current ubuntu installation. Then boot the ubuntu cd and use gparted (system>admin>partition editor) and delete all your ubuntu partitions, so that you are left with unallocated space. Then start the installer and choose to manually partition and setup your 3 partitions (/,/home, swap) using the unallocated space. The other  way is to move your /home to its own partition which has already been mentioned and to [[COLOR=Blue]reinstall grub[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351")

---

