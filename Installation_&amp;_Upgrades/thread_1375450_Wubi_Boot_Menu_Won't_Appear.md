---
title: "Wubi Boot Menu Won't Appear"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by Plombo on 2010-01-07
I installed Xubuntu 9.10 with Wubi and it worked fine until a recent kernel update broke my install. I uninstalled through Windows and reinstalled Xubuntu 9.10 with Wubi with no apparent problems.

When I look in C:\ubuntu\disks, root.disk, swap.disk, and the boot folder are both present. The C:\ubuntu\disks\boot\grub folder is empty; I don't know whether or not it should be that way.

But when my computer starts, it just boots Windows Vista without displaying the menu asking me to select my OS.

Does anyone know how I can fix this? Thanks.

---

### Post by Sisco55 on 2010-01-10
I have the exact same problem. Any help would be greatly appreciated.

---

### Post by meierfra. on 2010-01-11
This is the solution by the author of Wubi:

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")

---

### Post by garvinrick4 on 2010-01-11
Go to Vista command line and Code:

"bcdedit" without quotes and see if there is menu item like wubiblder or something like
that. That will be your attached Ubuntu to the dos4grub. If there is not one there. If there
is one there is there check the time in Vista in"msconfig" without qoutes in boot tab you will see that you can put 10 seconds to make choice not 0. Also there is a systems tab that tells you if there
is a vista and and ubuntu boot and which one you want first. Cannot quite remember where it is at. If you need I can find it, let me know. 


  	 	 	 	 	 	  Fix Wubi when will not boot  
 

 Describe your new note here.  
 Fix Wubi when will not boot  
 

 How can I access my Wubi install and repair my install if it won't boot?  
 

 Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:  
 

 sudo mkdir /win  
 sudo mount /dev/sda1 /win  
 

 Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein  
 

 sudo mkdir /vdisk  
 sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk  
 

 Now the content of the virtual disk will be visible under /vdisk. 7.04 users will have to install ntfs-3g first and specify it as fstype to gain r/w access.  
 

 To check the filesystem you can use:  
 

 sudo fsck /win/ubuntu/disks/root.disk

---

