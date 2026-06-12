---
title: "Upgrade to Ubuntu 11.10 with Live CD"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by miguel53201 on 2011-10-30
My Ubuntu 11.04 is booting very slowly. I have a dual boot with Windows XP and Ubuntu 11.04. I have burned a Live CD of 11.10. What I would like to do is upgrade and have a clean installation of Ubuntu 11.10 via Live CD and keep the Dual Boot. I know I will lose all my data on Ubuntu 11.04

I have tried the Live CD and I believe there should be an option to "Upgrade to Ubuntu 11.10" But all I see is is 2 options "Fresh Install" and "something else". I have looked at the web and cannot see any instructions on how to upgrade a dual boot via a Live CD. Also when in the Live CD I do not have any access to the Home Folder. Can someone please advise how to upgrade a dual boot via a LIve CD Below is the results of sudo fdisk -l


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         629     4755208+   b  W95 FAT32
/dev/sda2   *         630       12411    89071920    7  HPFS/NTFS
/dev/sda3           12412       15461    23058000   83  Linux
/dev/sda4           15462       15881     3175200   82  Linux swap / Solaris

Thanks In ADvance

---

### Post by Script Warlock on 2011-10-30
> What I would like to do is upgrade and have a clean installation of Ubuntu 11.10 via Live CD and keep the Dual Boot upgrade or clean install.. update-manager -d in the terminal is much easier.

---

### Post by miguel53201 on 2011-10-30
Thanks Script Warlock for the quick reply. 

That is what I normally do from when I started Ubuntu back with 7.10. My Ubuntu 11.04 is not booting well and has alot of stuff that has slowed Ubuntu down. So I want to do  fresh install of Ubuntu 11.10 and keep the dual boot with Windows XP. I have done more web surfing will the Upgrade to 11.10 be available from the Alternate CD

---

### Post by Script Warlock on 2011-10-30
ok if you want a fresh install ubuntu then choose the option "something else" upon partitioning don't ever touch any ntfs or you may lose your windows partition.

---

### Post by Elfy on 2011-10-30
> So I want to do fresh install of Ubuntu 11.10 and keep the dual boot with Windows XP.

> will the Upgrade to 11.10 be available from the Alternate CDWhich do you want to do?

For a clean install - backup your data.

Boot the cd - live or alternate - install - when you get to the partition part of the install - install over your existing install partition.

---

### Post by miguel53201 on 2011-10-30
So I do "Something Else" 
select "/dev/sda3 12412 15461 23058000 83 Linux" 
and the Dual Boot with Windows XP will still work when I reboot?

Just wondering why the Option in the Live CD does not have the "Upgrade to Ubuntu 11.10" option avaiable. Like I have seen in places. 

Thanks

---

### Post by Script Warlock on 2011-10-30
yes it will work and as i said dont touch those ntfs.. just be careful.

---

### Post by miguel53201 on 2011-10-30
OK I will try this tommorrow. 

Thanks for your help

---

