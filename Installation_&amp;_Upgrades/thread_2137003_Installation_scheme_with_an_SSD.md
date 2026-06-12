---
title: "Installation scheme with an SSD"
date: 2013-04-19
forum: Installation &amp; Upgrades
---

### Post by gentix on 2013-04-19
Hello, my apologies if this question has been asked before; I'm sure it has, but I couldn't seem to find it. I just bought by first laptop, which I am very excited about. It is going to be great. I'm planning on installing Ubuntu on it as I will need linux and Ubuntu is my favorite flavor. I will have a 16GB SSD and a 1TB HDD. I haven't used SSDs before, but from what I have read I have taken away two main things. 1) SSDs are obviously very fast at reading, so you wan to put boot files on it. 2) Frequent writes can be bad for the health of the drive.

That in mind, some questions:

I'm thinking I will want to put /home and /usr on partitions on the conventional drive and everything else on the SSD. Or is a better route to put just /boot on the SSD and everything else on the conventional? I assume that swap should go on the conventional.

I read somewhere about disabling "access time" writes to files on your SSD. Is that recommended?

Finally, I read a couple of years ago that it's a good idea to leave some of your SSD unallocated. Is that still true?

Thanks! ):P

---

### Post by darkod on 2013-04-19
The thing is that in /home you have some hidden folders with settings and configuration of programs. So if /home is on the ssd it will load faster.

I know that by default the personal data is also in /home, but you can easily make another big partition (mount point) on the hdd and keep your personal data there.

The swap should be on the hdd.

I would put / on the ssd with boot and home inside it, but make sure you don't forget to save all big data outside of Home in that case.

Also if you need much space for /usr, put it on the hdd. Do that with any mount point you expect to need large space.

You usually leave the first 1MiB unallocated, I don't need you need to leave more. Besides, newer SSDs have moved a lot since the first generations.

For the / partition on the ssd, I only have added discard and noatime to the options in fstab. The discard option is doing the TRIM function, and the noatime helps with writes. I think that is the access time writes you mentioned.

16GB is a little bit small, but you should be OK as long as you keep any big data and programs on the hdd.

---

### Post by dabl on 2013-04-19
Yes what darkod said.

Plus, here are a couple of further things to consider:

- default ext4 journal commits are every 5 seconds, but you can slow it down with the "commit=nn" mount option in /etc/fstab

- you can mount selected filesystems as tmpfs (i.e. in memory)

- you can use /run/shm as a location for browser caches (i.e. in memory)

I wrote a piece on the topic in late 2010 -- it is [**[color=green]here[/color]**](http://siduction.org/index.php?module=news&func=display&sid=78&lang=en).  You can safely disregard the initial part regarding detailed partitioning with fdisk, just let the GParted start the first partition at 2048 which is default. Further down is guidance on tmpfs filesystems and browser cache relocation.

EDIT:  Upon review, I see another error -- there was an experiment of placing the journal commit setting under pm-utils at the time, but that has been deprecated and it is once again controlled by a "commit=nn" mount option.  I personally use commit=120, giving a 24X reduction in the journal write frequency, while retaining the benefits of an ext4 filesystem, with journal.

---

### Post by prodigy_ on 2013-04-19
It's a bad idea to put /home on a small SSD unless you disable disk cache in all web browsers (and maybe some features in other apps that cause frequent writes). On the other hand performance-wise it's a bad idea to put /usr on HDD (though with 16GB SSD it may be the only option).

And you definitely want /tmp and /var (or at least /var/log) on HDD.

---

### Post by oldfred on 2013-04-19
I keep /home on the SSD, but have all data including Firefox & Thunderbird profiles that are normally hidden folders in /home on hard drive. I also move anything that starts to get large to hard drive data partition and link it back into my /home. 
I had not thought about the caches but by moving the profiles I (accidentally) solved the issue by moving just about everything.

       With SSD or Flash drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode for trim to work.
change to noop i/o scheduler
But per this noop may not now be best.
[http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1)


 Arch suggests gpt partitioning for SSD. Only if installing Windows on older system may you want MBR as Windows only boots from gpt with UEFI. 
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

