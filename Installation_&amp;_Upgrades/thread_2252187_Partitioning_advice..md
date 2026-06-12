---
title: "Partitioning advice."
date: 2014-11-09
forum: Installation &amp; Upgrades
---

### Post by pyrokinetic2 on 2014-11-09
Hi there, 

I recently bought a Toshiba laptop that had Windows 8.1 pre-installed on it. I'm wanting to dual boot between the two operating systems but can't quite figure out which partitions I should remove or resize. I'm sure this question has been asked numerous times but I couldn't really find any other threads relating to it, if someone has a thread relating to my problem PLEASE direct me there....providing the solution fits my particular scenario, obviously. :P

I've included a screenshot to show what I'm facing. Any help is greatly appreciated. :D 

Cheers, 
Stu

---

### Post by yancek on 2014-11-10
The partition referred to as "C" in your image is by far the largest partition and is the one you would need to shrink to make room to install Ubuntu.  You should be able to do that from the "Disk Management" option on your windows system.  After doing that you will have unallocated space which should be shown when you boot the Ubuntu installation medium, probably best to select the option "Something Elsle" in Ubuntu which is a manual install and will give you control of selecting where to install.  Also, your windows is installed as EFI so make certain you install Ubuntu in EFI mode.  There should be an option on the installation medium.  Read the explanation at the link below on how to accomplish this.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2014-11-10
It does not look like you have a lot of space in your "c:" partition. Windows really likes 30% free and at 10% free just about does not work. It has no working room to run defrag. So do not shrink Windows too much and do a major houseclean before doing the shrink.

---

### Post by pyrokinetic2 on 2014-11-11
> **yancek said:**
> The partition referred to as "C" in your image is by far the largest partition and is the one you would need to shrink to make room to install Ubuntu.  You should be able to do that from the "Disk Management" option on your windows system.  After doing that you will have unallocated space which should be shown when you boot the Ubuntu installation medium, probably best to select the option "Something Elsle" in Ubuntu which is a manual install and will give you control of selecting where to install.  Also, your windows is installed as EFI so make certain you install Ubuntu in EFI mode.  There should be an option on the installation medium.  Read the explanation at the link below on how to accomplish this.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

So, just to confirm.......all I have to do is shrink my C drive to whatever I wish, giving me enough unallocated space for my linux install, then just install using the 'Something else' option? ....After reading through that article you posted, obviously...

I just wondered if I'd run into problems given the numer of partitions that had been made? I thought there was like a limit of four or something, thus meaning I'd have to delete my recovery partion (or partitions? I can't work out what the other partitions are, I suspect the 10GB is the full recovery partition though) .....or is it because those are only logical drives rather than primary partitions?....This is where I get horribly confused.

---

### Post by oldfred on 2014-11-12
Your screen shot shows an efi partition. So if system if booting Windows with UEFI then drive must be gpt partitioned. If not really an efi partition and you have MBR(msdos) partitioning then you do have a 4 primary partition limit.

Post this:
sudo parted -l

---

