---
title: "No permission to access new (second) hard drive"
date: 2024-08-10
forum: Installation &amp; Upgrades
---

### Post by crashlanding on 2024-08-10
Hello, I have a new Ubuntu 20.04.6LTS installation with two hard drives. The second hard drive appears in Files > Other Locations. When I select it it says Folder is Empty. So I tried to copy a folder to the second hard drive.  I get "Error while copying. The folder cannot be copied because you do  not have permission to create it in the destination." In files, I tried to create a  folder on the new drive by right clicking. But the New Folder option is  gray, unavailable. The New Folder option in the drop down menu from the  Drive2 thing in the upper left of Files, is also gray and  unavailable. I right clicked in the directory area and selected  properties (for the second drive). Under permissions, all three boxes  are grayed out, and it tells me "You are not the owner, so you cannot  change these permissions." I looked this up on the internet and found  that I probably need to use the chmod command. However, everything I found is about  not being able to access a file, not about accessing the hard drive. I  don't know how to use chmod so it fixes the drive, (or the partition).
Please tell me how to gain access to the second hard drive. 				

In case this helps, here is what I get when I use the df -h command:

  	 	 	 	   Filesystem      Size  Used Avail Use% Mounted on
 udev             16G     0   16G   0% /dev

 tmpfs           3.2G  2.6M  3.2G   1% /run
 /dev/nvme0n1p2  1.9T  9.8G  1.8T   1% /
 tmpfs            16G     0   16G   0% /dev/shm
 tmpfs           5.0M  4.0K  5.0M   1% /run/lock
 tmpfs            16G     0   16G   0% /sys/fs/cgroup

 /dev/loop0      128K  128K     0 100% /snap/bare/5
 /dev/loop2       92M   92M     0 100% /snap/gtk-common-themes/1535
 /dev/loop3       46M   46M     0 100% /snap/snap-store/638
 /dev/loop1       64M   64M     0 100% /snap/core20/1828
 /dev/loop4      347M  347M     0 100% /snap/gnome-3-38-2004/119
 /dev/loop5       50M   50M     0 100% /snap/snapd/18357
 /dev/nvme0n1p1  511M   51M  461M  10% /boot/efi
 tmpfs           3.2G  108K  3.2G   1% /run/user/1000
 /dev/sda1       231G  1.8G  230G   1% /media/chris/USBFlash256
 /dev/nvme1n1p1  1.9T   28K  1.8T   1% /media/chris/Drive2
 /dev/loop6       39M   39M     0 100% /snap/snapd/21759
 /dev/loop7       64M   64M     0 100% /snap/core20/2318
 /dev/loop8      350M  350M     0 100% /snap/gnome-3-38-2004/143

---

### Post by yancek on 2024-08-10
The df -h command only shows mounted partitions.  mounted simply meaning accessible so that output doesn't really help anyone to help you.  The output you posted shows:

>  /dev/nvme0n1p2 1.9T 9.8G 1.8T 1% /
/dev/nvme0n1p1 511M 51M 461M 10% /boot/efi

That would be the Ubuntu system partition (partition 2) , the partition with the root ( / ) symbol at the end.  The second partition is your EFI partition.  The output below shows your 2 other drives, one 231G and one 1.9T.  

>  /dev/sda1 231G 1.8G 230G 1% /media/chris/USBFlash256
/dev/nvme1n1p1 1.9T 28K 1.8T 1% /media/chris/Drive2

To get information on them as far as permissions and owner:group you should use the ls command to list that information.  Just open a terminal and run the commands below.  To get the same information on the contents of these directories, any directory or file inside, run the commands and omit the 'd' in ls -ld. 

```
ls -ld /media/chris/USBFlash256
ls -ld  /media/chris/Drive2
```

Do these drives have Linux filesystems.  If they are windows, you need to set this in the /etc/fstab file as windows doesn't use/understand the standard Linux rwx permissions.  The link below gives an example of changing ownership if that is what is needed.  You don't indicate the owner:group but based on your post, it is likely root:root which is standard.  Just as an FYI, a standard user generally does not have permission to write/delete outside the /home/user directory.  That's very basic with Linux.  You need to use sudo to do these things that require administrator privileges to change system settings.  There are many sites which explain how to change owner:group such as the one below.  If the link below doesn't help, just do an online search until you find one you understand.

[https://askubuntu.com/questions/1368536/using-chown-to-change-ownership-on-additional-hdd](https://askubuntu.com/questions/1368536/using-chown-to-change-ownership-on-additional-hdd)

---

### Post by crashlanding on 2024-08-10
Hi Yancek, These are all Linux filesystems. I should have removed the flash drive before using df -h.
I reviewed the information you sent a link to and it worked on the first try. "sudo chown name:name /media/name/Drive2"
Thank you very much.

---

### Post by yancek on 2024-08-11
You're welcome.  Good thing to remember if you continue using Linux is that in general, a user will not have access to much of anything outside the /home/user directory so if and when you add external media you will need to modify owner:group and user permissions on any Linux filesystem.

---

