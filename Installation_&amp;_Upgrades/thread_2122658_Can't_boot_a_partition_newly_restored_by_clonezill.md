---
title: "Can't boot a partition newly restored by clonezilla"
date: 2013-03-05
forum: Installation &amp; Upgrades
---

### Post by Ralph L on 2013-03-05
I am trying to create backups for my CONFIGURED 12.04 disk partition.  In the past I have done updates, which damaged my OS.  It takes me considerable time to do a clean install and configure everything the way I want it, so I don't like to do it every time something messes up an OS partition.  I don't know if clonezilla cloning is the best answer, but that is what I am trying to use. (Would something like LuckyBackup, which I use to backup my data partition, also work for backing up my configured OS partition?).  I have successfully cloned my configured and working sda11 partition, and have done a clonezilla restore partition to my sda12 partition, which formerly contained a trashed 12.04 OS.  

I used the instructions at [http://drbl.org/faq/fine-print.php?path=./2_System/102_restore_image_to_different_partition.faq#102_restore_image_to_different_partition.faq](http://drbl.org/faq/fine-print.php?path=./2_System/102_restore_image_to_different_partition.faq#102_restore_image_to_different_partition.faq) , and at [http://www.sudo-juice.com/how-to-change-the-uuid-of-a-linux-partition/](http://www.sudo-juice.com/how-to-change-the-uuid-of-a-linux-partition/) to allow the sda11 clone to be restored on sda12.  However, I can't boot the newly restored sda12 partition.  I want to be able to restore to a different partition so that I can do a restore without completely destroying a partially working OS partition (partially working is better than nothing).  When I attempt to boot sda12 from the grub boot menu, I get an error immediately saying something to the effect that it can't find the necessary files.  Booting from sda11 still works fine.

I noticed that the grub boot menu entry hasn't changed, since I did the partition restore to sda12.  It still has the old partition UUID and several recovery entries, which of course are no longer there.  So I think it is still trying to boot the old, now non-existant, files.  I rebooted in sda11, which is the default partition at the top of the menu, and did:
```
sudo update-grub
```  However, this did not update the menu entry for sda12, so I still can't boot it.  I looked at sda11>grub.cfg and noted that sda12 entries there HAD been updated with the correct UUID, but this wasn't reflected in the grub boot menu.  Since I can't boot sda12, I can't do a "update-grub" on the sda12>grub.cfg.

1.  My first question is, on a many OS partition disk, which of the many grub.cfg files is used to build the grub boot menu?  I had thought it was the one that was last updated with "update-grub", but apparently I was wrong.

2.  How are the /etc/grub.d (and the other .d including init.d) folder/files used.  Apparently something searches through them and executes the instructions in them.  What program does this and how is it initiated?

3.  What do the programs initrd and update-rc.d do?  Both seem to be involved in some form of booting or initialization.

4.  When does one put options in /etc/default/grub, and when in /etc/grub.d?

5.  And finally, what can I do to make the sda12 restored partition boot?

Any help appreciated.

---

### Post by presence1960 on 2013-03-05
You need to have GRUB on MBR look for sda12. Boot ubuntu Live CD/USB. When you get to desktop open a terminal and run ```
sudo mount /dev/sda12 /mnt
```
Next run ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot without Live CD and you should be good. Your previous install has GRUB pointing to sda11, this will have it point to sda12 for boot files needed to boot, provided the restore from the image went well. You have to realize Clonezilla copies the MBR when you create an image, so it restored the previous MBR which points to sda11, even though you forced it to install to sda12. It can only restore the image that it captured. Clonezilla works great, have been using it for years for both Linux and Windows OS partitions.

You may need to edit some files manually if this does not work. For future reference it is best practice to restore an image to same partition from which it was taken.

P.S. I may have misunderstood you. Are you telling me you have 12.04 on both sda11 & sda12? Why? Just restore the saved image of sda11 to sda11. Isn't that the purpose of the image. To restore a working OS? I don't understand why you would put the image on sda12. If the simple fixing of the MBR does not work you may have to jump through a few hoops to get this working.

---

### Post by Ralph L on 2013-03-06
Presence1960

Thank you very much for responding.  I need the help, since I obviously don't understand booting and grub.  

1.  You asked why I want to restore my clone of sda11 (an OS that is working well) to sda12.  My reason is that I want to install more stuff in sda11 and that my history of breaking an OS, when installing more stuff, has been very poor.  The next thing I want to install is support for my winmodem, so I can send faxes directly from my computer.  I have done this before, but it is tricky.  Because of this I want to have a fall-back working OS (sda12), so that in case I have problems, I can immediately reboot to sda12 and have a working system.  It just takes too long to re-install and configure a new system.  I can't do without a computer for that long.

2.  I need to study your suggestion for a fix a bit more, before I implement it.  I just want to make sure that I don't cause sda11 to not boot and still not have sda12 working correctly.  Then I would be without a computer.

Thank you again,
Ralph

---

### Post by justincarter on 2013-03-06
You need to have GRUB on MBR look for sda12. Boot ubuntu Live CD/USB. When you get to desktop open a terminal and run  	Code:

 	
sudo mount /dev/sda12 /mnt 
Next run  	Code:
 	
sudo grub-install --root-directory=/mnt/ /dev/sda

 This is the best solutions

---

### Post by Ralph L on 2013-03-06
Presence1960, justincarter

I followed your instructions--boot to ubuntu 12.04.1 cd, brought up Terminal and entered the two commands you suggested above.  It didn't fix anything.  But it didn't hurt anything either!!!  However, I still can't boot to sda12.  Also, I noticed in the boot menu that the wrong version  of linux was listed.  It was the same as the linux version that was on sda12 prior to the restore.  So the boot menu still was not updated.  How is the boot menu generated?  And from which of the many grub.cfg files?

Any help appreciated.

---

### Post by darkod on 2013-03-06
There is only one grub.cfg file on each partition. It uses the one on the partition "linked" to grub2 that is on the MBR. I'm not sure how clonezilla restores. Did yuo check the UUIDs of sda11 and sda12 whether they are the same?
sudo blkid

will list all UUIDs. You can't have two partitions with the same UUID, it should be unique.

If the UUIDs are different, you still might need to chroot into sda12 and update the initramfs after the restore.

EDIT PS. I forgot to mention, you will probably need to modify /etc/fstab on sda12 because it will contain the UUID of sda11 instead of sda12.

---

### Post by Ralph L on 2013-03-07
Well, I finally got the sda12 partition to work, or at least to boot.  I haven't used it that much, so I really don' t know that everything works, but so far so good.

The method I used to get it to boot was quite convoluted, and there must be a better way.  I booted to sda11, mounted sda12 using nautilus, and edited sda12>/boot/grub/grub.cfg.  I changed the first (main) entry for sda12 to have the new UUID for sda12 in 2 places, and changed the linux version number of linux in 2 places.  I didn't change the other entries for sda12.  The new main entry for sda12 looked like this:  
```
menuentry "Ubuntu, with Linux 3.2.0-37-generic-pae (on /dev/sda12)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos12)'
	search --no-floppy --fs-uuid --set=root 84c781de-f7dd-4b72-9ba3-cb962240315f
	linux /boot/vmlinuz-3.2.0-37-generic-pae root=UUID=84c781de-f7dd-4b72-9ba3-cb962240315f ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-37-generic-pae
}
```
I did not run "sudo update-grub".

I then restarted and was able to boot to first (the one I changed) sda12 in the boot menu.  After booting sda12 I ran "sudo update-grub" and rebooted.  Now sda12 was moved to the first item in the boot menu.  Previously sda11 had been the first entry in the boot menu.  It was moved to the 26th entry.  I then rebooted to sda11 and ran "sudo update-grub" there.  Now everything seemed ok.  I might also have been able to boot from sda12 by using the "e" option in the boot menu and changing the sda12 entry the same way I described above.

I think I partially answered one of my questions in the first post of this thread.  The grub boot menu is apparently assembled from all of grub.cfg files (one in each OS partition).  The first entry in the boot menu (with no sdaxx in it) is taken from the "primary" grub.cfg file.  It is apparently pointed to by something associated with the MBR.  However, the boot menu entries for each of the other OS partitions seem to come from the grub.cfg for that partition.  So rather than the boot menu being taken for one grub.cfg file, an entry is taken from each corresponding partition's grub.cfg file.

In addition, I found that only the /etc/default/grub for the "primary" (first in the boot menu) partition seems to matter.  With sda12 as the "primary" parition I change the sda11 "GRUB_DEFAULT=0" to "GRUB_DEFAULT=26", so the default boot would be from the 26th entry in the menu (sda11).  It had no effect.  So I changed the /etc/default/grub entry in the "primary" (first boot menu entry) sda12 to be "GRUB_DEFAULT=26".  This worked and now the default boot is to sda11 (the 26th entry).  Hence, my conclusion that only the /etc/default/grub file on the "primary" (first boot menu entry) partition matters.

If anybody can shed further light on how the boot process works, I would appreciate it.  I would also like to find a more direct way of resetting the boot menu after the clonezilla restore to a different partition than the one from which the clone was made.  There must be a command that does this.

Thanks
Ralph

---

### Post by darkod on 2013-03-07
No, there is only one grub.cfg that matters, the one in the "main" partition. But with many OSs you have to be sure you know which the "main" is from grub2 point of view (not yours).

I think that after restoring a partition you have to chroot into it and update the initramfs and grub. That would have probably done what you did manually.

With update-grub you only update the grub.cfg, you do not change the main partition for grub2. In order to make grub2 from a specific OS to be primary, you have to boot that OS and that run:
sudo grub-install /dev/sda

That will (re)install grub2 to the MBR and link it to the OS you ran the command from. So, that will be the "main" OS for grub2.

---

### Post by oldfred on 2013-03-07
Grub2's os-prober scans system for other bootable partitions. It primarily finds grub.cfg or menu.lst and converts those entries into its grub.cfg. So you have to run an sudo update-grub in other systems to get the current bootable to find updates.

But Debian based systems also put links to the most current kernel in the / of the system. So you can manually create and entry that boots the partition or linked entry which boots the most current kernel in that partition.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

I turn off os-prober and add my own entries to 40_custom. 

 From Ranch hand
You only need 3 scripts for grub to tick like a clock;
00_header
05_debian-theme
06_custom (or 07, 08, 09, 25, 40)

Examples:
I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.
At least for Ubuntu family OS's, they all place symlinks in /, called vmlinuz and initrd.img These point to the most recent versions of the kernel in the /boot folder.
More info:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

A menuentry like this should always use the latest entry:

menuentry "Latest Kernel in sda1" {
insmod ext2
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
}
Just take your existing entry and remove the specific info from the end of the "vmlinuz" and "initrd" entries.

---

### Post by Ralph L on 2013-03-08
Darkod and Old Fred

Thank you again for responding.  You say that only the main grub.cfg file matters.  First, how do I know what is the main partition that contains the main grub.cfg file.  I had thought that it was the first entry in the grub boot menu.  Am I incorrect in this assumption???  

In my case sda11 was the first entry in the grub boot menu so I am assuming that it is the main partition.  After the clonezilla restore partition to sda12 and doing an update-grub on sda11, I examined sda11>grub.cfg.   It HAD the correct entries for booting from sda12.  However, when I restarted the computer, the grub boot menu DID NOT have the correct entries from the sda11>grub.cfg for booting sda12.  This made me think that the grub boot menu was NOT completely constructed from sda11>grub.cfg.

At that point I restarted sda11, mounted sda12, and edited sda12>grub.cfg to have the correct entries.  I did NOT run update-grub at that point.  Yet, when I restarted the computer, the boot menu entries for sda12 were now correct and showed exactly the edits I had made to sda12>grub.cfg.  Note that the edits I made to sda12>grub.cfg were NOT exactly the same as those that existed in sda11>grub.cfg.  I cannot explain how the sda12 boot menu entries could have been exactly my edits unless the boot menu were generated on the fly from the sda12>grub.cfg (as well as from the sda11>grub.cfg).  Can you explain how this could have happened if the boot menu were generated only from the sda11>grub.cfg, which had different sda12 entries in it?  I would really like to understand this, since I have other more severe boot problems with my other computer (Compaq Presario 2100) and I will need a deep understanding of grub to solve them.

Thanks again,
Ralph

---

### Post by darkod on 2013-03-08
Yes, if you don't customize the grub scripts to change the order, the top linux version is the main one.

I can't explain what you are saying about grub.cfg, it doesn't make much sense. If sda11 is your top version, then only the grub.cfg on sda11 should matter. When you run update-grub the os-prober does search for boot files of other OSs and makes an automatic entry for each found. All these entries go below the memory test entry in the boot menu (by default, unless customized).

update-grub usually does a very good job and that's why editing manually grub.cfg is not recommended. You can do it for troubleshooting purposes, but carefully. If you are not 100% sure your grub2 on the MBR is from sda11, you can try booting sda11 and running:
sudo grub-install /dev/sda

That will install it linking it to sda11.

We haven't addressed one important question, the UUIDs. Did you confirm you have no doubled UUIDs for the recovered partition? As I said, I don't know exactly how clonezilla does it. Have in mind that it's not designed to restore on the same disk next to the original partition. If the clonezilla restore uses the original UUID, that would mean you can end up with same UUID for two different partitions which will create confusion for both /etc/fstab and grub.cfg. Check the UUIDs with blkid and make sure sda11 and sda12 have different one.

---

### Post by Ralph L on 2013-03-08
darkod

Thank you again for your reply.  You are correct about only the "main" grub.cfg being used for the boot menu.  I think I see what happened to me.  When I did the clonezilla restore partition on sda12, the sda12 partition looked exactly like the sda11 partition.  The MBR must find the "main" partition by searching for a certain symbol (reference by symbol).  Because I had two exactly the same partitions (with the same symbols), it must have found the symbol in sda12, and not looked any further, it built the menu from the sda12 grub.cfg.  However, when I booted, since both partitions pointed to sda11, I always booted sda11.  Then when I did update-grub for sda11, I wasn't updating the grub.cfg file that was being used for the boot.  When I changed the sda12>grub.cfg to have the correct entry for booting sda12, booted sda12, and did update-grub, I finally updated the grub.cfg that was being used all along, and everything worked fine.

Oh, and I did have to change fstab in sda12 to have the correct UUID.  So I now have a backup OS partition that I don't have to spend hours reconfiguring, if I mess up my daily use OS partition.

So I thank you very much for educating me.  I am sure it will be very useful to me in the future, when I start chasing the boot problems on my Compaq Presario 2100.  Hopefully you will be on-line and give me some advice on those issues also.

PS:  I tried to support your Ubuntu membership, but the thread was closed.  Good luck.

---

### Post by darkod on 2013-03-08
If you are in doubt sometimes which partition is mounted as /, you can check all mounted partitions in terminal with:
df -h

That will show what is mounted as / so you don't need to guess. Glad you got it figured out. :)

Don't worry about the membership application, I already got the membership and that's why they closed the thread. Thanks anyway.

---

### Post by Ralph L on 2013-03-11
See [http://ubuntuforums.org/showthread.php?t=2124458](http://ubuntuforums.org/showthread.php?t=2124458) for detailed solution.

---

### Post by justincarter on 2013-03-12
Hey your problem have been solved or not ?

---

### Post by justincarter on 2013-03-12
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

A menuentry like this should always use the latest entry:

menuentry "Latest Kernel in sda1" {
insmod ext2
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
}  It works .

---

