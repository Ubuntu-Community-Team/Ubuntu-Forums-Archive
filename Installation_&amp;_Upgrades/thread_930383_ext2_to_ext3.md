---
title: "ext2 to ext3"
date: 2008-09-26
forum: Installation &amp; Upgrades
---

### Post by nbakewell on 2008-09-26
I was just installing Ubuntu and I came across the error at 94% complete - "Unable to install GRUB.."  After reading through the forums, I solved the problem by formatting to ext2 during the install instead of ext3.  The thread said to then change to ext3 after the install, but after searching Google I can't figure out how to do this - any help?  The only thing i've come across is changingb/etc/fstab:

```
/dev/hda1   /   ext2    defaults,errors=remount-ro 0       1
```

To ext3.

---

### Post by tommcd on 2008-09-26
You can convert ext2 to ext3. Read:
[http://www.linuxquestions.org/questions/linux-general-1/reformat-file-system-from-ext2-to-ext3-16490/](http://www.linuxquestions.org/questions/linux-general-1/reformat-file-system-from-ext2-to-ext3-16490/)
and the link in that thread:
[http://www.redhat.com/support/wpapers/redhat/ext3/](http://www.redhat.com/support/wpapers/redhat/ext3/)

Use ```
sudo tune2fs -j /dev/sda1
``` assuming /dev/sda1 is your Ubuntu partition. I think it would be best to do this from the Ubuntu live CD with the /root partition unmounted. Then mount the /root partition and edit /etc/fstab and change file system type from ext2 to ext3.

You will likely need a new initrd in your /boot directory as well. This may be the tricky part. To create it, do this from the live CD, just chroot into the Ubuntu root partition after it is mounted and do:
```
chroot /dev/sda1
sudo mv /boot/grub/ initrd.img-2.6.24-19-generic /boot/grub/ initrd.img-2.6.24-19-generic.bak (to back up your current initrd)
(then)
 sudo mkinitrd  -k 2.6.24.19-generic -m ext3 -f ext3 -r /dev/sda1 (if your kernel is different change accordingly. Find your kernel with "uname -r"
```

I have never done this myself. This is just from a quick google search. Also:
[http://www.troubleshooters.com/linux/ext2toext3.htm](http://www.troubleshooters.com/linux/ext2toext3.htm)
[http://www.togaware.com/linux/survivor/Ext2_Ext3.html](http://www.togaware.com/linux/survivor/Ext2_Ext3.html)
First, from the live CD, use tune2fs to change from ext2 to ext3, and change fstab. Then try to boot Ubuntu. If it won't boot then you will need to make a new initrd as described.

I don't know why ext3 would not let you install grub but ext2 did. That seems odd.

---

### Post by prshah on 2008-09-26
> **nbakewell said:**
> 
The thread said to then change to ext3 after the install, but after searching Google I can't figure out how to do this - any help?  The only thing i've come across is changingb/etc/fstab:
```
/dev/hda1   /   ext2    defaults,errors=remount-ro 0       1
```
To ext3.

AT YOUR OWN RISK. Sorry.

You have to do a bit more than that. Fortunately, ext2->ext3 is quite easy and painless. Just involves adding a journal.

Boot off a live CD. Unmount your ext2 partition if it is mounted. ```
sudo umount /dev/hda1
sudo tune2fs -j /dev/hda1
sudo mount /dev/hda1 /mnt -o defaults,rw
sudo nano /mnt/etc/fstab
#change ext2 to ext3, press Ctrl+X to exit, confirm save and filename when asked.
sudo umount /mnt
sudo shutdown -r now

```

When you reboot, your system should be using ext3. Confirm with ```
sudo fdisk -l
```

EDIT: When perusing the man for tune2fs, I came across this> On  some distributions, such as Debian, if an initial ramdisk is
              used, the initrd scripts will automatically convert an ext2 root
              filesystem  to  ext3  if  the /etc/fstab file specifies the ext3
              filesystem for the root filesystem in order to  avoid  requiring
              the  use  of  a rescue floppy to add an ext3 journal to the root
              filesystem.


I don't know how far it's applicable here. You may want to try just changing the ext2 to ext3 in the fstab file and rebooting, as you had originally planned.

---

### Post by kerry_s on 2008-09-26
ext2 is just as good and a bit faster than ext3.
i'm using ext2 on my install.

---

### Post by tommcd on 2008-09-26
> **prshah said:**
> 
EDIT: When perusing the man for tune2fs, I came across this

I don't know how far it's applicable here. You may want to try just changing the ext2 to ext3 in the fstab file and rebooting, as you had originally planned.

Thanks for that Prshah. I wasn't sure if he would need a new initrd or not.

---

### Post by nbakewell on 2008-09-26
Ok thanks everyone.  Out of curiosity, is there any reason why I have to have my partition formatted as ext3?  Is it just because it's newer and supposedly better?  So far everything seems to be working just fine on ext2.

---

### Post by prshah on 2008-09-26
> **nbakewell said:**
> Ok thanks everyone.  Out of curiosity, is there any reason why I have to have my partition formatted as ext3?  Is it just because it's newer and supposedly better?  So far everything seems to be working just fine on ext2.

ext3 has file journalling support. Essentially, that means that any files written to the hard disk are written twice; once to the journal, and then once to the hard disk drive, then deleted from the journal. This way, if the computer is interrupted during the writing job, then usually, on the restart, it will recover the missing entries from the journal, and restore your hard disk drive to a pristine state without a need for a full checkup and minimizing data loss.

Though this sounds much slower (multiple disk accesses) it is not really so, since we do a whole bunch more reading than writing. NTFS is also a journaling file system.

ext2 is slightly, marginally faster, but if you ever have an unclean shutdown on ext2, it's a very scary experience. On restart, the file system is checked, and, more often than not, fsck requires manual intervention to sort the problem. [It's not a very nice experience]("http://ubuntuforums.org/showpost.php?p=5723971&postcount=5").

Bottom line: Stick with ext3.

---

### Post by bcschmerker on 2008-09-26
> **prshah said:**
> ext3 has file journalling support. Essentially, that means that any files written to the hard disk are written twice; once to the journal, and then once to the hard disk drive, then deleted from the journal. This way, if the computer is interrupted during the writing job, then usually, on the restart, it will recover the missing entries from the journal, and restore your hard disk drive to a pristine state without a need for a full checkup and minimizing data loss.

Though this sounds much slower (multiple disk accesses) it is not really so, since we do a whole bunch more reading than writing. NTFS is also a journaling file system.

ext2 is slightly, marginally faster, but if you ever have an unclean shutdown on ext2, it's a very scary experience. On restart, the file system is checked, and, more often than not, fsck requires manual intervention to sort the problem. [It's not a very nice experience]("http://ubuntuforums.org/showpost.php?p=5723971&postcount=5").

Bottom line: Stick with ext3.

Already plan to, as part of rebuilding my Everex; I found that its 1.5GHz VIA MPU hasn't enough oomph to keep up with most Webpages.  I've plenty of experience with ext2 (from a decade-old Pentium MMX-based homebuild with Red Hat 6), and ext3 is a logical improvement thereon.

I found Advanced Micro Devices to be a one-vendor source for critical components for my planned "Hod Rod gPC,", so plans are now frozen at an Athlon or Phenom MPU, appropriate system board, and ATI Radeon-based 8X AGP or x16 PCI Express videocard.  And, I might as well do a clean 8.0.4 install while I'm at it, as gOS (based on Ubuntu 7.10) won't upgrade very cleanly.

(Bummer that I need a new eMachines/Gateway running MS-Windows Vista to document the Hot Rod gPC project for a YouTube miniseries; I found no Object files (viz., Modules) available in LinUX Kernel 2.6.22-18 for my Emprex G40 webcam.  Besides, Yahoo! Bix is rather Internet Explorer-centric at present....)

Update:  Make that a clean Ubuntu 8.0.10 install, assuming that the new hardware scheduled for the Everex will run it.  And, yes, ext3 is still planned.

---

