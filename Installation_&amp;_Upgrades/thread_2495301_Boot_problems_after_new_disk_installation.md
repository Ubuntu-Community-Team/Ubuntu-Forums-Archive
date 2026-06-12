---
title: "Boot problems after new disk installation"
date: 2024-02-14
forum: Installation &amp; Upgrades
---

### Post by Pierre Dartigues on 2024-02-14
Greetings!
I have my harddisk replaced by a bigger one and the technician made an image of my old one and transferred it to the new one. After that action booting with the new drive presented a problem. After power on the initial boot menu pops up and I choose the first option: booting Ubuntu 22.04. Ubuntu starts booting but stays a long time in an intermittant screen an finally delivers a failure message: Failed to mount /mnt/wwn-0x5001480000000000
The new disk partitioning is equal to the old one. There are 5 partitions: sda1 = EFI, sda2 = Microsoft reserved, sda3 = basic data ntsf (for windows) sda4 = ext4 for Ubuntu and sda5 = ntsf diag.
For details see the boot journal that I attached.

Is there someone around who could tell me how to correct this problem? 

Thanks already for helping!
Best regards,
Pierre


[ATTACH]293409[/ATTACH]

---

### Post by MAFoElffen on 2024-02-14
Boot from an installer LiveUSB. From booted off it, use "Try". Post the contents of the /etc/fstab file, posted within CODE Tags.

---

