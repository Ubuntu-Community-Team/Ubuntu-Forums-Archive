---
title: "Pre-install RAID question"
date: 2013-09-10
forum: Installation &amp; Upgrades
---

### Post by Coder88 on 2013-09-10
I have an ultranotebook (Acer Aspire S5 with Windows 7) configured from the factory as RAID0 for speed by using raid with its two 128GB sata drives. My goal is to convert the laptop to a dual boot with Win7 on one drive, Ubuntu on the second drive. How to prepare for this without losing the Windows 7? I have never done e.g. a Clonezilla disk image clone of a dual-drive raid0 operating system before. Not sure what to expect if I boot a Clonezilla live CD and attempt to do an image clone, what to clone, and will the resulting cloned disc image restore okay to a single non-raid disc when I go to convert to two drives each with its own operating system. And per the BIOS, I will have a choice (after I first do a clonezilla image backup of the existing Windows 7 OS) to change the drive configuration from RAID to IDE or ATAPAI-- which should I choose, IDE or ATAPI at that point?

---

### Post by lukeiamyourfather on 2013-09-10
ATAPI is for removable media and optical drives. The IDE mode is for non-removable storage like hard disks and SSD. I've never tried to create an image from a RAID 0 array but my guess is you won't be able to, or even if you can Windows probably won't boot when you're done. If you're able to get it to work please post the results here.

---

### Post by Kevin_Arnold on 2013-09-10
As long as whatever clone utility you use has drivers for the RAID array, it won't really even know/care that it on a striped setup, it just gets data from the controller. The only issue I could see is when you disable RAID and then reload it on a single drive and boot up, windows might mess up because it will still have the raid driver set... should be pretty easy to fix though.

---

### Post by Coder88 on 2013-09-10
I did an Acer recovery disc set creation as well as an Acer Drivers recovery disk, just in case this all goes wrong. I checked with Gparted and the laptop (raid0 with two 128GB SSD drives configured as a super fast 256GB SSD drive) shows up as shown below. I am thinking (asking here) I should leave the RAID0 intact, and see if i could shrink windows 7 and see how much of that **70 GB unused space** I can safely free up? Then create a partition using as much of that 70GB that I can, to put Ubuntu on? This laptop would be primarily for writing, listening to music (music could be on my amazon cloud music or on the Windows drive), browing the web, email, so I don't need a ton of space, I could go with a lightweight version of ubuntu, minimal package set of apps or remove unneeded apps? Any thoughts on the next step? How much space at a *minimum* do you think I need to go for for a decent Ubuntu install-- 20GB? (including / and home)

Or dare I disable the RAID0 and try to restore the system to one 120GB ssd drive as an IDE? I fear that will somehow break the system, but wow that would be ultimate if it worked, two separate drives, one for Win7, one for Ubuntu and Grub2 bootloader.  I actually would even be willing to buy another copy of Windows 7 if needed to rescue an IDE ssd 120GB drive, thought it would be very inconvenient to be without the laptop for that week or so waiting for an $80 Windows 7 OEM disc to arrive in the mail.

3 devices or drives:
/dev/md126 (240GB)
/dev/sda (120GB) "Unallocated)
/dev/sdb (120GB) "Unallocated"

The "unallocated" sda and sdb are obviously a bit of a ruse, not empty at all, just combined as RAID0 to form that 'virtual' 240GB /dev/md126

The /dev/md126 drive is partitioned as follows (I am guessing partitions 1,2,3 are part of the Acer system recovery, contain a rescue version of Windows 7 and the drivers):

partition 1: unknown 8GB
partition 2: ntfs PQSERVICE 16GB
partition 3: ntfs SystemReserved 100MB
partition 4: extended 214 GB (contains    **partition 5**: ntfs Acer 214 GB with **70 GB unused**)
unallocated: 1MB

---

### Post by Coder88 on 2013-09-10
I got free space increased to 90GB and Windows 7 says it can shrink the raid drive down 90GB, so I think I will shrink partition 5 down 40GB and then use that 40GB for an ubuntu install, should be plenty for basic coffee shop laptop work writing, music, browsing, email, GIMP, etc. I can use a bootload manager other than Grub, there are Windows based bootload managers that simply provide a GUI interface to the native Windows bootloader, I can use that to manage Win7 and Ubuntu, avoid Grub. This way I keep the raid array for speed, less risk of completely messing up the laptop.

---

### Post by lukeiamyourfather on 2013-09-11
Nice, 40GB should be sufficient for Ubuntu. You can use EasyBCD to modify the Windows boot loader instead of using GRUB as the primary boot loader. Not sure how that will play with RAID though, it might require some tinkering to get working.

In the future I'd avoid RAID 0. None of the tasks you perform on the machine merit RAID 0, especially with SSD. It's less flexible than JBOD and less reliable. It should really only be used in situations where the throughput of a single disk simply isn't sufficient for a given task (live video capture, realtime playback large caches or media) but even then a RAID 5 array or RAID 10 array might get the job done without the reduced reliability of RAID 0.

---

### Post by Coder88 on 2013-09-11
yes the raid may be the rub (problem); i was able to make an ext4 40GB partition on the laptop 'raid' disk, but i am unsure if i will be able to get ubuntu onto that partition, and without any grub install (i do not want to write over the Windows 7 MBR). if i can not get Ubuntu on that partition, I might just order an $80 copy of Windows 7 OEM and wipe the raid and wipe the two ssd drives and set the drives as two IDE drives in the bios. I have rescue recover DVDs if it all goes bad.

---

### Post by lukeiamyourfather on 2013-09-11
No need to buy another copy because you already own one that came with the laptop. You can use any vanilla Windows 7 disc to reinstall, just use the key on the OEM sticker.

[http://www.pcworld.com/article/248995/how_to_install_windows_7_without_the_disc.html](http://www.pcworld.com/article/248995/how_to_install_windows_7_without_the_disc.html)

---

### Post by Coder88 on 2013-09-11
> **lukeiamyourfather said:**
> No need to buy another copy because you already own one that came with the laptop. You can use any vanilla Windows 7 disc to reinstall, just use the key on the OEM sticker.

[http://www.pcworld.com/article/248995/how_to_install_windows_7_without_the_disc.html](http://www.pcworld.com/article/248995/how_to_install_windows_7_without_the_disc.html)

Don't have that. I do have rescue discs for the laptop, set of 4 (and a drivers rescue disc), but that is not like a Windows 7 OEM disc. I wonder if I could download legally windows 7 from microsoft.com and then use my serial number for the copy of Win7 i own that came with my laptop? That would make too much sense.

I am actually think of just scrapping Win7 on the laptop rather than have to buy a copy of Win7. Just make a kick-**** linux laptop.

---

### Post by lukeiamyourfather on 2013-09-11
Click on the link in my previous post and read it, your questions will be answered. If you don't want to dual boot that's cool, just trying to help.

---

### Post by Coder88 on 2013-09-11
> **lukeiamyourfather said:**
> Click on the link in my previous post and read it, your questions will be answered. If you don't want to dual boot that's cool, just trying to help.

Nice. I should have read that before, just been so busy with these linux problems, installing, reinstalling, ugh. You saved me $. I will give it a try. I think I am going to remove the raid0, then install Windows (vanilla method) to one IDE ssd drive, then see if it boots into windows; if so i will put Ubuntu on the second IDE ssd drive and put grub2 on that drive. If Windows fails to install and boot to an IDE drive (no more raid), I think I will (for now) just trash windows on the laptop and make it a linux laptop.

---

