---
title: "Permissions DualBoot"
date: 2023-10-31
forum: Installation &amp; Upgrades
---

### Post by SBFree on 2023-10-31
Embarrassed with a noob question. I recently upgraded to Ubuntu 22.04.3 LTS. It was a new install rather than an in place upgrade of my prior LTS version. It Dual Boots with an install of W10. My data is on a separate physical drive. In Linux it is mounted as  /dev/sdb1 and mounts on startup with 
[INDENT]nosuid,nodev,nofail,x-gvfs-show
Mount Point /mnt/Able
Identified as Label=Able[/INDENT]

I can save and delete files on Able but they are owned by root:root even though I am logged in as user scott.
I tried
[INDENT]chown -R scott:scott Able[/INDENT]
but this didn't change ownership of directories or files.

I would like to configure the drive to mount at start and have it owned by user scott.

Thank you in advance for any help or comments.
scott

---

### Post by yancek on 2023-10-31
Is your external drive formatted with an ntfs filesystem?  Standard ownershipt and permissions for Linux don't mean anything to windows.  You haven't indicated the filesystem type so this is a guess.  If it is ntfs and you want it mounted on boot, you need a proper entry in the /etc/fstab file.  You can search the forums here (or online) to get examples/instructions as to what entry will work for you.

---

### Post by Rubi1200 on 2023-10-31
If you show us the output of these commands we will be more enlightened:

```
lsblk -f

cat /etc/fstab
```

When replying, please use Go Advanced and wrap the output with # tags.

---

### Post by MAFoElffen on 2023-10-31
I create an empty folder to make permanent mount points for data that I am going to use to share between my dual-boot. 

Here is my fstab file:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / is rpool on /dev/disk/by-id/nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W310240K-part3 during migration
# /home is hpool on /dev/disk/by-id/nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W310240K-part5
# bpool is /boot on nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W310240K-part2
# dpool is /dpool on nvme-PCIe_SSD_23011650000183-part1
# kpool is /kpool on nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W310240K-part6  & nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W618194B-part1
#
UUID=0A24D9F224D9E0AD             /home/mafoelffen/WIN_G  ntfs  defaults,uid=1000,gid=1000,fmask=0002,dmask=0002,rw   0   0 
UUID=828C01738C016351             /Media_H                ntfs  defaults,windows_names,uid=1000,gid=1000,fmask=0002,dmask=0002,rw   0   0 
# EFI at /dev/disk/by-id/nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W310240K-part1
/dev/disk/by-uuid/CBE6-0806 /boot/efi vfat defaults 0 0
/boot/efi/grub /boot/grub none defaults,bind 0 0
# swap at /dev/disk/by-id/nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W310240K-part4
/dev/disk/by-uuid/943f90ef-079f-4a38-840f-f786d19127ab none swap discard 0 0

```
(Note that this is ZFS-On-Root, and that their are really more than 11 disks on that system, but there are only 4 mounts needed for it in the fstab...)

Note that with that, I had created two folders: /home/mafelffen/WIN_G & /Media_H

Note that with my mount options, my user is UID 1000. I have full access rights and permissions to those mounts.

I do not recommend that people create permanent mounts within the /mnt or /media folders. Those two folders are meant for temporary mounts, and if you have to use some utilities that use those folders (usually /mnt), there are sometimes troubles that arise from that practice... That is why I recommend that people create new folders for their mountpoints.

---

### Post by SBFree on 2023-10-31
Hi - MAFoElffen, Rubi1200 & yancek
and thanks for the replies.

The partition is on an internal SSD that has an NTFS file system. I'll start learning about how to make a  proper entry in the /etcx/fstab file.
In response to **lsblk -f ** (loopXX responses removed)
[INDENT]
sda                                                                         
&#9500;&#9472;sda1
&#9474;    ntfs         System Reserved
&#9474;                       1EC82108C820E02F                                    
&#9500;&#9472;sda2
&#9474;    ntfs         Win10 9C0E288B0E28608E                                    
&#9500;&#9472;sda3
&#9474;                                                                           
&#9500;&#9472;sda5
&#9474;    swap   1           b9799b43-e426-4676-95e8-f22a9cad97b9                [SWAP]
&#9500;&#9472;sda6
&#9474;    ext4   1.0   LinuxA
&#9474;                       86989ae1-3d88-44bb-8786-e424ca4e9119   38.6G    30% /var/snap/firefox/common/host-hunspell
&#9474;                                                                           /
&#9500;&#9472;sda7
&#9474;    ext4   1.0   LinuxB
&#9474;                       c4dc6ede-3891-46ef-bf22-59a2c76ce15e                
&#9492;&#9472;sda8
     ext4   1.0   LinuxC
                        66b48dea-f43b-471d-837f-c4affc537825                
sdb                                                                         
&#9500;&#9472;sdb1
&#9474;    ntfs         Able  DAFC70C6FC709E87                      158.8G    20% /mnt/Able
&#9492;&#9472;sdb2
     ntfs         Games 9E423E97423E73DD                                    
sdc                                                                         
&#9500;&#9472;sdc1
&#9474;                                                                           
&#9492;&#9472;sdc2
     ntfs         Charlie
                        00C47A20C47A185C                      552.1G    41% /mnt/Charlie
sdd                                                                         
&#9500;&#9472;sdd1
&#9474;                                                                           
&#9500;&#9472;sdd2
&#9474;                                                                           
&#9492;&#9472;sdd3
                                                                            
sde                                                                         
&#9500;&#9472;sde1
&#9474;    ntfs         Delta 382A7BCF2A7B8920                                    
&#9492;&#9472;sde2
     ext4   1.0   Echo  228286e2-2c5d-4cdf-818f-b0dea18327c8                
sr0                   
[/INDENT]

In response to **cat /etc/fstab** (Response lines starting with # removed)
[INDENT]UUID=86989ae1-3d88-44bb-8786-e424ca4e9119 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b9799b43-e426-4676-95e8-f22a9cad97b9 none            swap    sw              0       0
LABEL=Able /mnt/Able auto nosuid,nodev,nofail,x-gvfs-show 0 0
LABEL=Charlie /mnt/Charlie auto nosuid,nodev,nofail,x-gvfs-show 0 0
[/INDENT]

Thanks again for your assistance!
scott

---

### Post by MAFoElffen on 2023-10-31
Please visit the "CODE Tags" link in my signature line to edit your last post. Just to try to keep you out of troubles. Read "posting Guidelines" > #3, also in my signature line, for the reasons why...

Try changing those two lines in your fstab to this:
```