### Post by Pierre Dartigues on 2024-02-14
Hallo [COLOR=#000000]MAFoElffen[/COLOR]


Thanks for reacting. I don't know how to use Try, gave it as a command in the terminal window but it 's not recognised as a command.
I copied fstab from /etc to my desktop and added te txt extension because I coud not attach it as it was, but I could after I added the txt extension. Is this correct ?
This fstab is from the new harddisk.


[ATTACH]293411[/ATTACH]

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=683b62ad-6c3b-4e63-8ac9-554859d9f3a2 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=F410-B858  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
/dev/disk/by-id/usb-Generic_USB_CF_Reader_00000000000006-0:0 /mnt/usb-Generic_USB_CF_Reader_00000000000006-0:0 auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-id/usb-Generic_USB_SD_Reader_00000000000006-0:1-part1 /mnt/usb-Generic_USB_SD_Reader_00000000000006-0:1-part1 auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-id/usb-Seagate_Expansion_Desk_NA8ED40X-0:0-part1 /mnt/usb-Seagate_Expansion_Desk_NA8ED40X-0:0-part1 auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-id/wwn-0x5001480000000000 /mnt/wwn-0x5001480000000000 auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-id/usb-TOSHIBA_External_USB_3.0_20130121015073-0:0 /mnt/usb-TOSHIBA_External_USB_3.0_20130121015073-0:0 auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-id/usb-Generic_STORAGE_DEVICE_INIC186X20100625-0:0 /mnt/usb-Generic_STORAGE_DEVICE_INIC186X20100625-0:0 auto nosuid,nodev,nofail,x-gvfs-show 0 0


```

---

### Post by oldfred on 2024-02-14
For terminal output better to just copy & paste. If more than a couple of lines, use Code Tags which are easy to add using Forum's Go Advanced editor and # icon.

Ubuntu installer is both an installer & a repair flash drive. The try mode boots the live installer so you can use it to test if you like system or make repairs.  

Added your  fstab to your post. Not everyone is willing to download an unknown file.

If you do not have all the same devices plugged in, comment out incorrect entry in fstab.

If device not found, it has to either time out or fail either of which can cause issues.
Do you want all those devices always automounted?

---

### Post by Pierre Dartigues on 2024-02-14
Hi oldfred,
I am not shure if I understand what you are writing.

---

### Post by oldfred on 2024-02-14
More info on code tags.
How to use Code tags, # in Forum's advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)
[https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)

---

### Post by Pierre Dartigues on 2024-02-15
Hello folks, thanks for the information you sent to me. Unfortunately I am not capable of understanding and using it in order to repair my boot problems.
Does it mean that this problem is too complicated to be solved other than by an expert having physical access to my laptop?

Brgds, Pierre

---

### Post by yancek on 2024-02-15
Since you had a technician do this for you, have you considered contacting that person and explaining the problem?

If sda4 is the partition with your /etc/fstab file for Ubuntu, you could boot the Ubuntu install media and select the Try option when you see the Try and Install options.  Once you are booted into the live usb, you will need to mount sda4 and access the file /etc/fstab using a text editor and comment out all the lines below the line /swapfile.  You can do this by putting the character # at the beginning of the line.  Save the change and try to reboot.  If all those drives/partitions are not available on boot it will fail or take a very long time to boot.  If you don't know how to mount partitions just do an online search 'how to mount a linux partition from a live usb' or something similar.  You will get thousands of sites with explanations.  The link below shows an image of what you should see for the Try and Install options.

[https://ubuntu.com/tutorials/install-ubuntu-desktop#4-boot-from-usb-flash-drive](https://ubuntu.com/tutorials/install-ubuntu-desktop#4-boot-from-usb-flash-drive)

In your initial post, you indicate Ubuntu is on sda4.  Where did you get this information as the fstab file you posted shows it is on sda5.  If you are able to access the Try option on the Ubuntu usb, you should open a terminal and run the command:  sudo parted -l (that's a lower case Letter L in the command) and post the output to see which partition is correct.  You might as well run:  sudo blkid and post that output here as it will show the UUID for all partitions.  These commands provide information and won't 'fix' or change anything.

---

### Post by Pierre Dartigues on 2024-02-16
The technician who changed the drive was not entirely sure about Ubuntu. He does know little about Ubuntu. One solution might be replacing the new disk by the old one, but that is of course not what I want to do....

---

### Post by Pierre Dartigues on 2024-02-16
This is what I did until now in order to correct the problem: 
-Starting up from a USB-stick with the ISO for Ubuntu 23.10 as Try, mounted the new drive, p4 and checked the fstab file on the new drive, commented out all entries below the line /swapfile. Then rebooted without the USB-stick. No change.
-Starting up from the old sdd, by USB port.
-Starting up from a USB-stick with the ISO for Ubuntu 23.10 as Try, checked all drives, tried to repair the Grub.
No change... 

I can however start up from mu old disk when I attach it to a USB port. That allows me to work with the laptop.
This is what I thought that I might do:
Installing UBUNTU 23.10 from the USB-stick to the new drive. Before changing the SSD I made a data-backup that I can safely restore to the new drive. The old drive can help to remind me of re-installing all programs that I had installed before. It's quite a bit of work but it would work, is it not? Is there a better way to restore the programs I used before?

---

### Post by Pierre Dartigues on 2024-02-16
I decided to hand my laptop in on monday at the workshop of an experienced Ubuntu engineer.... He'll know what to do. In the mean time I will be able to start my machine up from the old SSD and have access to all my data and applications.
What do I do with this thread now? Is it ok to close the thread? The problem is not solved yet.....

---

### Post by oldfred on 2024-02-16
From old install, you export a list of installed applications.
Then from new install you use that list to install all your apps. It will not reinstall anything that was already installed.
List is just a text file. Sometimes, particularly when upgrading, you may want to edit out old kernels or maybe other apps you do not want any more.

If you use synaptic, using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
sudo apt-get -y update
sudo apt-get dselect-upgrade
#IF you get this error:
dpkg: warning: package not in database
sudo apt-get install dselect
sudo dselect 
   -> Update
   -> Install

I include a export of the list of apps & sources (as I have added a couple of ppa) as part of my backup script file.
sources & ppa
cat /etc/apt/sources.list; for X in /etc/apt/sources.list.d/*; do echo; echo; echo "** $X:"; echo; cat $X; done


Some more info:
compare script  MAFoElffen
[https://ubuntuforums.org/showthread.php?t=2470869&page=2](https://ubuntuforums.org/showthread.php?t=2470869&page=2)
[https://unix.stackexchange.com/questions/3595/list-explicitly-installed-packages](https://unix.stackexchange.com/questions/3595/list-explicitly-installed-packages)
[https://askubuntu.com/questions/680392/how-to-get-the-list-of-installed-packages-without-dependencies](https://askubuntu.com/questions/680392/how-to-get-the-list-of-installed-packages-without-dependencies)

---

### Post by Pierre Dartigues on 2024-02-16
Thanks Oldfred, I read your message but I will for now wait what our village engineer will achieve next week. In the mean time I can use the laptop by starting up from the old ssd, connected by USB
Thanks a lot for your help.

---

### Post by yancek on 2024-02-16
In post 10 you indicate that you commented out some of the entries in the fstab file but make no mention of whether you ran the blkid command to verify on which partition your Ubuntu is actually installed.  Did you do that?  If the blkid command shows something different than your fstab file, it won't boot.  You didn't post the output of the parted -l command, did you run that to check what partitions you have?

Good luck with your engineer.

---

### Post by Pierre Dartigues on 2024-02-21
@yancek: I'm afreaid I did not very well understand what to do with the blkid command. And as I already decided to hand the laptop in at the workshop I left it there....
Today I received my laptop back from the repair shop. I am not shure how the engineer managed to repair my laptop, he told me that he wrote a new image from the old disk to the present disk and then managed to resize the windows- and the Ubuntu partitions. He also told he had to do some research in order to get everything booting again in the correct order.
Well, now that everything is working as it should, I can close this thread as being solved.
I thank all of you for the support !

---

