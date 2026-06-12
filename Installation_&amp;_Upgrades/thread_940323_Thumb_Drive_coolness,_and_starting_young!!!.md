---
title: "Thumb Drive coolness, and starting young!!!"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by buck2825 on 2008-10-06
I have just bought a new 8gb thumb drive $30 with shipping from tigerdirect.com.  I found a install guide that I just had to try.  Installing 8.04.1 on a 1gb or greater thumb drive.  so i gave is a spin.  the tutorial I found was on pendrivelinux.com.  I first followed the direction to the letter and everything seemed to work great (had to reinstall MBR as tutorial points out may be require and gives directions for).  but I now had a 8 gb ubuntu thumb drive.  ubuntu and other linux distros can read and write to the empty space but not my conformist family's PC's and MAC's. sigh.  so i tried to read the drive as is, with no changes, and Vista could see the OS partition (the tutorial makes two partions one for OS fat16, and one for user data ext2 /home...) so i gave it a shot to see what might happen.  deleted everything.  set up three partitions sdb1-sdb3.  sdb1 is a fat16 4 gb partition.  sdb2 is a 750Mb OS fat16 partition, and sdb3 is the rest of the thumb drive ext2.  installed OS and other files just like the directions state but formated sdb1 with label "storage" and shifted the partion number for all the directions (1 became 2, 2 became 3....)

long and short the thing works.  AWN, installs of all kinds and best of all it mounts the 4 gb partition on the desktop on boot.  and when i change to the useless vista partition windows mounts the 4 gb partition also 

to the avarage user a simple 4 gb thumb drive.  to the linux knowlagable user endless possibilities.  

one last note this weekend my sister was naging about vista not supporting her win95 vintage games (tetis, bejewled...)  I told her about ubuntu and happened to have my cd.  installed ubuntu on her spare 40 hd.  and poof games out the you know what.  so we went outside to enjoy the nice indiana fall air.  before leaving I walked inside and found my EIGHT YEAR OLD NIECE playing games.  no one started the games for her no one even told her they where there.  this next week i'm installing edubuntu on the little girls old win2000 pc.

---

### Post by buck2825 on 2008-10-06
I have found a few bugs i guess you would say regarding the install.  some of the user settings are not persistant as one would hope.  things like time, deleting install icon, startup of AWN and wallpaper setting sometimes go to default but i'm very pleased, in-all.

---

### Post by buck2825 on 2008-10-06
all this on a thumb drive

---

