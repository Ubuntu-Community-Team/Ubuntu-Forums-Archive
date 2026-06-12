---
title: "Ubuntu and Windows 8 dual boot on HP Pavilion G7 - Locked-ESP detected error"
date: 2013-02-04
forum: Installation &amp; Upgrades
---

### Post by antsys on 2013-02-04
Hello,

This may help if you bump into this problem.

When installing Ubuntu 12.10 on a HP Pavilion g7-2242sf, I had this error.

```

An error occurred during the repair.

Locked-ESP detected. You may want to retry after creating a /boot/efi partition (FAT32, 100MB~250MB, start of the disk, boot flag). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot/efi partition:] option of [Boot Repair].
```************
Quick answer and work around : the problem is not that the partition is locked, the problem comes from the grubx64.efi file that is corrupted in the the EFI partition, at place /EFI/ubuntu/grubx64.efi.

Just suppress this file, then make a Boot Repair reparation : the whole repair should then be a success, and the dual boot should work.
(if you don't know how to suppress this file, see here after, the explanation).

************
More explanation.

I installed the Ubuntu 12.10 version with the "other way" option, with reduction of the Windows8 partition, and creation by hand the Ubuntu partition and the Swap partition.

All goes fine, ... but no boot on Grub, to choose between Ubuntu or Windows.
Windows starts directly.

So I tried the BootRepair, as explained nicely here : 
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

To do that, I stated  Ubuntu from the installation USB Key, and the installed the BootRepair, as explained in the internet page of Boot Repair :
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Just copy and past the two given lines in a Terminal window, and you can use Boot Repair with the LiveUbuntu from the USB key.

But I got the error : "Locked-ESP detected. You may want to retry after creating a /boot/efi partition...."

It appear, after searching, reinstalling, looking closely at the boot files and so... that the grubx64.efi file was corrupted.

I guess that when Ubuntu tried to installed, there is a bug that makes this file not be properly set.
I have tried to install several times, with another EFI partition, etc... the problems comes when the EFI partition is made by Windows8 : then, the grubx64.efi file is not properly installed by Ubuntu.

Then, Boot Repair cannot rewrited or manipulated it, when doing the reparation with the Grub2 files etc...

So, the idea is to remove the corrupted file.

The trick is to make the EFI partition a simple usual partition, remove the file, then put it back to it's "boot" partition role.

To do so : 
 - boot with Ubuntu (live version, from the USB key), and use GParted to change the flag of the EFI partition : remove the boot flag.
 - shut down the pc, remove the USB key, and boot with windows 8 (the removal of the boot flag does not prevent windows to boot).
 - within windows 8, call the partition tool (search for "partition" in the control panel or in the parameters setting search tool). 
 - in the partition tool, select the EFI partition, and give it a Drive letter (you can do it because it is not anymore marked as a "boot" partition).
 - then open a File Navigator, and go to the Drive of the partition : you can see the EFI folder, and navigate down to the file :  /EFI/ubuntu/grubx64.efi
 - suppress the file.
 - shut down the computer
 - restart with Ubuntu (live version, from the USB key), and use GParted to change the flag of the EFI partition : set back the boot flag.
 - install the Boot Repair tool (see here above, and the link to the Boot Repair page).
 - proceed to the repair : choose your settings and option, etc...
 - the process should be sucessfull, and the Ubuntu Grub panel appear when starting.

then try first to boot with Ubuntu, and then shut down and try to boot with Windows 8.
It should work fine.

**SEE HERE UNDER the other post : this is incomplete**

There certainly other ways to do this file delete, but this one was the one I did when trial and error... 
You can also mount the EFI partition within Linux and make the delete from there...

Hope it helps,
Antoine Herzog

---

### Post by oldfred on 2013-02-04
I am surprised Windows will boot with efi boot flag off, but if it does that is good. 

Please report your work around in the bug report on locked efi partition. The developers can review and confirm and then fix grub install procedure.

       grub-efi fails to install with Input/output error - locked efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)
Some find chkdsk on efi partition helps, others backup, reformat and restore as current work arounds.

---

### Post by antsys on 2013-02-04
> **oldfred said:**
> I am surprised Windows will boot with efi boot flag off, but if it does that is good. 


Yes !
You're right... and I did something else.
When I read you post, I realized what happened, more precisely, when I struggled to have it work.
Sorry to had it only know, but I wrote the post by memory, andI though this was not important.

In the process, I made some room for a small partition (between the windows8 one, and the Ubuntu one), and created a EFI partition (FAT32), ... and set the flag "boot" to it.

and when I restarted the computer to go to windows, ... It started some HP recovery. 
It was not very long, ... and in fact, it did the repair of the EFI partition (that was empty at startup).

So the "second" EFI partition was set with some starter for windows : I saw it when using the BIOS feature to choose the EFI booting system (F9 at boot, makes you enter in the "boot choice").  There are two EFI booting elements, and the second has only the windows8 files.

I did not mentionned it because I thought this second partition, for temporary EFI, was not used, and not usefull.
Know, this partition has only 3.56 Mo of data, and only a starter file for Windows8 (without the starter files for the HP recovery, nor the Ubuntu,...).

