---
title: "disk partitions"
date: 2011-09-19
forum: Installation &amp; Upgrades
---

### Post by Junior3327 on 2011-09-19
I have a 1 tet. HD, a 1.5Tet HD and am thinking of installing Ubuntu 11.04 64 bit on a seperate 500Gig HD or maybe the 1.5Tet. What would be the best way of partitioning the 500 or the 1.5. The 1.5 is currently my D: drive under windows 7. It would not be a problem for me to use the 500 or another drive for the D: and use it for Ubuntu 11.04. I have read too much information on partitioning and am somewhat confused. Any help would be greatly appricated.  I have 12 gigs of Ram and a quad 3.0 processor in this system. This will be my first move to trying Linux (Ububtu).
Thanks in advance.

---

### Post by drs305 on 2011-09-19
Junior3327,

Welcome to Ubuntu and the Ubuntu forums.

There are lots of opinions.

A basic Ubuntu installation takes a bit less than 5GB. I'd use a minimum of 10GB and considering the size of your drives probably 15-20GB, which is more than enough *for the system*. If you plan on keeping data/music/etc in the /home partition, which is where Ubuntu thinks you will keep stuff, increase the amount of space by the amount of data you intend to keep within, plus growth. (If you have 50GB of data, make the partition a minimum of 60GB plus extra space for new data). * See later.

A small swap partition will be created during the installation. You don't need to specify one. If you want to create it before installing, depending on the amount of your memory, 2-4GB is probably about right. No more.

Some users like a separate /home partition, others don't. The advantage is that if you do an online upgrade to the next release you can save a lot of your customized configurations during the upgrade. Many users always do a clean install of the next release and reformat the partition. To them a separate /home partition is not as important.

I keep all my data in a separate data partition - not even in /home. It's a personal preference.

* A note on partition size and location. No matter what you decide, I would place all the Ubuntu system partitions (/, /home) within the first 130GB of the drive unless you know your BIOS recognizes the entire disk size or you are going to use an advanced partitioning table such as GPT. (GPT has it's own partition requirements, which I haven't addressed here. If you plan on GPT partitioning, I think you will need an additional small partition. Search for posts by *srs5694*). The reason for the 130GB is that many BIOS's, older ones especially but even some of the newer ones, can only 'see' the first 137GB of the drive. If the boot files end up past that part of the drive, Grub won't be able to find them and boot.

---

### Post by underquark on 2011-09-19
> **Junior3327 said:**
> I have 12 gigs of Ram and a quad 3.0 processor in this system.
This sounds like a fairly up-to-date system.  That being the case, your PC will usually give you options at start-up including pressing a key (e.g. F12) to access the boot menu or of entering the BIOS setup and choosing which disk to boot from.  You can keep Windows 7 on the 1TB drive (or wherever it is at present), install ubuntu on the 500GB drive and just choose to use the whole of the 500GB drive and accept the default partitions including the swap file.  What you do with the 1.5 TB drive is up to you.  I use mine to store large files (video, music) and keep "normal" documents on my ubuntu drive.

---

### Post by drs305 on 2011-09-19
*underquark* brought up something I meant to address and didn't - the advantages of putting Ubuntu on the 500GB drive.

By putting it on that drive, you can disconnect the other drive during installation. This will do two very helpful things.

First, it will ensure your Windows installation doesn't get overwritten by mistake.

Second, Grub 2 will write to the 500GB MBR. You will need to change the BIOS settings to ensure your Ubuntu drive is the first drive in boot priority. This will boot Ubuntu, and after you boot and reconnect your Windows drive, you can run "sudo update-grub" so it finds Windows and includes it in your Grub boot menu. 

The second advantage of this method is that the Windows drive MBR is not touched. Should there be a time that Grub 2 fails, you can change the BIOS boot order back to Windows and your Windows will boot just as it did before installing Windows. Or if you prefer, you could write the Grub code to the Windows MBR as a backup (but I'd not).

---

### Post by oldfred on 2011-09-19
As drs305 says you will get many opinions and none are really wrong.

I prefer smaller system partitions of 20-25GB (since you have the space) and keep data separate either /home or data partitions. You already have a d: drive which is a NTFS data drive and useful as the shared partition. It is best not to write into the windows C: drive as eventually Windows will complain or you may accidentally move a system file as Ubuntu will show all files including those Windows normally hides.

I keep my Firefox & Thunderbird profiles in my shared NTFS partition so in my XP install I have exactly the same email & bookmarks as Ubuntu.

You do want to be sure to install the grub2 boot loader into the MBR of the drive you install to and keep the Windows drive with its boot loader. Grub will let you boot either system where Windows will only boot Windows.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by Junior3327 on 2011-09-19
I thank you for the reply. It looks as if I have more than enough to run Ubuntu with windows by dual booting. I will probably keep the 1.5 tet for data, movies, music, etc.
Thanks again.
Junior

---

### Post by Junior3327 on 2011-09-19
I thank you all for your replies. It looks as if I have more than enough to run Ubuntu with windows by dual booting. I will probably keep the 1.5 tet for data, movies, music, etc. as you suggest. 
Thanks again.
Junior
P.S. I will disconnect the Windows drive during installation of Ubuntu. Again I thank all of you. I will let you know how I make out as soon as I do the install, should be this week.

---

### Post by jalirious on 2011-09-21
After installing the 11.10 64 beta I was a bit annoyed -

I have 10.04 32b and a 64b OS's sharing the same home partition.

For a previous installation of 11.04, during installation I was sure not to check "format partition" for home.

It worked fine.

For 11.10 I was also sure (and retried to check) not to check "format partition" for home.

However, it selected it automatically upon closing the 'edit partition' window. I didn't notice and it formatted my home partition (losing valuable data).

There did not seem to be a way -not- to format the /home partition. I realize this will not affect the majority of users, but could the developers sort this out please.

---

