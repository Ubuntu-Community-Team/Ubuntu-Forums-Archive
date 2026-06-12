---
title: "Unable to install on SSD"
date: 2014-07-02
forum: Installation &amp; Upgrades
---

### Post by oricshin on 2014-07-02
gparted on Ubuntu and Xubuntu see my ssd but in the install it's only avaliable to select on the "Device for bootloader installation"
[ATTACH=CONFIG]254406[/ATTACH]

---

### Post by SuperFreak on 2014-07-02
I think it is because you have the partition flagged as boot. Is that because the EFI files are stored there?
Hopefully someone with more experience will pipe in but you may have to make a new partition in addition to sda1 without the boot flag

---

### Post by yancek on 2014-07-03
Which installation type have you selected and what options did you have?  If you have any other operating system, you should have seen the 'Install Alongside', 'Erase Disk' and 'Something Else' options.  Do you have any other drives attached?

---

### Post by oricshin on 2014-07-03
> **yancek said:**
> Which installation type have you selected and what options did you have?  If you have any other operating system, you should have seen the 'Install Alongside', 'Erase Disk' and 'Something Else' options.  Do you have any other drives attached? there's no menu and no i have no other operating systems installed it just goes from from Language->System Req->screen with no harddrive

---

### Post by SuperFreak on 2014-07-03
I would suggest you start over. **I am assuming you have UEFI BIOS so if not do not follow these steps**
1. Boot to Live USB/DVD and delete the partition you made in GParted
2. Create 4 partitions 
a) First   format  the drive to GPT
(Device -> Create Partition Table... -> GPT)
b) Right click  on Unallocated space and chose "new"Then I created a 250 MB FAT 32 partition and labelled it EFI
c)Creat and lablel  / and HOME partitions and formatted them EXT 4 (25 GB and 25 GB(or what ever you want for HOME ie remainder of disc leaving room for Swap)) and labelled them
d) Creat a 2 GB SWAP and Formatted it LINUX-SWAP
e) right click  on EFI partition and chose Manage Flags. Chose boot flag for EFI 
3. Reboot  the computer and go into UEFI and set the boot priority to USB  UEFI as the first choice  and exit  and save.
4. Then start  install. Chose to install manually -I think it is called "Or Something Else" .Most of the rest is fairly straight forward  . You have to set the root partition and home partition up. double click on each of these and it will give the option to select / for ROOT from the drop down list or /Home for each. These should be set as EXT 4 partitions.
5. Before preceeding choose the bootloader on the bottom of that window to your EFI partition.

---

