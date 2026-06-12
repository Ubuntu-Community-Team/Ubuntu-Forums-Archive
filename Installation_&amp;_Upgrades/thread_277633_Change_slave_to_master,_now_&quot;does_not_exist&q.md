---
title: "Change slave to master, now &quot;does not exist&quot;"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by Angry on 2006-10-14
Hello,

I had originally installed Ubuntu onto a slave drive, with Windows on master, but the drive with Windows has bitten the dust.

I had removed the pooched drive, changed the jumper settings from the slave drive to reflect master, and now wish to go with just Ubuntu.

However, when trying to boot from Grub, I select the Ubuntu option and receive an error about "root (hd1,0)... does not exist".  I can only assume that I need to tell Ubuntu that it now on the master drive.  However, I do not know how to do that - especially from the live cd (which I am using right now).

I had run the Grub setup:

sudo grub
find /boot/grub/stage1 # returns (hd0,0)
root (hd0,0)
setup (hd0)

to no avail.  I am now assuming that I have to edit the file /boot/grub/[something] that is sitting on my harddrive, however I cannot mount that drive as I get the error "device /dev/hda1 is not removable" due to the fact I am running from the live cd.

I'm sure there is a simple command line to make this happen, but from the searches that I have done, it has not provided me with any answers.

Thanks in advance.

---

### Post by catlett on 2006-10-14
I'll assume ubuntu is on your first partition but if there is an issue, post the output of```
 sudo fdisk -l
```
To get at the menu list do this 
```
sudo mkdir /media/ubuntu
```
```
sudo mount /dev/hda1 -t ext3 /media/ubuntu
```
```
sudo gedit /media/ubuntu/boot/grub/menu.lst
```
When you get the menu opened, you will see the listings for ubuntu. You need to change the second line of the ubuntu entry.
> root (hd1,0) 
to the correct number since the move changed it
> root (hd0,0)
Save the file and close.
If you get any errors, post them along with the fdisk output.

---

### Post by Angry on 2006-10-14
Thanks man!!!  You rock!

The only problem that I had was that the kernel root entries (root=/dev/hda1) were wrong (it was root=/dev/hdb1), so it hung when trying to reboot.  So I made the appropriate changes and everything is right with the world.

Thanks again.

---

### Post by gn2 on 2006-10-15
> **Angry said:**
> Thanks man!!!  You rock!

The only problem that I had was that the kernel root entries (root=/dev/hda1) were wrong (it was root=/dev/hdb1), so it hung when trying to reboot.  So I made the appropriate changes and everything is right with the world.

Thanks again.

Other alternative would have been to leave it where it was, it doesn't need to be Master at all.......

---

### Post by catlett on 2006-10-15
> **gn2 said:**
> Other alternative would have been to leave it where it was, it doesn't need to be Master at all.......

When you only have 1 drive, you do not have a choice to make it a slave. It has to be the master.> I had originally installed Ubuntu onto a slave drive, with Windows on master, but the drive with Windows has bitten the dust. The windows drive died. All he has left is the ubuntu drive. The grub file had to be changed to reflect the fact that Ubuntu's drive was now the first drive and not the second.

---

### Post by gn2 on 2006-10-15
> **catlett said:**
> When you only have 1 drive, you do not have a choice to make it a slave. It has to be the master. The windows drive died. All he has left is the ubuntu drive. The grub file had to be changed to reflect the fact that Ubuntu's drive was now the first drive and not the second.

If you are running IDE drives, you can have one drive on the slave connector with Ubuntu and Grub on it, nothing at all on the master connector and it will boot. Fact.

All the O.P. would have required to do is install Grub to the Ubuntu drive, leaving Master connector for a new drive with Windows and un-corrupted MBR.

Then select OS via F8 (or whatever key) to bring up the boot device selection menu.

---

