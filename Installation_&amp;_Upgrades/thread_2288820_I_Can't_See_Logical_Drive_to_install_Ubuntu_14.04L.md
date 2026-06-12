---
title: "I Can't See Logical Drive to install Ubuntu 14.04LTS"
date: 2015-07-30
forum: Installation &amp; Upgrades
---

### Post by koaung2 on 2015-07-30
When i try to install Ubuntu dual boot with window 8.1,i cant see my logical partition in installation wizard.it is show Free sda partition. Why?
I already create logical partition with EaseUS Partition manager in window.
In the installation process ,it is show the whole drive.How can i do for that?
Help me for that.i attach my installation steps.

---

### Post by dino99 on 2015-07-30
use the linux partition tool: gparted live
[http://sourceforge.net/projects/gparted/files/gparted-live-stable/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/)

---

### Post by yancek on 2015-07-30
The third image you posted from windows shows a 36GB logical partition.  Is that where you planned to install Ubuntu?  If it is, you have a major problem because it is formatted ntfs which is a proprietary windows filesystem and no Linux will run on it so use GParted from the install medium to change that.  I would still expect that partition to show, not sure why it doesn't but you do need to change the filesystem type.

---

### Post by happyytilton on 2015-07-30
Use your EaseUS Partition manager in Windows, to delete the "G" partition. It will then become unallocated space. Boot to your live CD and then choose the "install alongside" option.
It will format the unallocated space as "ext4" and install Ubuntu and the "swap".
This has been the easiest way for me to do it. It might not be proper way, but it has worked well for me in the past. Hope this helps.

---

### Post by oldfred on 2015-07-31
Is Windows 8 in BIOS boot mode on MBR(msdos) partitioning?

Post this from terminal in live installer:
sudo parted -l

If you create too many partitions in Windows it may convert from Basic to Dynamic which is a Windows proprietary partitioning which does not work with Linux.
Or did you leave Windows 8 with fast start up on. That is always on hibernation which then prevents Linux NTFS driver from seeing the Windows partitions.

Do not force install if Windows not shown. Only use Something Else.

---

### Post by koaung2 on 2015-08-01
Now i see my logical drive with ubuntu 15.04 .My error may be uefi? Because when i install ubuntu 15.04 ,it ask to change UEFI mode and i click yes.But now new problem when install ubuntu 15.04.It take so long time in partition process.

---

### Post by oldfred on 2015-08-02
UEFI uses gpt partitioning which does not use MBR with primary, extended and logical partitions. 

But if you installed Windows in BIOS mode with MBR(msdos) partitioning, then installing  Ubuntu in UEFI mode will convert drive from MBR to gpt and in effect erase Windows.

---

### Post by koaung2 on 2015-08-02
Mr oldfred ,you are right .now my window can't boot :-( :-( .Now ubuntu only work.How can i solve to dual boot.Is my window boot file is lost? How can i repair ?

---

### Post by oldfred on 2015-08-02
Did it erase drive?
If so Windows is not recoverable as at least parts of it were overwritten with Ubuntu's files.  But Windows writes primarily to beginning of drive and Ubuntu writes all over drive. So some data is still there.

Post this:
sudo parted -l

---

### Post by koaung2 on 2015-08-02
> **oldfred said:**
> Did it erase drive?
If so Windows is not recoverable as at least parts of it were overwritten with Ubuntu's files.  But Windows writes primarily to beginning of drive and Ubuntu writes all over drive. So some data is still there.

Post this:
sudo parted -l

No. it didn't erase drive. i think boot file is overwritten.Window is primary partition and Ubuntu is next logical partition.Now i can see and access window file from ubuntu.

---

### Post by koaung2 on 2015-08-02
> **koaung2 said:**
> No. it didn't erase drive. i think boot file is overwritten.Window is primary partition and Ubuntu is next logical partition.Now i can see and access window file from ubuntu.

Now it is ok with update-grub.

---

### Post by oldfred on 2015-08-02
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