LABEL=Able      /mnt/Able     ntfs     defaults,windows_names,uid=1000,gid=1000,fmask=0002,dmask=0002,rw 0 0
LABEL=Charlie   /mnt/Charlie  ntfs     defaults,windows_names,uid=1000,gid=1000,fmask=0002,dmask=0002,rw 0 0 

```
Then do
```

sudo mount -a

```
To remount your mounts from fstab, that way you do not have to reboot to test them.

Tell us how that goes.

---

### Post by #&amp;thj^% on 2023-10-31
> **MAFoElffen said:**
> 
I do not recommend that people create permanent mounts within the /mnt or /media folders. Those two folders are meant for temporary mounts, and if you have to use some utilities that use those folders (usually /mnt), there are sometimes troubles that arise from that practice... That is why I recommend that people create new folders for their mountpoints.

Wise Words to live by, and I do the same.

---

### Post by SBFree on 2023-10-31
Ok, changing fstab made the Able & Charlie partitions disappear from the "Other Locations" in FILES. They do appear as folders under "Computer/mnt".  The few files & folders I checked permissions on describe 'scott' is the owner & group rather than 'root'. Thank you for helping solve the ownership question I had. How do I go about making them subfolders in "Home" or does that seem unnecessary if I make 'bookmarks' of them in FILES?

Also I tried
```
gksu gedit /etc/fstab
```
and got a command not found message. Using
```
sudo gedit /etc/fstab
```
gave warnings, so I guess I should learn the proper way to edit fstab.
Using
```
sudo mount -a
```
didn't seem to work but rebooting did.

Thank you again, and if I am still not using tags correctly or adhering to posting guidelines please let me know.
scott

---

### Post by Rubi1200 on 2023-11-02
In most cases, using sudo and the nano editor should suffice when editing the types of files mentioned here.

For example:

```
sudo nano /etc/fstab
```

---

### Post by ajgreeny on 2023-11-02
Assuming you have not changed the default editor set in your .bashrc file you could use command ```
sudoedit /etc/fstab
```
That will by default open the file in nano.

You can change the editor used by that command by editing the lines in .bashrc
[B]# set text editor to use with sudoedit command
export EDITOR="nano"[/B]
changing **nano** to **gedit**, **mousepad** or whatever GUI text editor you prefer.

---

### Post by MAFoElffen on 2023-11-02
For editing system files in console, I use Nano, Vi, Sublime, and sudoedit. When I tell someone to edit a file with elevated permissions, I tell them to do it in terminal or console, and use nano... Since nano displays the hot-keys on the bottom of the terminal screen, it is often easier for new users to pick up and use.  

Sidenote: I have used sublime-text for years, but is not in the repo's anymore so is no longer in APT. I add their repo to install it. Also available via Snap and FlatPak.

---

### Post by #&amp;thj^% on 2023-11-02
> **MAFoElffen said:**
> 
Sidenote: I have used sublime-text for years, but is not in the repo's anymore so is no longer in APT. I add their repo to install it. Also available via Snap and FlatPak.
Same here but a heads up the flatpak version has an outdated "(runtime/org.freedesktop.Sdk/x86_64/21.08) found in remote flathub" 
If your concerned with security is all.

---

