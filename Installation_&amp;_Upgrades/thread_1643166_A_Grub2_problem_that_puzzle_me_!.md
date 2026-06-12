---
title: "A Grub2 problem that puzzle me !"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by georgesgiralt on 2010-12-11
Hello !
First of all, I did not know an suitable forum to post this. So I put it here. If I'm wrong, please fell free to relocate it elsewhere ! 

So I've a computer with a lot of disks which is running Ubuntu 9.04.
The setup is made od a software raid 1 array of 200 MB for use in /boot (md0), then another raid1 array of the remaining space as a unique PV for the LVM2 vg0.
This vg0 is split in many lv, for /, /usr .... and swap.
A few days back, one of the raid1 disk went wrong. So as the raid is built on 160Gb disks and nobody in my town sells so little disks ;-) I bought a couple of 320GB disks. 
The partitioning was made like the original partitions, except that the second partition is way bigger than it was. 
I replaced the failed disk in the arrays, and now I've an md0 of 200 MB and an md1 of roughly 150GB as it was previously and all is in sync.
This replacement was made using a rescue disk (in order to be sure that the machine was not locking anything...)
So I thought it was fine. But upon reboot on the hard disks, I get a fast GRUB message "error: no such device : <UUID ending in 4ec05>.
when I start the first Ubuntu entry I get the same error. 
So I edit the boot entry, remove the "search --no-floppy --fs-uuid --set <UUID ending in 4ec05> " and boot the damn thing. 
When booted I ran :
update-grub
checked that the /boot/grub/grub.cfg has the correct UUID (it ends in d2f8d) 
then, being paranoid I ran grub-install /dev/sda .
Then I rebooted the computer, just to find that it still search for the same cf4ec05 UUID ! 

I then rebooted and ran boot-info-script and looked in the RESULTS.txt file for UUID. 
Guess what ? the cf4ec05 ending one is NOT in the file. But my md0 has the one ending in d2f8d.
So I ask for help and your advice ! I'm stuck here 
Many thanks in advance for your help and advice !

---

### Post by wilee-nilee on 2010-12-11
Did you run update grub again after loading grub2 to the mbr?

---

### Post by georgesgiralt on 2010-12-11
Can't tell for sure.
Will do a grub-install then an update-grub a couple of times to be sure....

---

### Post by georgesgiralt on 2010-12-11
So I ran update-grub, then install-grub /dev/sda (my first Sata drive which the BIOS is set to boot to)
then another update-grub. 
Guess what ? .....
Still the same error with the same UUID ! 
I'm thinking buying some garlic and saint images or a bottle of holly water ....

---

### Post by wilee-nilee on 2010-12-11
I'm not familiar with raid, 9.04 is past the end of release as well.

---

### Post by Rubi1200 on 2010-12-11
I suggest you post the results of the boot info script linked at the bottom of my post (instructions included).

Post the results back here please.

Also, is this a RAID1 or RAID0 setup?

Thanks.

---

### Post by oldfred on 2010-12-11
Take a look at /var/cache/debconf/config.dat. We used to have to run this to get the sda or sdb upated as it stored by drive not other info. I just looked at mine with Lucid and it has drive not UUID, so maybe not the solution.

To see where dpgk sees grub (this is the part of config.dat you want to see):
sudo debconf-show grub-pc
To reset
sudo dpkg-reconfigure grub-pc

---

### Post by georgesgiralt on 2010-12-11
Hello !
Here is the results from the boot script I ran a couple of hours ago.
I've made the dpkg-reconfigure thing. Let you know how it went. 
Thanks fo your help.
P.S there is a menu file for grub on LV4 (which is mounted on /root) it is an old file made when one needed to set the keyboard stright in the menu file...

---

### Post by oldfred on 2010-12-11
I do not know RAID nor LVM and you have both.

But the only way the old partition info would be saved is if it was in the MBR. Sometimes the script shows info like yours and sometimes it says which UUID it is looking for (not sure why).

So are you sure you are booting from the drive with the updated grub install adn not one with the old UUID info? I would even test booting each drive.

I have two identical 160GB drives and originally had to try to boot one or the other as I did not know for sure what boot loader was in which drive. Boot script helps a lot.

---

### Post by georgesgiralt on 2010-12-11
Oldfred,
When I did the reconfigure for the grub package, the procedure asked onto which disk it should install on.
I gave it all disks. So even if I'm wrong or mistaken, the MRB should have been updated on every disk. 
The sda disk is my first SATA drive. I checked and double checked and confirmed that. (it took time to figure that the IDE disk was at the end of the detected disks, and at first I did not thought (or remember) that I booted ot the first IDE disk. This happens when you use the very same hardware for years and add devices during that course of time).
I've had another idea to try but it is too late now where I live. 
I wonder if there are files on lv1 under the /boot mount point.
When booting, the md0 is not on /boot yet. So if something is screwed up and there are files on that directory they will be hidden by the mount after the boot had taken place.
I can't see another way to have the same UUID even after rebuilding everything...
I'll keep you posted.

---

### Post by georgesgiralt on 2010-12-12
Hi !
Finally, after a good sleep, I found it.
It was right under my nose.
Dmesg tell it all :
md: sdc1 has same UUID but different superblock to sda1
md: sdc1 has different UUID to sda1
md: export_rdev(sdc1)
md: sdc2 has same UUID but different superblock to sda2
md: sdc2 has different UUID to sda2
md: export_rdev(sdc2)
Sdc is the failing disk. As I had removed it from the two arrays, I let it into the box, planning to remove it before putting the machine back in the hands of my wife. 
Now, with the faithfull aid of dd and /dev/zero, it has been cleaned and wiped, and don't mess around anymore ... 
I'm astonished as the search command  in grub finds out all MD superblocks (it is not the boot disk) and opens a config file.... 
Thanks a lot for your help ! 
Now I've just to grow the array to get the whole 320GB useable and tell the PV above it to grow a little bit...

---

