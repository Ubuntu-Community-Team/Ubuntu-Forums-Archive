---
title: "disk confusion after install refuses to boot first hard drive"
date: 2014-03-14
forum: Installation &amp; Upgrades
---

### Post by jim_smith2 on 2014-03-14
Hardware:  AMD 64 system with IDE 200 GB HD and CD on channels one and two
                3 SATA 2TB drives (someday will become a raid 5 array for media server)
OS:           Ubuntu 12.04.4 Server

Steps to reproduce problem.
  1.  Use 12.04.4 server CD iso to install server 
  2.  Choose the 200GB IDE drive which displays as sda for the boot drive
  3.  Complete the install using standard choices
  4.  When install routine asks where to install grub, choose sda drive which should be the server installation drive.
  5.  When install completes, follow instructions to remove cd and reboot.

And that's when the fight started!
  The first five times i tried this I was so puzzled I kept doing the same thing over and over again expecting different results, not the brightest choice, I know.

  I used bios settings to attempt to choose the boot drive, but alas, I can only choose FDD, First Hard Drive, CD, various USB devices.
  Then I checked bios setting to see what drives were being detected.  (I know, it seems silly, after all, it detected the drive just fine for the installation just completed).
  The drive was NOT showing up.  thinking...thinking... oh yeah, those IDE drive have jumpers and cable select and other nonsense.  So I added another ide cable to the motherboard and put the hard drive on its own ide channel and rebooted to the bios and presto, drive was recognized.  I was laughing happily as I rebooted thinking the
problem was solved!  FAIL.   Grub not found or whatever, anyway, it refused to boot from hard drive.

Back to install CD boot up, reinstall to the same sda 200GB drive I've installed to 4 times now.  Yet another reinstall.  Disk recognized fine, used single disk install everything to that disk, standard defaults on all choices, and then the remove cd and reboot screen.  I held my breath looking for success....and about suffocated myself.  

Same blankety blankety blank crapola, refusing to boot off the drive where it just finished installing the os and grub.  

I am not a total noob, having started with DOS 1.0 and Basic 1.0 in the early 80's, followed by OS/2 for a few years tried to avoid windows as long as possible.

Anyone who takes a little time to point me in the right direction for a solution will earn my undying gratitude.  I'm at my wits end here.

Thanks for listening and have a wonderful day whatever is left of it where you are.

Best Regards,
Jim Smith

---

### Post by oldfred on 2014-03-14
Best to see details.
 
Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

But with old IDE/PATA drives it can be confusing. I really really hated those tiny jumpers, so when I built my "new" system in 2006 and SATA drives were on $10 more I converted to SATA only. But if newer PATA system with cable select you must have 80 conductor cables & jumpers on cable select. I once tried a 'new' 40 conductor cable from a CD and that of course did not work.
If only a hard drive jumper system with primary & slave, I think you only can boot from primary.

      
 with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

   If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by jim_smith2 on 2014-03-14
Thanks so much for your input with many great links.  I can see I'll be even more busy for a little while sorting this out.

I will not forget to report back my results.

Thanks again for your kind assistance.

Best Regards

---

### Post by ubfan1 on 2014-03-14
The BIOS and grub enumeration of disks may be quite different, so you may have to edit the hard disk's grub.cfg file to get the first boot.  Boot the live media, (and if it's USB, that likely will alter the enumeration too, so some guesswork or trial and error is involved in this). Mount the hard disk and take a look at the /mnt/sdx/boot/grub/grub.cfg file.  Where the uuids are used, those are OK, but where you see actual device partitions like /dev/sdb?, consider those edit candidates.  Also any reference like (hd1,...   may need to be changed.  The likely changes with a USB live media is to reduce the letter/number on the disk by one (the partition numbers should be OK).  You can investigate the disks at grub boot time (on the live media) by entering a "c" for the grub command line and then using the <TAB> for completions on commands like 
set root=(hd <TAB>
and get a list of candidates.  Once the disks are identified, you can use ls or even more tab completions to determine which is the disk you want to boot.  Use that number for edits (or one less if doing this from a USB live media).  
After the first successful boot of the hard disk, immiediatly run sudo update-grub to hopefully fix things permanently.

---

### Post by jim_smith2 on 2014-03-14
> **oldfred said:**
> Best to see details.
 
Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.


Well, that is a wonderful tool (Boot-Repair) at the link above.  I can not figure out why I never had that before.  Thanks so much for linking me to it.

It has been an interesting afternoon.  Firstly the forums went down right after my last post but that does not matter, as I have been working like a mad man tweaking and rebooting over and over.

When I say umessage, this is what I mean:   Disk Boot Failure, Insert System Disk and press Enter

1. [http://paste.ubuntu.com/7091098/]("http://paste.ubuntu.com/7091216/")     before I attempted anything else after your post repair

2. Attempted grub repair using the booted cd and which resulted in this: [http://paste.ubuntu.com/7091216/](http://paste.ubuntu.com/7091216/)  umessage

3. Deleted all partions on the 3 2tb drives with gparted resulting in this:  [http://paste.ubuntu.com/7091296/]("http://paste.ubuntu.com/7091216/")  umessage

4. Created new partions on all 3 2tb drives with gparted resulting in this: [http://paste.ubuntu.com/7091404/]("http://paste.ubuntu.com/7091216/")  umessage

5. Dropped to terminal and ```
#sudo dd if=/dev/zero of=/dev/sda bs=446 count=1
``` resulting in this: [http://paste.ubuntu.com/7091586/]("http://paste.ubuntu.com/7091216/")  umessage

6. Dropped to terminal and ```
#sudo dd if=/dev/zero of=/dev/sdb bs=446 count=1
``` resulting in this: [http://paste.ubuntu.com/7091786/]("http://paste.ubuntu.com/7091216/")  umessage

7. Now that I have all of the mbr records removed except for the sdc drive I'm trying to reinstall the server to see if the fixes "took".  I made a booboo on the
    one of the mbr removals and used sdc and also had 512 for the size instead of 446.  Anyway, I'm hoping I'll have success soon.  

I'll update you as soon as possible.

thanks again for your invaluable assistance.

Best Regards

---

### Post by jim_smith2 on 2014-03-14
Thank you, OldFred, I have got to learn more about this on a daily basis, and you have certainly been my teacher today!  

Thank you sir for your kindness and promptness and most of all, for coming up with some tools which I desperately needed to be able to solve the problem on my own.  DIY is always the best way to learn, assuming you have good guidance, and I certainly did today.  

I learned about some really cool tools of the trade to make all this work.

I learned the syntax of getting rid of mbr via dd and the pitfalls with using the wrong size blk!  446 gets rid of mbr but 512 trashes the partions, too!

Before I even posted the problem I had already figured out that I had a hardware problem dealing with those old ide interfaces and switched my drive to a new cable.  Fortunately I still have a lot of old parts available here and was able to put a new cable in on the opposite channel from my cd/dvd drive which is also ide.

All in all, it has been a productive day, and I have not yet explored those other links you so graciously provided, but I intend to do so while the server churns and burns and gets setup to serve our entertainment and allows automated backups.

Thanks again for your timely assistance!

Best regards to you and yours,

Jim Smith
On the banks of the Suwannee River here in White Springs, Florida, USA

---

### Post by jim_smith2 on 2014-03-14
Thank you ubfan1 for your comments,  I did immediately run sudo update-grub after I finally successfully booted into my server 3 times in a row without error. :)

It was a struggle, but together we achieved it.

Friendship multiplies joy and divides grief!   - author unknown

---

### Post by oldfred on 2014-03-16
Glad you got it working. :)

---

