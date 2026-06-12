---
title: "[SOLVED] GRUB problems, no system can boot on dual boot system"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by Micke Witt on 2007-10-16
Hi!
I got the bright idear to test out Ubuntu 7.10 on my home computer yesterday. I have a Nvidia fakeraid with two 70 GB disks, RAID 0 and one SATA data disk 200 GB.
The raid is configured with two partitions, one with WinXP and the otherone I planned to use for Ubuntu.

So I downloaded the Live CD for AMB X64 and off I go!
The live CD booted fine, but could not recognize the RAID array, instead it just showed 3 disks (2 from the array and the datadisk). I read a bit and downloaded and installed DMRAID. I then ran gParted and after quite some time it came up with both the raid array, the two individual disks and well as the datadisk?
I then formatted the second partition (the one not running XP) on the raid array as ext3 as well as a swap patition. After commiting the changes, gParted crached.

I then decided to install on a partition on the data-disk instead. After partitioning the disk from the installation meny the Installer complained that the two raid-partitions had the same mount point?

I quit the installer and restarted on the live CD, avoided installing DMRAID and started the Installer. I partitioned the data-disk and installed Ubuntu, everything seemed fine.

After reboot GRUB flashes a second on the screen and then reports "error 21" and nothing happens. I can not boot any of the operating systems.

I then started on the XP install CD and went into the repair console. Using BOOTCFG I find the master boot record which according to BOOTCFG only contains one entry, my XP installation.

So now to my question:

How do I get rid of GRUB and get my XP installation back?

Im not that good at Linux, so please bear with me, I have not found anyone with the same problems on any of the searches I have done.

Best regards
/Micke

---

### Post by PmDematagoda on 2007-10-16
Try the fix MBR option of the XP install recovery console.

---

### Post by Micke Witt on 2007-10-16
> **PmDematagoda said:**
> Try the fix MBR option of the XP install recovery console.
Well the utility in the XP recovery console to fix the MBR states that it only supports X86, not X64, so I did not dare to use it.
As far as I could see the MBR was ok from Windows point of view, the GRUB installer seems to load "before" the MBR is read, but I might be missing something...

The only thing I came up with so far is that the Ubuntu installer seems to write GRUB default to the first partition on the first disk it finds, unfortunatelly for me, that is one of the disks in my RAID-array, which GRUB does not seem to understand.

/Micke

---

### Post by SLK on 2007-10-16
That is easy to fix...As said above, just use the XP CD and choose to repair Windows when asked which action you would like to take on the XP setup menu...

---

### Post by SLK on 2007-10-16
There is a Windows command called fixmbr when you get into the console repair window

---

### Post by PmDematagoda on 2007-10-16
Where is the XP MBR located, can't you make the BIOS boot from there?

---

### Post by Micke Witt on 2007-10-16
Ok, thanks for the replies.
Well, checking the MBR from the repair console just shows me the windows operating system and it look ok as far as BOOTCFG can tell. To be able to get to the Nvidia fakeraid I have to load special drivers during the XP-install boot, and my uneducated guess was that this is the basis of the problem, grub does not understand my RAID-array and are pointing to the wrong disk.

The MBR is located on the striped RAID-array I guess, but which physical disk that is, I dont know.
I did a complete repair of the windows installation without any luck, still the 
"error 21" which seems to be that grup can not find the correct disk.

My new approach is right now to use the "Super Grub Disk" just to be able to get rid of grub and get the WindowsXP install up and running, but Im not sure its going to work considering the RAID config...
/Micke

---

### Post by Micke Witt on 2007-10-16
UPDATE!
Just ran some grub commands from the live-cd and this is what i get:

"ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd2,1)
grub> "

Im not realy sure what disk and partition that is indicated by (hd2,1), but gParted identifies three disks, dev/sda, dev/sdb and dev/sdc. dev/sda & dev/sdb is the disks in my RAID-array and dev/sdc is the disk where I installed Ubuntu.

dev/sdc hold three partitions, dev/sdc1 which is NTFS (datadisk), dev/sdc2 which is ext3 whith Ubuntu and dev/sdc3 which is Swap.

Dont know if this helps, but anyway...
/Micke

---

### Post by Micke Witt on 2007-10-17
Problem solved, or sort of anyway. Downloaded and used "Super GRUB disk" and managed to repair the windows MBR and uninstall GRUB.

Windows installation now works fine, but I could not fix the Ubuntu installation. Maby try in the future, but probably on another computer....:-).
/Micke

---

### Post by SLK on 2007-10-17
Hi Micke...Good to know that you fixed the Windows bootup...Shame you (and me as well) couldn't get to run Ubuntu due to this mystrious error 21 on grub on a raid system...

See I have 2 raid arrays and I followed the fakeraidHowTo guide however grub complains during boot up with ERROR 21: It seems to me that Grub can't find where the root (for stage2 file to load) resides, i.e. on which drives...Grub probably can't see the raid array device and needs a driver at start up to recognise my 2nd array which is where I installed linux on...of course grub is installed on MBR of the first array...

I'm also lost as to how to get Grub to see the 2nd raid array where Grub thinks /boot is installed on (hd3,4) I assume hd3 is one of the two drives on the 2nd raid array...

---

### Post by Micke Witt on 2007-10-18
> **SLK said:**
> Hi Micke...Good to know that you fixed the Windows bootup...Shame you (and me as well) couldn't get to run Ubuntu due to this mystrious error 21 on grub on a raid system...

See I have 2 raid arrays and I followed the fakeraidHowTo guide however grub complains during boot up with ERROR 21: It seems to me that Grub can't find where the root (for stage2 file to load) resides, i.e. on which drives...Grub probably can't see the raid array device and needs a driver at start up to recognise my 2nd array which is where I installed linux on...of course grub is installed on MBR of the first array...

I'm also lost as to how to get Grub to see the 2nd raid array where Grub thinks /boot is installed on (hd3,4) I assume hd3 is one of the two drives on the 2nd raid array...

Yeah I know that "solved" was a bit of a strong word to use, but I just had to get my WinXP up and running, wife has forbidden more experimentation with our "production machine":-). Have installed Ubuntu on a separate system for now, so I can play anyway:-)).

Try the Super GRUB disk, it might work out for you, its an amasing tool (at least for a newbie like me). I discovered that I had a slight bios problem that might have made things worse, but even after fixing that I could not boot Ubuntu.

Good luck!
/Micke

---

### Post by theproc64 on 2007-11-20
I have a related problem.  I am dual booting Ubuntu 7.10 and winxp and decided to try to install Ubuntu on an external hard drive and now when I try to start my normal system up without the external hard drive plugged in Grub doesn't load and says error 21.  If I have the drive plugged in Grub loads and I can boot from my computer os.  I'm guessing that Grub's trying to load from the external.  Can anyone help?

---

### Post by theproc64 on 2007-11-22
I solved my own problem.  Just had to follow directions to reinstall grub from the forums.

---

### Post by theproc64 on 2007-11-22
followed directions similar to these [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

