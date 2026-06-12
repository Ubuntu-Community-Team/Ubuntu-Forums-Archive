---
title: "Dual Boot Netbook Remix &amp; WIN XP - Xp is not detected"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by smoh on 2010-11-07
Hey all,

I'm trying to dual boot Netbook remix and win xp on my Samsung NC10 netbook. 

I'm booting from my usb stick and everything works perfectly until it comes to the partition part. It says that my ENTIRE hard drive is 'unallocated space' and it says that it'll wipe the entire hard drive, meaning my xp install as well. 

I was watching a YouTube video and this guy who has Windows 7 just created a new partition and his Netbook Remix 10.10 version detected his xp version on there and gave him the option "Install alongside other operating system"

On mine, it only gives me the other 2 options...

1.) erase the entire disk
2.) specify partitions manually (advanced)

[http://www.youtube.com/watch?v=T8mc-g1Gj20](http://www.youtube.com/watch?v=T8mc-g1Gj20)

I was wondering why I can't install onto my D:\ partition. I just created it and formatted it using NTFS.  Better yet, why is ubuntu netbook remix not seeing my XP? When I go to option 2 - specify partitions manually, it shows the /dev/sda2 but makes me format the entire drive.

When I go to gparted, it shows the entire 150gb hard drive as "unallocated space" 

Can anyone help provide a solution for this?  

It's also noteworthy to say that my boot screen looked different than his.  It booted right away into the screen where it says "Try Ubuntu" and "Install Ubuntu". I had to click Try Ubuntu to get to gparted etc. 


ANY help would be greatly appreciated. I'm a linux noob.

---

### Post by smoh on 2010-11-07
I've also tried wubi but then I got an error that said no root file found? I can't remember the exact error message but it had somethign to do with a root folder or file.  Is there a fix to that if I install through WUBI?

---

### Post by Quackers on 2010-11-07
Bearing in mind that Ubuntu won't use an NTFS partition to install to, does XP occupy all your disc space at the moment?
Or have you resized the XP partition? And if so, how did you do that please?

---

### Post by smoh on 2010-11-07
I didn't resize my C drive.  I formatted my D drive which really didn't have anything important on it.  I used EASEUS partion master to format this drive. I've used this in the past to create a hackintosh and worked lovely. 

I want to keep my C and D drives separate. I'm doing a disk defrag on my C drive at the moment but I have a feeling that it won't do anything...

Thanks for responding! I appreciate your interest in helping out!

---

### Post by Quackers on 2010-11-07
After defragging your C: drive, and as you've already formatted your D: drive, what I would do is delete the D: drive partition, so that it becomes unallocated space. Then try installing Ubuntu again. I'm not sure whether the "side by side" option still exists in the 10.10 installation. See what is offered during the partition stage and, if possible, choose the unallocated space to install Ubuntu (or choose the manual partitioning option and use only some of the unallocated space).

---

### Post by smoh on 2010-11-07
Seems like the defrag and deleting of D:\ worked! I'm having a little trouble on the partitions I should create. I've been reading some articles on setting up a /boot a / a /home and a swap partition.  I can't create that many partitions since I already have my recovery partition, my C drive and an 'unknown partition'.  

I can basically create 2 more partitions.  which ones would you recommend and what size should I allocate to them? I have about 75 gigs to allocate in free space.

---

### Post by Quackers on 2010-11-07
I don't think anything will be gained by a /boot partition. I would make a root partition (mount point "/") of 8GB to 12GB and a swap partition (no mount point) of a size slightly bigger than the amount of ram you have (if you want to use hibernate) and the rest should be for your home partition (mount point /home), or as much as you want to have for your personal files and settings etc.

---

### Post by wilee-nilee on 2010-11-07
> **smoh said:**
> Seems like the defrag and deleting of D:\ worked! I'm having a little trouble on the partitions I should create. I've been reading some articles on setting up a /boot a / a /home and a swap partition.  I can't create that many partitions since I already have my recovery partition, my C drive and an 'unknown partition'.  

I can basically create 2 more partitions.  which ones would you recommend and what size should I allocate to them? I have about 75 gigs to allocate in free space.

You need a extended partition to put the others into, Linux that is. The extended allows as many partitions as you can fit. Windows needs a primary partition to boot Linux doesn't

---

### Post by smoh on 2010-11-07
Should all of them be primary or logical? or a mix?

---

### Post by smoh on 2010-11-07
Also, I can only create 2 partitions.  I've set them all as EXT4 except SWAP. I'm guessing the 2 i should do is EXT4 at 12gb for / and the rest to /home also on EXT4 since I can't use swap.  Kind of annoying that I cant create more

---

### Post by Quackers on 2010-11-07
As wilee-nilee says, Linux can boot from extended (or logical) partitions, they don't need to be primary. Windows is the only one that insists on primary partitions to boot from.
ext4 is now the default file system for Ubuntu.

---

### Post by wilee-nilee on 2010-11-07
> **Quackers said:**
> As wilee-nilee says, Linux can boot from extended (or logical) partitions, they don't need to be primary. Windows is the only one that insists on primary partitions to boot from.
ext4 is now the default file system for Ubuntu.

Thanks I'm worn out with tutoring.;)

---

### Post by Quackers on 2010-11-07
> **wilee-nilee said:**
> Thanks I'm worn put with tutoring.;)

Yes, sensai :-)

---

### Post by smoh on 2010-11-07
Found another thread on creating an extended partition.  hahaa. Like I said, Linux noob here.  Thank you BOTH so much in helping out with this process and being patient with me.

To all the other linux noobs out there that ran into the same problem

**Problem: **Wanted to dual boot xp and ubuntu but linux installation only gave unallocated space. Meaning I would have to wipe my XP drive. 

**Solution:** 
1.) Defrag your XP partition. 
2.) Create free space - unpartitioned in xp using your favorite partitioning tool
3.) Boot w/ ubuntu netbook 10.10
4.) Click "Try Ubuntu" 
5.) Click on the menu button (top left) and type partition in the search box.  Select g parted
6.) Create an extended partition and add whatever you'd like there. I used 1 partition at 1.5x my ram size + 10gb 
7.) Create SWAP at 1.5x your ram size 
8.) Create ext4 with 10gb 
9.) Click Install -> Click to manually configure your partitions
10.) Format your 10gb mounted on as / 
11.) Format the rest of your desired space for files etc as ext4 mounted on /home.  I set it to Primary. 


Once again, thank you two for helping out.

---

### Post by Quackers on 2010-11-07
[Solved] is always nice to see :-) You're welcome.

---

