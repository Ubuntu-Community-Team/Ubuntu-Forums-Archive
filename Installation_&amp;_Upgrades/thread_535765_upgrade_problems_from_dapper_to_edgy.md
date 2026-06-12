---
title: "upgrade problems from dapper to edgy"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by kenley on 2007-08-26
i installed dapper last year on a new compaq laptop.  dual boot.  worked fine.  great to get away from ms.  i thought i would upgrade to a later version of ubuntu.  so i started with the commands i found in this forum.  i found i needed to install edgy first.

i tried gksu "update-manager -c".  it could not find a couple web sites.  i downloaded the iso and made a bootable cd.  i also found on this forum information about about changing 'dapper' to 'edgy' in a sources list file.  then used the command gksu "sh /cdrom/cdromupgrade".  that finally got an upgrade to run.

after a reboot x.org does not start.  and it comes up to a busybox prompt.

when i boot the install cd i get to the disk partitioning window.  

i have 2 options guided and manual.

guided lists only ide1 master (hda).  it does not show my wxp partition.

when i select manual and go to the next window the only thing listed is /dev/hda.  when i click on forward i get a no root file system defined.  i do not want to lose my wxp partition.

will the install write over my wxp partition?

is there any way to install ubuntu in a linux partition that will not boot a previously installed version?

if i need other tools for this fix let me know.  

thanks for any help.

---

### Post by Pumalite on 2007-08-26
First, defrag XP several times, erase all temp files, then use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) to 'shrink' your XP partition. Then install. You might want to post your specs for better instructions.

---

### Post by kenley on 2007-08-27
i ran defrag.  i have never run defrag more than once before when i needed to run defrag.  seems to clean up more when it is run several times.  probably another ms feature.

when i run gparted the graphical interface window lists one drive with no particitions.  

when i run fdisk from gparted the command line commands will show several partitions.  the hd is 40 gb drive.  from the command prompt window hda1 shows a ntfs partition with 23 gb and hda2 shows 16 gb for a linux partition.

will a ubuntu install install in the linux partition even if it does not show the partition in the partition windows that come up when running the install from a cd??

should i try to reformat the linux partition as well?

---

### Post by kenley on 2007-08-27
i have tried runnning the alternative cd and selection rescue a broken system.  i work through the menus and get to where i can choose a partition to repair in.  i select hda2 since that is the linux partition.

the next window has some options and i select "execute a shell in /dev/hda2"

the next screen has a text concerning mounting other file systems.

i continue and in get a "#" at the bottom of the screen.  i have no other file systems to mount.  what do i have to do to continue with the rescue???

i there any manuals describing the different menus and what each item does??

for newbies like me that would come in handy.

---

### Post by Pumalite on 2007-08-27
Post your specs. Did you shrink the XP partition? If not what problems did you encounter?

---

### Post by kenley on 2007-08-27
i have deleted temp files and run defrag.

how small must the xp partition be?  is 23 gb on a 40 gb drive to much?  how big must the partition for ubuntu be?  is 16 gb not big enough?  if there is an article concerning partition size that would help me understand size limitations can you point me to it?

laptop=presario v2000
hdd=40 gb
hda1=23 gb ntfs
hda2=16 gb linux
hda3=unknown size(may be unformated area)
hda5=49 mb w95 fat32
hda6=370 mb linux swap / solaris

memory=512 mb

what other info do you need?

---

### Post by Pumalite on 2007-08-27
hda3 is probably your recovery partition. 16 GB for Ubuntu is fine. Give 8 GB for '/', you have the swap and give the rest to /home. Make sure you point Ubuntu to hd2 during installation; choose 'Manual if necessary.

---

### Post by kenley on 2007-08-28
i was able to get to prepare mounts points window by selecting manual.(screen shot is attached)

i know that there is a discussion over how many partitions and whether one should put /home in it's own partition.  i choose not to.  i understand that this should work.

i went through the next windows and the install started.  in a 60 sec the no root file system message came up.(see other attachment)

any suggestions as to what needs fixed now.

thanks for any help.

---

### Post by Pumalite on 2007-08-28
You are not giving a mount point for '/'

---