******** the best way is the work around given in the Bug report
Well, after reading the Bug report, I did by experimentation what they propose as the workaround.
The given workaround is more simple.

I will give some other info in the bug report...

Hope it helps,
Antoine.

---

### Post by oldfred on 2013-02-04
Thanks for the update.

---

### Post by tvkas on 2013-02-12
The method listed here worked for me. I tried the simpler method listed above but was warned that to adjust partitions such that a new EFI partition within the first 100 Go (GB) would move my Windows 8 partition, which is 150 Go/(GB), and render it unbootable. So I came back to this method and did all but create a temporary partition as that was not needed. 

Prior to attempting this fix I had [http://paste.ubuntu.com/1641372](http://paste.ubuntu.com/1641372) and [http://paste.ubuntu.com/1641460](http://paste.ubuntu.com/1641460). After I have [http://paste.ubuntu.com/1641789](http://paste.ubuntu.com/1641789). 

BTW, I was able to boot up this morning into Ubuntu with no problems. After whatever updates I had were ran I rebooted the laptop "just because" and that is when it all stopped working. 

Thanks for listing this fix as it will work for those who like me cannot create a different EFI due to existing partitions.

---

### Post by forumname on 2013-06-20
This for the benefit of the internet! Skip to the bottom to skip the story and get to the steps I used to workaround this.

So,  I recently bought a new Dell Inspiron laptop which unfortunately came  pre-installed with Windows 8. After repartitioning, installing ubuntu  13.04, and running boot-repair I still could not get dual-boot up and  running. I had the problem described here, the "locked-esp" error after  running boot-repair. Not good. Disabling SecureBoot didn't help either.  There have been two solutions proposed thus far:

1) Re-partition the HDD again within the first 100GB (or 150GB?) and create a new ESP partition.

2) Follow the instructions outlined here, deleting the grubx64 file from the /EFI/ubuntu folder, etc.


However,  I could not (or at least didn't want to) re-partition my HDD as per  option 1. That would've required fiddling with the current Windows 8  partition. No good.

I tried to follow the instructions here, but I  found myself in a different situation. 

(Note: The actions in this  paragraph occur while running ubuntu from a Live USB) I first ran  gparted to remove the boot flag from the ESP partition that already  existed. Then I mounted that partition using the command "sudo mount  /dev/sda1 /home/myfolder" where myfolder was some random folder I created in  the home directory of the Live USB ubuntu. Upon navigating to the  /EFI/ubuntu folder I found that I couldn't open the folder! So at this  point, either the grubx64 file was stuck inside or something else had  gone wrong. Probably the latter I thought.

I thought I might be  able to remove the file from Windows. So I shutdown my laptop, removed  my USB, rebooted into Windows and ran the Disk Management tool. I gave  the ESP partition a driver letter then navigated to it using the windows  file explorer. This time I was able to open the folder, but there was  no grubx64 file! Just a zero byte, nameless file and also a 1.3MB (Might  have been 1.3GB) file named Locali.zd or something. I couldn't delete  the zero byte file (didn't try the other one) and running the DIR  command in a command prompt gave a weird error when inside the  /EFI/ubuntu directory. I then decided to run check disk on the ESP  partition (why not? I thought). After agreeing to a prompt assuring me  that a scan wasn't necessary (ha!) it scanned, said it was successful,  and I found the entire /EFI/ubuntu directory to be gone. "Now what?" I  thought. Well, after some thinking I decided to leave the ESP partition  as it was. That is, I left the boot flag UNCHECKED. However, I did  remove the drive letter using the windows Disk Management. Basically,  all I did after booting into Windows was delete the /EFI/ubuntu folder.

Now  booting back into my Live USB I decide to run boot-repair once again.  Leaving all recommended settings untouched. For the record, SecureBoot  was NOT selected, and the "Separate partition" for the GRUB installation  was checked and pointed to my ESP partition. Also, Purge GRUB was OFF. I  just did a reinstall. After running boot-repair it worked! I ran  gparted to set the boot flag back to ON for the ESP partition, rebooted  my laptop without the USB, and voila! GRUB was working and I could  successfully boot into both Ubuntu and Windows.



tl;dr

Steps I followed:

1) Use gparted from the Live USB to remove the boot flag from the ESP partition

2) Delete the /EFI/ebuntu folder by following the steps below. (Doing it from Ubuntu by mounting the ESP partition may or may not work)

2.1) Boot into windows w/o the Live USB/DVD plugged in.
2.2) Use windows Disk Management tool to give the ESP drive a drive letter.
2.3) Delete the ubuntu folder within the EFI folder. I used the Check Disk tool to do this, which may or may not be important.
2.4) Remove driver letter from ESP partition. Might not be necessary.
2.5) Reboot into the Live USB/CD. WITH THE BOOT FLAG STILL REMOVED FOR THE ESP PARTITION.

3)  Re-run boot-repair with SecureBoot OFF. The "Separate partition"  CHECKED and pointing to your ESP partition. Also, Purge GRUB was OFF.  Just did a reinstall.

4) Set boot flag to ON for the ESP partition after boot repair (hopefully) succeeds.

5) Rejoice!



Note: I am writing this right after my success. Who knows how long it will last?

---

