---
title: "Dual Boot - Vista already on RAID-1"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by johnbick on 2007-04-21
I have not used Linux (Unix) since back in the 1970s and thought this would be a good time toi try Kubuntu and, maybe, convert. 

CONFIGURATION: 
- ASUS P5B-E 
- Windows Vista is already installed on a RAID-1 (Mirror) set formatted NTFS - 150 GB Raptors (Uses P5B-E connectors 3 & 4) 
- Data is ion a RAID-5 (4 disks)  NTFS - 320 GB Cavaliers (Uses P5B-E connectors 1, 2, 5, 6) 
- JMicron SATA has a single NTFS drive used for backup 
- IDE (PATA) has DVD burner as Master
- FOR KUBUNTU I HAVE INSTALLED A SEPARATE IDE/PATA 120 GB DISK (Slave) with 
--- First partition 90 GB for Kubuntu, (EXT3) 
--- Second partition 9 GB for swap
--- Third partition 20 GB FAT -- I had been warned to stay away from R/W to NTFS at first.

PROGRESS TO DATE: 
1) Obtained and installed Feisty DESKTOP with no problems onto the intended disk. Was not asked about GRUB or dual boot and found I could only boot into Vista. Hmmmmm.....
2) Obtained and installed Feisty ALTERNATE install. Asked about GRUB at the end. It told me it was installed on the first disk! Thought I had it made this time, BUT...no choices on booting, it still goes straight into Vista. 
3) Have spent 6+ hours trying to search these forums (fora?) for a solution to no avail. (The answer is probably in there but danged if I can find it!) 

I suspect my problem has to do with the RAID mirror for that first drive... 

Need some help, please.... I just got this system up and running with Vista and am not really inclined to have to re-configure it!

---

### Post by jpeddicord on 2007-04-22
You are only installing one version of Ubuntu, right? Never install using *both* the alternate and desktop CDs, as that will just give you two Ubuntu installs.

Anyway, when the system boots, if you see a message that says "Press ESC to go to the menu", press it. You should see Ubuntu on there somewhere. :-)

Jacob

---

### Post by johnbick on 2007-04-22
Such was, of course, the theory (although I need to do an F8 and then an ESC to get there) but the (Windows) boot manager only shows the Vista system at the top (and a "Windows Memory Test" at the bottom). No Kubuntu. 

And no, there are not two Kubuntu partitions. When I did the alternate install I installed overthe first one (including a reformat).

---

### Post by johnbick on 2007-04-23
Bump....

---

### Post by johnbick on 2007-04-25
Lots of folks looking at this thread but no one responding?????

Lots of similar threads but no solution???? (At least my looking has not found anything...) 

Bump......

---

### Post by g8m on 2007-04-25
Did you change the boot prioritiy in the bios so that your ubuntu install boots first?

---

### Post by johnbick on 2007-04-25
Yes, I tried that and I get a completely different error message. (Unfortunately I cannot find where I wrote that down the other day but the general implication was that there was likely no MBR on that drive.) It definitely did not get into GRUB.

UPDATE: 
OK, G8M, you got me to try a seroies of re-boots to actually determine where GRUB installed. First, here is my configuration (an ASUS P5B-E system) 

Intel Controller
SATA 0-1-4-5 (connectors 1-2-5-6) are a RAID5 array used for data and are "D:" under Vista (4 Cavalier 320s) One partition
SATA 2-3 (connectors 3-4) are RAID 1 used for boot drive "C:" under Vista. (2 Raptor 150s) One partition
JMicron Controller: 
SATA has one Cavalier 320 that configures as "F:" under Vista. (Configured for IDE) One partition
IDE bus has DVD Burner as Primary and 120 Cavalier to which I have installed Kubuntu. There are 3 partitions: 83 for Kubuntu root (/), 9 GB for Swap and 19 GB for FAT32 that shows as "I:" for  Vista. 

Boot results for each, in order: 
Boot from the RAID5 does get me to GRUB but I get "Error 21" and it stops there. (I had not tried this before your asking, G8M! Thanks!) 
Boot from RAID1 takes me to Vista
Boot from 320 tells me "Boot Manager is Missing". 
Boot from 120 (this is where Kubuntu is actually installed) gets me "Error loading OS" 

