---
title: "Pre Re-Installation Partition Question"
date: 2013-06-16
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2013-06-16
The "restore" is putting things into the /home. As GParted told /dev/sda6 to be /home it must be working as well as possible.

Case Closed.

Thank you, Linux-Ubuntu Community Members.

========== divider =================

My OS blew up by using the dd command to copy DVD's. It put them in the /media folder. I have to re-install my system.

1 - I have a backup of my /home objects. That backup was made using the Ubuntu default package "Backup".

2 - The "Backup" of /home was from (originated in) /sda5.

3 - I want to make a clean re-installation of my /boot (which is /sda3).

4 - Two days ago, I made a clean re-installation, but did not understand which type of installation I was doing -sortof. So I believe I selected "Custom" and made the boot partition to be: /sda3 and formatted as ext2. But I did nothing to or with the /sda5 (/home) partition. As a result of not understanding what to do, with /sda5, the clean re-installation put the (empty) /home into /sda3 or /boot. When I ran the "Backup" restore, "Backup" populated /sda3. It populated it until I have 3% of free space on /sda3. I have decided to re-install the /sda3 (or /boot), to clean out the "Backup" mistake.

5 - DURING THE INSTALLATION process, I want to format and create /sda3 for Ubuntu's boot and system OS files. I want the installation to do nothing to the /home or /sda5 partition. But how do I mount it during an installation? That sounds counter-intuitive. If it's not going to be mounted during the installation, how will /sda3 find /sda5 and vice-versa? AND I apologize to you if I'm not making sense in this request for your help, but I cannot understand what I am trying to ask in a way I can put into words.

---

### Post by fantab on 2013-06-16
Does your '/home' on /dev/sda5 still has all the data from previous Ubuntu install?

If the DATA on it is intact then:
** You can REUSE it with your new install. During Installation after you have chosen 'custom'/'Something Else' option, select /dev/sda5 (previous /home) and just Mountpoint=/home. Do NOT format the partition. Thats it.
If you want to remove the application settings from the previous Ubuntu then:
Boot Ubuntu Install Disk and 'Try Ubuntu without installing'. From the desktop/launcher choose the /home partition or /dev/sda5. you have to click on it to mount it. Then in the 'File Browser', Nautilus hit Ctrl+H to reveal dot folders (.folder) and delete them. Dotfolders are hidden folders you have to reveal them with ctrl+H.

If you don't want to reuse it then:
During Installation after you have chosen 'custom'/'Something Else'  option, select /dev/sda5 (previous /home) and select Mountpoint=/home, USE AS=ext4 and select to format.
Then restore data from Backup after installing Ubuntu.

During install when we don't specify /home partition our Home folder gets created in '/' partition. That is why when you ran backup it populated your '/' Home and not the /home partition. /home partition never existed for your new install.

---

### Post by Mark_in_Hollywood on 2013-06-17
I had several problems with the re-installation. I have re-formatted the hard drive:

mark@Lexington:~$ df -h

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        19G  4.6G   13G  27% /
udev            2.0G   12K  2.0G   1% /dev
tmpfs           805M  952K  805M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  2.1M  2.0G   1% /run/shm
/dev/sda6       342G  312M  324G   1% /home

I set /dev/sda6 to /home 

How do I use the default (formerly Deja-Dup) "Backup" to restore the objects it backed up into /dev/sda6?

---

### Post by cincinnatus13 on 2013-06-17
Backup is pretty easy to restore nowadays.

Go to the program, there's a button to the bottom right that says restore. It will simply ask you for the backup location, which date to use, where you want it restored to (which would be "previous location" if your /home is already marked as being on /sda6), and it'll go.

---

