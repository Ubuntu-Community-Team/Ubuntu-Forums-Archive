---
title: "Partition guide"
date: 2019-12-14
forum: Installation &amp; Upgrades
---

### Post by hamid-azizi on 2019-12-14
hi , it may been asked alot but i didnt find same situation so i better ask
im new to linux , i have 120 GB SSD i want to install ubuntu and i plan to run windows in virtual machine for my design works after install linux .
what is recommended partition schema for me (depend on i need a partition for my design works to organize them & care virtual machine run smooth )
(i use bios)
thank you .

---

### Post by Skaperen on 2019-12-14
you can separate things in a different directory.  i recommend the whole thing be split into about 8 GB swap space and all the rest be one big 112GB partition.  this way you are less likely to run out of space if you make some partition too small.

---

### Post by hamid-azizi on 2019-12-14
I wont lose my design works if os fail to boot or any other problem ?
Sorry im new to linux , in windows its risky if i save my files in os drive

---

### Post by hamid-azizi on 2019-12-14
> **Skaperen said:**
> you can separate things in a different directory.  i recommend the whole thing be split into about 8 GB swap space and all the rest be one big 112GB partition.  this way you are less likely to run out of space if you make some partition too small.

[COLOR=#000000]I wont lose my design works if os fail to boot or any other problem ?[/COLOR]
[COLOR=#000000]Sorry im new to linux , in windows its risky if i save my files in os drive[/COLOR]

---

### Post by CatKiller on 2019-12-14
Partitioning is irrelevant. You can make it as simple or as complicated as you like.

What you want are backups.

---

### Post by tea for one on 2019-12-14
> **hamid-azizi said:**
> [COLOR=#000000]I wont lose my design works if os fail to boot or any other problem ?[/COLOR]
[COLOR=#000000]Sorry im new to linux , in windows its risky if i save my files in os drive[/COLOR]

Saving files in the OS drive (whether Ubuntu or Windows) is not inherently risky in itself.

What is risky and inadvisable is the **lack** of a data back up.

If the OS fails to boot you will lose immediate access to your files.

Many boot problems can be fixed by the helpful users on this forum but nobody can replace your data.

Therefore, I advise that you **always** have healthy and reliable back ups of your important design work.

Operating systems can be replaced but your data is irreplaceable.

Oh CatKiller, I was making a cup of tea and you sneaked in front of me.

---

### Post by hamid-azizi on 2019-12-14
> **tea for one said:**
> Saving files in the OS drive (whether Ubuntu or Windows) is not inherently risky in itself.

What is risky and inadvisable is the **lack** of a data back up.

If the OS fails to boot you will lose immediate access to your files.

Many boot problems can be fixed by the helpful users on this forum but nobody can replace your data.

Therefore, I advise that you **always** have healthy and reliable back ups of your important design work.

Operating systems can be replaced but your data is irreplaceable.

Oh CatKiller, I was making a cup of tea and you sneaked in front of me.

What about reinstall os ? Is it smart to save files in os drive and move them when want reinstall os ?

---

### Post by hamid-azizi on 2019-12-14
> **CatKiller said:**
> Partitioning is irrelevant. You can make it as simple or as complicated as you like.

What you want are backups.

Yes just wanted to know for better virtual machine experience i need more swap or bigger root directory or ?

---

### Post by tea for one on 2019-12-14
> **hamid-azizi said:**
> What about reinstall os ? Is it smart to save files in os drive and move them when want reinstall os ?

In the unlikely event that you would have to re-install Ubuntu, it would make no difference where your files are stored because you would/should always have a back up of your data.

Just imagine if your complete drive failed &#8211; operating system and data gone.

At least you have a back up of your important data.

---

### Post by hamid-azizi on 2019-12-14
> **tea for one said:**
> In the unlikely event that you would have to re-install Ubuntu, it would make no difference where your files are stored because you would/should always have a back up of your data.

Just imagine if your complete drive failed &#8211; operating system and data gone.

At least you have a back up of your important data.
Thank you !
I will backup my data
So no need /home or /boot or others ?
As skaperen adviced 8 gb swap and others for root ? 
I just dont want go wrong in first step because im new to linux

---

### Post by Impavidus on 2019-12-14
> **hamid-azizi said:**
> What about reinstall os ? Is it smart to save files in os drive and move them when want reinstall os ?

It is useful to have a separate partition for your data. Of course you should have backups, but when you want a fresh install of your OS (because you broke it or because you want to move the the next release), it's very easy when you can simply mount your data afterwards without a need to restore your backups. That can save some time. In particular if, like I, you don't keep complete backups of your home directory. To save space and make creation of backups faster, I don't have backups of any stuff I compiled myself (executables, PDFs). Instead, I create only backups of the sources from which they are generated. Similarly, I don't have backups of stuff I can download again. Faster backup, slower restore, but I spend much more time creating backups than restoring them anyway.

Typically, you want about 25GB for the OS and use the rest for data, for example a /home partition. But I don't know where your virtual machine will be stored.

---

### Post by hamid-azizi on 2019-12-14
> **Impavidus said:**
> It is useful to have a separate partition for your data. Of course you should have backups, but when you want a fresh install of your OS (because you broke it or because you want to move the the next release), it's very easy when you can simply mount your data afterwards without a need to restore your backups. That can save some time. In particular if, like I, you don't keep complete backups of your home directory. To save space and make creation of backups faster, I don't have backups of any stuff I compiled myself (executables, PDFs). Instead, I create only backups of the sources from which they are generated. Similarly, I don't have backups of stuff I can download again. Faster backup, slower restore, but I spend much more time creating backups than restoring them anyway.

Typically, you want about 25GB for the OS and use the rest for data, for example a /home partition. But I don't know where your virtual machine will be stored.

Do i need separate ntfs to share with windows in virtual machine ? Or windows will write in home directory ? Where files will be saved when im doing design in windows ?

---

### Post by TheFu on 2019-12-14
Every "cook" has a slightly different recipe.  

It depends on which hypervisor you plan to use where VMs might be stored.  It also depends on you storage management choices at installation time which would work best.  Also, how partitioning should be done is dependent on whether UEFI or legacy BIOS is being used to boot.

Windows likes to have 60G+ for itself.

I've posted my "ideal" partitioning in these forums a few times, since this question comes up weekly.  I think 8G is overkill for swap. Each cook here has different experiences, which is why we have slightly different answers. [https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277) shows mine. On my VM hosts, I use a separate LV for each VM. There are many reasons to do it that way. Someone new to Linux shouldn't probably shouldn't use LVM, but just take the partition sizes and mount points for a guide. LVM is an enterprise storage technique, so if you are familiar with Veritas Storage Manager and File System, it isn't hard to understand.

We will all agree that you need daily, versioned, backups that can be restored to get the system back the way it was prior to any failure.  If you need to restore to completely different hardware, the backups should support that scenario.  I use specific partitioning to make backups and recovery easier.

---

