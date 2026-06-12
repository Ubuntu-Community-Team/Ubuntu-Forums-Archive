---
title: "Booting issues"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by MrJKwik on 2006-07-14
New here, hope I have the right forum.

Here is my set up.  2 harddrives, 1 200 ide, 1 250 sata.  the 250 is set as primary boot drive.  the 200 basically holds data i moved to from the 250 before doing these installs.

First thing I did was to completely wipe the 250 drive using knoppix and qtparted.

Next, I loaded in Ubuntu (knoppix kept locking up)and used gparted to partion the 250 drive.  I left it as:

25gb ntfs for xp
10 ext3 for root
4gb for swap (i have 2gb of ram)
and the remaining as a ext3 partition.

installed xp first on the windows partition.
then installed ubuntu

booted, and got "DISC BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"

did some searches, found someone saying about going into qtparted and setting the drive to active.

so i loaded up knoppix, and did so.

next, i booted, and now i get "A kernel file is missing from the disk.  Insert a system diskette and restart the system."

now, i know the windows os is there, and the ubuntu, and grub.  how?

i have a multi xp install disc.  one of the options when i put the disc in other than which install to do, is "press escape to boot to first drive".  if i do that, it loads grub, and then i can pick which install will work.  did that twice, once for each os.

basically, its not loading grub on boot.  i could really use some detailed instructions and help with this.  i dont really wanna give up and wipe the drive again, and just say forget it.  after all the reading i've done on ubuntu, i'd like to give it a try, but dont wanna quite windows either.  so dual boot is the best option for me.

thanks for any help you guys give me.

---

### Post by cotcot on 2006-07-14
Your explanation is not very clear for me.
So finally you get in ubuntu or xp with your XP CD.
In that case you have to boot ubuntu. Go to terminal and type :
```
sudo grub
```
This will give you the grub prompt :  grub>
Then type :
```
setup (hda0,0)
quit
```
The grub bootloader should now be installed in the MBR.
Reboot without XP disk to check.

If i did not understand you well try to post your partition table. ("sudo fdisk -l" in terminal)

---

### Post by orb9220 on 2006-07-14
Which drive to active? should be sda1 or hda1 depending on sata or ide.

Grub installed on first hardrive?

Mine:

/dev/hda2       /               ext3   
/dev/hda1       /media/hda1     ntfs    
/dev/hda4       /media/hda4     ext3    
/dev/hdd1       /media/hdd1     vfat   
/dev/hda3       none            swap    
/dev/hdc        /media/cdrom0   

So xp on hda1 then / hda2 swap hda3 have a 45gb part at hda4 then my second hardrive is hdd1 and is 112Gb

Hope this helps Im kinda new myself.

---

### Post by MrJKwik on 2006-07-14
the xp install disc i have has more than one version of xp on it.  when i boot the disc, it gives me a few options such as which version of xp i want to use, as well as a few others.  if i select say 1, it starts an xp install.  at the bottom of the options, is an "exit" option that "boots to first disc".  when i select that, it will boot to grub.  from grub, i can boot to either xp or ubuntu.

i tried the setup grub instructions above, and got "error 23: error while parsing number". and i did change the hda to sda since its an sata drive.

here is everything presented to me when doing the command for the partitions.

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188        4526    10755517+  83  Linux
/dev/sda3            4527        5038     4112640   82  Linux swap / Solaris
/dev/sda4            5039       30401   203728297+  83  Linux

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
240 heads, 63 sectors/track, 26342 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       26342   199145488+   7  HPFS/NTFS



i really appreciate the help guys.  thanks.

---

### Post by MrJKwik on 2006-07-14
i've tried a few different things now.  found through searching and learning some commands, that grub sees the harddrives as hd0 and hd1.  so i tried the commands using hd0

these are the commands and their results so far:

grub> root (hd
 Possible disks are:  hd0 hd1

grub> setup (hd0,0)

Error 12: Invalid device requested

grub> root (hd0,0)
 Filesystem type unknown, partition type 0x7

grub> setup (hd0)

Error 17: Cannot mount selected partition


just updating if any of this helps.  still not working obviously.  like i said, i find it weird that grub is there, and gets there when 'booting to first disc'.  would it be my mbr is messed up?  how to fix that?

and just tried to use the xp recovery console to repair mbr, still nothing.

---

### Post by MrJKwik on 2006-07-14
fixed it.  dont know why, but looks like the mbr is on the other harddrive, the spare drive, and not the sata drive with the actual os's on it.  not sure it thats a problem or not.  if so, maybe someone can tell me how to fix it.

thanks.

oh, fixed it by going into the bios and for the hell of it, booting that drive first.

---

### Post by cotcot on 2006-07-15
After root you have to indicate the root partition of your linux install where the file /boot/grub is on, not the MBR. And sorry you were right (hd0) is to be used for the MBR and not (hd0,0). 
```
root (hd0,1)
setup (hd0)
```

Another way is described in  [http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm")
It is a tutorial for dual booting XP/Dapper and it includes a MBR restore step only.

0x7 is NTFS. This partition is obviously not mounted. But there is no need to because it had to be (hd0,1) a linux native partition. If you have done this from the installCD you had to mount it :```
mkdir whatevernameyouwant 
sudo mount /dev/sda2 whatevernameyouwant
```

---