So, at least I know now that Grub installed to the incorrect disk! (Or, one can argue, Windows installed it's boot manager to the wrong disk....) And we know something is wrong with the way it installed: (1) it did not run correctly asd indicated by the "Error 21" and (2) it is not giving a choice between Vista and Kubuntu -- at least not yet.....

Soooo..... Where do I go from here? (Remember, I am a newbie to Linux.....

---

### Post by psusi on 2007-04-25
Do you want to install grub on your main boot disk, or install it on the other disk, then switch back and forth in the bios?

I also need to know how linux sees all these disks.  Please paste the results of sudo fdisk -l

---

### Post by johnbick on 2007-04-25
Ideally I would like to have GRUB come up automatically and give me a choice between Kubuntu and Vista. (Perfection would also include the ability to have the Windows memory test on that list of choices but that may be pushing the envelope!) If this can work by changing the disk in the BIOS that would be fine -- and would give me the ability to "go back" if necessary. I would settle, in the short term, for a solution thet would reqire me to make a BIOS change to do the switch, but that really would not be a desirable long term solution. 

The FDISK Listing that you asked for follows. Please note that Kubuntu is actually running off my DVD (and I am using Konqueror to post this) since I cannot boot off the hard drive yet. Have not learned how to save to another device yet or I would have put the file onto /dev/sdh2 and then included it as an attachment instead of this copy/paste.... 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      116739   937704448    6  FAT16

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38914   312568832    7  HPFS/NTFS

Disk /dev/sdc: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       18241   146518016    7  HPFS/NTFS

Disk /dev/sdd: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       18241   146518016    7  HPFS/NTFS

Disk /dev/sde: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       38914   312568832    7  HPFS/NTFS

Disk /dev/sdf: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1      116739   937704448    6  FAT16

Disk /dev/sdg: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       38914   312568832    7  HPFS/NTFS

Disk /dev/sdh: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1       10942    87891583+  83  Linux
/dev/sdh2           12112       14593    19936665    c  W95 FAT32 (LBA)
/dev/sdh3           10943       12111     9389992+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by psusi on 2007-04-26
Ok... the problem is that linux sees one of your 320 gig drives in the raid5 as /dev/sda, so that is where grub was installed.  Quite frankly, I am surprised that this did not totally hose up your raid5.  You should run a thorough checkdisk on that volume.  

You need to explain to grub that the boot disk is the 120 gig drive, so you need to edit /boot/grub/devices.map so that it shows that hd0 is /dev/sdh instead of /dev/sda.  Then reinstall grub.  

If you are running from the livecd, mount your linux partition.  For example:

sudo mount -t ext3 /dev/sdh1 /mnt

After that you should be able to chroot into the disk:

chroot /mnt

This will make a new shell that uses /mnt as the root of the filesystem, so it will behave as if it were actually running from the hard disk.  Now edit /boot/grub/devices.map, then run sudo update-grub, and that should take care of it.  Reboot and make sure your bios is set to boot from that 120 gig disk.

---

### Post by johnbick on 2007-04-30
Thanks for the quick reply and my apologies for the delay in responding here. I have been out of state. 

I cannot execute the chroot command as I "cannot change root directory to /mnt : operation not permitted". 

I tried editing (KATE) the displays.map and was able to access it. Unfortunately I am unable to save the change as the device is read only and I am not allowed to write to it. Obviously I could not "update grub" either.... 

I did all this using the Desktop (not alternate) install disk. 

Further thoughts????

---

### Post by psusi on 2007-04-30
Let's try this an easier way.  Start off with:

sudo -s

Then give the mount command and you should be able to edit /mnt/boot/devices.map.  Do that.  Then:

umount /mnt
grub
device (hd0) /dev/sdh
root (hd0,0)
setup (hd0)
exit
exit

Then you should be set.

---

### Post by mwiebelhaus on 2007-04-30
you deserver a bump because of all the info you entered and you have a big *** computer lol nice but i cant help you.

---

### Post by johnbick on 2007-05-01
After the sudo -s I issued the mount command and did a "mount l" to get a listing: 

root@ubuntu:~# mount l
mount: can't find l in /etc/fstab or /etc/mtab
root@ubuntu:~# mount -l
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
/dev/bus/usb on /proc/bus/usb type none (rw,bind)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sdh1 on /mnt type ext3 (rw) []
root@ubuntu:~#


I note that sdh1 is on /mnt and it indicated it is "rw". Since I have Kubuntu the "edit" does not work and I need to use KATE. Again, I am able to access /mnt/boot/grub/displays.map but I cannot save it. I get the message "Document cannot be saved as it was not possible to write to file ///mnt/boot/grub/devices.map -- Check that you have write access to the file or that enough disk space is available."

How to save that file....???

---

### Post by psusi on 2007-05-01
From the command line do nano /mnt/boot/grub/devices.map

---

### Post by johnbick on 2007-05-01
OK, i was able to edit the device.map and save it and then execute all the other steps as you described. 

I then changed my boot drive to that 120GB drive (sdh) and re-booted. Got into grub just fine. (We're making progress here!) Saw several choices on the screen -- a couple for ubuntu, one for a memory test and two for Vista. Took the default at the top and got "Error 21 - Selected disk does not exist". Same error if I try the ubuntu "safe" option. 

I opened that first entry for edit. It contains the following (a manual transcription): 

   root (hd7,0)
   kernal .boot/vmlinuz-2.6.20-15-generic root=uuid 5d258020-56da-49ba- ->
   initrd /boot/initrd.img-2.6.20-15-generic
   quiet
   savedefault

I also looked at the entries for Vista (both fail with reference to "no boot manager") and noted that the first points to root (hd2,0) and the second to root (hd3,0). I did not try to write down all the other entries there but they are very different and involve remapping the root drive and hd0. (Will worry about that later, let's get kubuntu working first!) 

I really appreciate your help on this.... When I get it working I will boil down these steps into a single entry in summary for everyone else to use....

---

### Post by psusi on 2007-05-01
Ok, we need to figure out how the bios sees your disks then.  When you get to that grub prompt, edit the line and change the hd7 part.  Try hd6, then 5, and so on down to 1.  Just edit the line, then press B to try and boot with the modified command.

---

### Post by johnbick on 2007-05-01
My thinking as well.... I had already started that process!

Turns out that kubuntu starts to boot when I use root (hd0,0)... And Vista boots when I change the first line of that entry to root (hd1,0). In BOTH cases I have left all other entries unchanged, but I am not at all sure that is the right thing to do with Vista given the subsequent map entries in grub. 

But back to kubuntu.... First question would be how to make that change permanent. I did not see any option to save the edited entry. Is that possible when actually in grub? 

Unfortunately, when the boot progresses my screen (a Samsung 206 BW) gets unreadable. Obviously the display parameters need to be changed. I may need to find a solution to that before I can fix grub! Thoughts on that???

---

### Post by psusi on 2007-05-01
Now you need to edit your devices.map so that hd1 points to the correct /dev device that windows is on, then sudo update-grub.

---

### Post by johnbick on 2007-05-01
Well I must say that Kubuntu has accomplished what no version of Windows, DOS 9either one), VM, MVS and a number of other systems has not -- I am totally humiliated. 

Edit device.map so HD1 points to the correct device, then run sudo update-grub.

Any way I try that I end up with exactly the same thing on my 120 GB MBR. I tried it the second way you described, then the first way, and it remains the same. At one pont it appeared to add a one block FAT16 disk into the mix in front og the "sdg" disk above (changing the 120 GB disk to "sdj", but that disappeared after I booted into Vista and has not (yet) returned. 

How do I change the "root (hd7,0)" (first line) entry in Grub to be "root (hd0,0)"? 

FYI, at the moment the device.map has one entry for hd0 /dev/sdh

It is so obvious that I am missing something here.... I do appreciate your patience.

---

### Post by psusi on 2007-05-02
Huh?  You want to edit your /boot/grub/menu.lst to direct grub to boot from the correct hd number that worked for you manually changing it at boot time.

---

