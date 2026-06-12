---
title: "How to restore Ubuntu OS to a different partition using Clonezilla"
date: 2013-03-11
forum: Installation &amp; Upgrades
---

### Post by Ralph L on 2013-03-11
On my laptop I have multiple operating system (OS) partitions and one data partition.  The OS's include a Windows partition and multiple Ubuntu partitions of various types and vintage.  Recently I have trashed my main OS (Precise Pangolin 12.04.1) several times by doing updates or installing new programs.  Because it takes me considerable time to re-customize the system, I decided to backup my OS including my customizations.  (I have always backed up my data partition using LuckyBackup.)  I wanted to be able to  have a duplicate of my main OS in another partition, both to prove that I could do a restore and to have it ready,  when I next trashed my main OS.  It took me some experimenting to achieve this so I thought I would write it up.  I chose Clonezilla as the backup/restore tool.  Clonezilla clones the OS exactly.  See [http://clonezilla.org/](http://clonezilla.org/) .

1. Downloaded clonezilla-live-2.0.1-15-i486.iso from [http://clonezilla.org/downloads.php](http://clonezilla.org/downloads.php) ..  
2. Used Basero to burn an iso image to a cd.  
3. Created a folder at the first level on my USB backup disk called “osbackup”  Note that clonezilla will look only for first level folders without any spaces in the name.
4. Booted from the clonezilla cd.  I used all the default settings (press Enter) up to the point it asked for the repository.
5. When asked for the repository, I plugged in my USB disk, waited for it to be recognized, and waited for clonezilla to list all disks and partitions on my computer.
6. Picked “sdb2” as the repository location—the USB disk partition on which I had create "osbackup" folder.
7. Selected “osbackup” as the first level folder to contain the cloned image.  Note that on backup clonezilla just writes an ordinary folder with several files in it as the cloned image.  It does not write boot records or do anything special to the repository disk.  Of course on a "restore partition" it overwrites everything on the partition being restored.
8. Selected “Beginner's Mode”.
9. Select the second item “saveparts  Save local Partition to an image”.
10. Input the file name for the saved image.  In my case it was “clonesda11_1”.
11. Waited for clonezilla to to display all disks/partitions to allow selecting the source.  In my case it was sda11.  This partition contained my current OS.  Selected it by pushing the space bar, then Enter.  
12. Skipped checking/repairing partition.
13. Checked to make sure I wasn't overwriting the wrong stuff, and started creating the cloned image folder.

I wanted to restore the cloned image to the sda12 partition, which contained an OS that I no longer wanted.  To do this I had to make modifications the sda11 image that I had just dumped.  This shows how:  [http://drbl.org/faq/fine-print.php?path=./2_System/102_restore_image_to_different_partition.faq#102_restore_image_to_different_partition.faq](http://drbl.org/faq/fine-print.php?path=./2_System/102_restore_image_to_different_partition.faq#102_restore_image_to_different_partition.faq) 

1. Duplicated “clonesda11_1” calling the new folder “clonesda11_1tosda12_1”.
2. In the folder “clonesda11_1tosda12_1” renamed all the files that are similar to “sda11.ext4-ptcl-img.gz.aa”, changing sda11 to sda12.  There should be one or more.  For example:
```
“sda11.ext4-ptcl-img.gz.aa” to “sda12.ext4-ptcl-img.gz.aa”
“sda11.ext4-ctcl-img.gz.ab” to “sda12.ext4-ctcl-img.gz.ab”
```
3. Again in the folder “clonesda11_1tosda12_1” modified the content of the file “clonesda11_xtosda12_x”/parts, 
Replaced "sda11" with "sda12".
4. Rebooted from the clonezilla cd.
5. Selected default for all settings up to point where clonezilla asked for the disk/partition that contained the cloned image to be restored.  
6. Plugged in  my USB disk and selected sdb2, “osbackup” folder, and “clonesda11_1tosda12_1”.
7. Selected “restoreparts Restore an image to a local partition”.
8. Waited for clonezilla to list all the disks/partitions, and selected sda12.  Note that any data on sda12 will be completely destroyed so make sure you have the correct partition and that you don't want any of the data on it.  All my data is in a separate data partition (including firebox and thunderbird profiles), so I didn't care.
9. Started the restore operation.

Note that sda12 will now have a clone of sda11 including the partition UUID and the /etc/fstab UUID entry.  These must be changed.  I discovered that it was easiest to just restore the old UUID that sda12 had before the clonezilla restore.  See [http://www.sudo-juice.com/how-to-change-the-uuid-of-a-linux-partition/](http://www.sudo-juice.com/how-to-change-the-uuid-of-a-linux-partition/) . 

1. Restarted to the first (primary) partition on the grub boot menu.  This booted to sda11.  
2. Using nautilus I double clicked /boot/grub/grub.cfg and searched for sda12.  The menu entry showed the old UUID for sda12 so I copied it and pasted it into Terminal as the last parameter on this command (following the space after “U”), and executed the command:
```
sudo tune2fs /dev/sde5 -U 84c781de-f7dd-4b72-9ba3-cb962240315f
```
3. Under Terminal I entered “sudo nautilus” to launch nautilus with root privledge.
4. Mounted sda12 with nautilus.
5. Double clicked sda12>/etc/fstab bring it up in gedit.
6. For the disk/partition that contained “/” (usually the first entry in fstab), pasted the old sda12 UUID over the restored one.
7. Saved the modified fstab.
8. Under Terminal ran “sudo update-grub”.  I don't know if this was necessary, but it updates the sda11>grub.cfg file.
9. Restarted the computer.
10. At the boot menu selected sda12 and pressed “e” to edit the following two lines in the entry.  
```
linux /boot/vmlinuz-3.2.0-37-generic-pae root=UUID=23bc8f0e-3e4c-4911-8d42-af8106b22ec7 ro quiet splash $vt_handoff
and
initrd /boot/initrd.img-3.2.0-37-generic-pae
```
11. Changed the version number in both commands to “3.2.0-38”, because sda11 had been updated, and the old sda12 had not been updated.  You may not need to make any changes.  Note that by using the old UUID for sda12, it was not necessary to type in a new (and difficult to type) UUID.
12. Pressed F10 and booted sda12.
13. Ran “sudo update-grub” to update sda12>grub.cfg.  In my case sda12 became the primary partition at the top of the boot menu.  Hence sda12>grub.cfg was now used to build the boot menu.  All partitions including both sda11 and sda12 should now boot correctly.

---

### Post by presence1960 on 2013-03-11
Nice Ralph! I have been using Clonezilla for years and love it. However I never restored an image to a different partition. This is great to know and have bookmarked this for future reference. Thanks for sharing the solution as I am sure someone will need the same info one day.

---

