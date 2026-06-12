---
title: "Not able to recognize home directory post upgradation to Ubuntu 22.04"
date: 2023-03-15
forum: Installation &amp; Upgrades
---

### Post by ssinha6 on 2023-03-15
Recently there has been an upgradation to Ubuntu 22.04. Prior upgradation, I used to login with username "sourav" and all my files were kept under home/sourav directory .Post upgradation , when I try to login to the system I am unable to find the home directory. I used the command df - h and found out that  dev/sda1 has files of  size 81GB . How can I retrieve those files ? Also I am noticing none of the browsers such as firefox or chrome are working. System volume is also not appearing on the screen.

---

### Post by MAFoElffen on 2023-03-15
In the Grub2 Boot menu, go to "Advanced Options for Ubuntu" > Go to a menu item ending in "(recovery mode)" > Select "network" > Select "root"... At the prompt, press <Enter>

Post the results of 
```

ls /home/sourav/
grep . /etc/fstab
lsblk -o name,size,type,fstype,mountpoints | grep -v 'loop\|snap'

```

Edit: The easiest way to post the result, may be to either take a picture of it with a phone (uploaded as an attachment), or redirect it to a file, which you could then post the contents of that file (posted within CODE Tags).

---

### Post by ssinha6 on 2023-03-15
Tried [COLOR=#000000][FONT=&quot]ls /home/sourav/ but getting "No such file or directory ".[/FONT][/COLOR]

---

### Post by ssinha6 on 2023-03-15
I have checked the /etc/passwd file , my login is present in it , but when I try to login I am getting 2 login option 1)Ubuntu 2)Ubuntu in Wayland(pls see the screenshot).When I try to login with Ubuntu option, it is redirecting me back to the login screen . When I try to login with Ubuntu with Wayland option, I am able to login but I cant see any files under home/sourav, also no browsers are working , no volume options are visible . So it seems my login is looping with the Ubuntu option.

[IMG]https://i.stack.imgur.com/E1j3a.png[/IMG]

---

### Post by MAFoElffen on 2023-03-15
I asked for the above results of the commands, because your home folder is somehow not mounting to your userid. We need that information (and maybe more) to see why...

If you can log in in Wayland, then you could run those commands from a graphical terminal.

You cannot use a browser, because you don't have a working profile file, because of the home folder being messed up. The same wiht not being able to start Xorg. Those problems will resolve themselves when you get a working User Home folder...

---

### Post by ssinha6 on 2023-03-15
```
Please find the results of the commands.

sourav@sourav-Lenovo-ideapad-320-15IKB:/$ ls /home/sourav/
ls: cannot access '/home/sourav/': No such file or directory
sourav@sourav-Lenovo-ideapad-320-15IKB:/$ grep . /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=8a96eeb3-32e7-455a-ae81-9c90a09a6174 /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0
sourav@sourav-Lenovo-ideapad-320-15IKB:/$ lsblk -o name,type,fstype,mountpoints | grep -v 'loop\|snap'
NAME   TYPE FSTYPE   MOUNTPOINTS
sda    disk          
                     /
sr0    rom          
sourav@sourav-Lenovo-ideapad-320-15IKB:/$
```

---

### Post by MAFoElffen on 2023-03-15
Sideline note: If you go back to your last, Select Edit > Advance > Select the text of the output with your mouse > Select the "#" Icon... That will wrap the raw output within code Tags... > Save. Raw output and commands in post, where not wrapped in Code Tags, does strange things to the Forums software.

Now post the results of 
```

ls /home

```

---

### Post by ssinha6 on 2023-03-15
Nothing is being listed under  /home for the command ls /home

---

### Post by MAFoElffen on 2023-03-15
You do not have any backups do you? I am assuming the answer is "No"...

