---
title: "[SOLVED] Need Help Migrating From Windows"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by DouglasT on 2008-12-01
After installing Ubuntu with the live disc's "Install Inside Windows" option and using it for a few days, I've decided I want to permanently switch to Ubuntu.

Also, (I think this is due to the Install Inside Windows option I used and would be solved if I did the overwrite I'm planning), I can't save (large) files anymore, it tells me the disk is full (and a torrent I had running stopped)

I have the system set to mount my C: drive on boot so that I can access my Windows files. Gparted tells me I have two partitions (note, I don't know how to use partitions very well yet) a /dev/sda1 ntfs of 74 gigs, my hard drive with Windows on it, which I have set to mount on boot. 

And I have 8 megs of unallocated disk space, so I assume this is where Ubuntu is running from. 

My question is, what would be the best and safest way to save all of my files in C: and overwrite Windows? 

To me, buring the files on the Windows /dev/sda1 partition that I want to save to discs, booting back inside Windows, uninstalling Ubuntu as if it where some software, and then using the live disk to install over Windows sounds like my best bet, but I want to hear what you guys think. 

Thanks in advance for any tips!

---

### Post by Idefix82 on 2008-12-01
You have two options:
[LIST=1]
[*]either burn the data to discs, restart with the Live CD in the CD rom, tell your BIOS to boot from CD and install Ubuntu into the Windows partition,
[*]or resize the windows partition, create a separate partition with GParted, call it Data or something like that, copy your data that you want to keep from Windows partition to the new partition and then install Ubuntu into the Windows partition, keeping the new partition untouched.
[/LIST]
I would probably opt for the first option. The Ubuntu installer will offer you the option to use the entire hard disc and do everything for you, so the installation should be very easy.

---

### Post by albandy on 2008-12-01
The 8 MB unallocated space is free disk, not used by ubuntu.
If you installed ubuntu with wubi all the ubuntu files ar in c:\ubuntu

You can backup your home directory using tar in a big pendrive for example:

tar zcvf /pendrive_dir/home.tgz /home

then you can reinstall ubuntu using the entire hard disk (windows will be deleted)

after this, you can restore your backup:

cd /
tar zxvf /pendrive_dir/home.tgz

---

### Post by Mark Phelps on 2008-12-01
Here's a link that discusses moving the Wubi installation to a separate partition:

[http://ubuntuforums.org/showthread.php?t=438591]("http://ubuntuforums.org/showthread.php?t=438591")

Just be sure that nothing you need to do requires MS windows to do it -- and forget about using Wine as a substitute.  I converted some time back, spent months not getting Wine to run ANYTHING useful, and finally decided to learn how to do everything I needed with Linux apps.  That works for about 90% of what I do.

But I still need Windows for the other 10%  because I have hardware and apps for which there is no real Linux "substitute".  So, I keep a multi-boot machine in place for the once or twice a week I have to boot into Windows.

So, you might want to consider multi-booting as an alternative for a while.  It will be a LOT easier then to remove your MS Windows install and switch over to Linux full-time.

But, that's only my opinion...

---

### Post by DouglasT on 2008-12-01
Thanks for the tips everyone but:
"The 8 MB unallocated space is free disk, not used by ubuntu.
If you installed ubuntu with wubi all the ubuntu files ar in c:\ubuntu"

If thats the case, then why does it tell me that my disc is full? I still have 17 GB free. 

This really isn't necessary to know, considering I plan to overwrite it anyway, but it would be nice to know why my Wubi installation is acting up.

---

### Post by albandy on 2008-12-02
> **DouglasT said:**
> Thanks for the tips everyone but:
"The 8 MB unallocated space is free disk, not used by ubuntu.
If you installed ubuntu with wubi all the ubuntu files ar in c:\ubuntu"

If thats the case, then why does it tell me that my disc is full? I still have 17 GB free. 

This really isn't necessary to know, considering I plan to overwrite it anyway, but it would be nice to know why my Wubi installation is acting up.

Because you defined the size in wubi installation.
wubi makes a fixed size file (like an iso image) where are all ubuntu files.

---