This is output from one of my computers:
```

mafoelffen@Mikes-B460M:~$ lsblk -o name,type,fstype,mountpoints | grep -v 'loop\|snap'
NAME        TYPE FSTYPE     MOUNTPOINTS
sda         disk zfs_member 
&#9492;&#9472;sda1      part zfs_member 
sdb         disk            
&#9500;&#9472;sdb1      part ext4       
&#9500;&#9472;sdb2      part ntfs       
&#9492;&#9472;sdb3      part ntfs       
nvme0n1     disk            
&#9500;&#9472;nvme0n1p1 part vfat       /boot/grub
&#9474;                           /boot/efi
&#9500;&#9472;nvme0n1p2 part swap       [SWAP]
&#9500;&#9472;nvme0n1p3 part zfs_member 
&#9492;&#9472;nvme0n1p4 part zfs_member 

```
From another:
```

mafoelffen@Mikes-ThinkPad-T520:~$ lsblk -o name,type,fstype,mountpoints | grep -v 'loop\|snap'
NAME   TYPE FSTYPE   MOUNTPOINTS
sda    disk          
&#9500;&#9472;sda1 part vfat     /boot/efi
&#9500;&#9472;sda2 part          
&#9500;&#9472;sda3 part ntfs     
&#9500;&#9472;sda4 part          
&#9500;&#9472;sda5 part          
                     /
sdb    disk          
&#9500;&#9472;sdb1 part ntfs     
&#9492;&#9472;sdb2 part ext4     /home/mafoelffen/Disk2
sdc    disk          
&#9492;&#9472;sdc1 part ext4     /home/mafoelffen/mSATA

```
From what you posted on yours:
```

sourav@sourav-Lenovo-ideapad-320-15IKB:/$ lsblk -o name,type,fstype,mountpoints | grep -v 'loop\|snap'
NAME   TYPE FSTYPE   MOUNTPOINTS
sda    disk          
                     /
sr0    rom          

```
'/dev/sr0' is the first CD-ROM device in the system through SCSI or SATA. 'lsblk' is showing only one drive as /dev/sda, but the output is wrong... It is not showing any aprtitoins, nor filesystem type in those partitions. It does boot to a certain point, and you can log in via wayland. [COLOR=#ff0000]Those results are somehow "wrong".[/COLOR] 

You have peaked my interest and got my full attention. LOL

I need more information to see what is going on there.  I'm thinking of ways around that. 

The safest way, without affecting your original account would to create a temporary administrative user account, and log in as that user, so you can provide more information on your system, so you can straighten this out.
```

sudo adduser sourav2
sudo usermod -aG sudo sourav2
logout

```
Login as 'sourav2'

Then please run the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") and post the URL of the pastebin the report uploads to.

---

### Post by ssinha6 on 2023-03-16
I have executed the steps as you mentioned. The report can be viewed here - [https://paste.ubuntu.com/p/pxRqFy3sSj/](https://paste.ubuntu.com/p/pxRqFy3sSj/)
Please let me know what is needed further. I am worried about my data and how to recover it.

---

### Post by MAFoElffen on 2023-03-16
I reviewed the report and I only see one partition on your system. It is booted as legacy, so there is only one partition found, where that partition is the root volume. 
```

---------- Disk/Partition Information From 'lsblk':
NAME     SIZE FSTYPE   LABEL MOUNTPOINT                            MODEL
sda    931.5G                                                      ST1000LM035-1RK172
|_sda1 931.5G ext4           /                                     
sr0     1024M                                                      PLDS DVD-RW DA8AESH
   ------- 'lsblk' information continued ...
NAME   HOTPLUG PARTUUID                             UUID
sda          0                                      
|_sda1       0 dd9b9e2e-01                          8a96eeb3-32e7-455a-ae81-9c90a09a6174
sr0          1                                      

```
```

---------- Disk/Partition Information From 'fdisk':

Disk /dev/sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000LM035-1RK1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xdd9b9e2e

Device     Boot Start        End    Sectors   Size Id Type
/dev/sda1  *     2048 1953523711 1953521664 931.5G 83 Linux

```
```

---------- Current Mount Details of 'mount':
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
/dev/sda1 on /var/snap/firefox/common/host-hunspell type ext4 (ro,noexec,noatime,errors=remount-ro)

```

There is nowhere else that home might be mounted, from, so should be found in that partition... But isn't...

But, this sections shows that there is 81GB used "somewhere"...
```

---------- File system specs from 'df -h':
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda1      ext4  916G   80G  790G  10% /

```
That is a lot of space used, that seems to be more than just the basic system files and programs... Maybe there is still hope.

So let's follow that path to investigate more. Please post the output of these commands:
```

sudo du -hsx /* 2> /dev/null | sort -rh | head -n 40
find / -name '.Xauthority' 2> /dev/null
find / -d -name '.config' 2> /dev/null

```

---

### Post by ssinha6 on 2023-03-16
```
sourav2@sourav-Lenovo-ideapad-320-15IKB:~$ sudo du -hsx /* 2> /dev/null | sort -rh | head -n 40[sudo] password for sourav2: 
58G	/lost+found
11G	/var
8.7G	/usr
2.1G	/swapfile
806M	/opt
239M	/home
168M	/boot
90M	/google-chrome-stable_current_amd64.deb
44M	/root
17M	/etc
2.2M	/run
732K	/tmp
104K	/snap
8.0K	/media
4.0K	/usb
4.0K	/srv
4.0K	/mnt
4.0K	/cdrom
0	/vmlinuz.old
0	/vmlinuz
0	/sys
0	/sbin
0	/proc
0	/libx32
0	/lib64
0	/lib32
0	/lib
0	/initrd.img.old
0	/initrd.img
0	/dev
0	/bin
sourav2@sourav-Lenovo-ideapad-320-15IKB:~$ find / -name '.Xauthority' 2> /dev/null
sourav2@sourav-Lenovo-ideapad-320-15IKB:~$ find / -d -name '.config' 2> /dev/null
/usr/src/linux-headers-5.15.0-60-generic/.config
/usr/src/linux-headers-5.15.0-67-generic/.config
/home/sourav2/snap/firefox/2432/.config
/home/sourav2/snap/snapd-desktop-integration/49/.config
/home/sourav2/.config
sourav2@sourav-Lenovo-ideapad-320-15IKB:~$
```

---

### Post by MAFoElffen on 2023-03-16
> **ssinha6 said:**
> ```
sourav2@sourav-Lenovo-ideapad-320-15IKB:~$ sudo du -hsx /* 2> /dev/null | sort -rh | head -n 40[sudo] 
password for sourav2: 
[COLOR=#ff0000]58G    /lost+found[/COLOR]

```
There you go... They might still be there.

Please boot up from a LiveUSB > TRY > Open a terminal session and do
```

sudo fsck -p /dev/sda1

```
When it is done, reboot and check what is there.

---

