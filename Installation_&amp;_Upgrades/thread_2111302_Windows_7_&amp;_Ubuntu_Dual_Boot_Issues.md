---
title: "Windows 7 &amp; Ubuntu Dual Boot Issues"
date: 2013-02-01
forum: Installation &amp; Upgrades
---

### Post by Piersadept on 2013-02-01
I just installed Ubuntu on my hard drive that has windows on it. The installation goes great. No problems, it gets to the point where it says it has to restart. After it restarts Windows boots up, I don't get an option to boot Ubuntu anywhere. I downloaded Easy BCD2.2 and It doesn't show Ubuntu in the Edit Boot Menu options. How do i boot from Ubuntu?

---

### Post by Mark Phelps on 2013-02-01
Can't answer until we know HOW you installed Ubuntu.  There are two very different procedures and the solution to your problem depends critically on which one you used:
1) Installed from INSIDE Windows using Wubi
2) Booted from an Ubuntu install CD/DVD/USB, shrank the Win7 partition, and installed to a separate Linux partition.

---

### Post by Piersadept on 2013-02-01
I booted from the Ubuntu Install on my USB drive. I shrank my Windows Partition and installed Ubuntu on that.

---

### Post by oldfred on 2013-02-01
Best to see what is where:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Piersadept on 2013-02-02
I couldn't get my USB one to work so I installed with Wubi. It loads up fine, but now my user/password wont work; the one I set. I can only log in with Guest, and I don't have access to do most anything as a Guest. Is there a way to force reset the Root password and let me create an admin user through the guest account?

---

### Post by presence1960 on 2013-02-02
> **Piersadept said:**
> I couldn't get my USB one to work so I installed with Wubi. It loads up fine, but now my user/password wont work; the one I set. I can only log in with Guest, and I don't have access to do most anything as a Guest. Is there a way to force reset the Root password and let me create an admin user through the guest account?

Wubi is OK. Do you know it is not meant to be a permanemt installation? It is meant as a test drive only for those unwilling to commit to altering their partition scheme until they see if they like Ubuntu. I realize a lot of people use wubi as a permanent installation, however when it breaks as it does a lot they expect miracles to get it running again.

Read this: [http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Read the answer to the second question in the interview.

---

### Post by Piersadept on 2013-02-02
Should I just go out and buy a DVD and burn the Ubuntu instillation ISO onto it and run the instillation from there then? Seems everywhere I go that is the best solution.

---

### Post by Kixtosh on 2013-02-02
> **Piersadept said:**
> Should I just go out and buy a DVD and burn the Ubuntu instillation ISO onto it and run the instillation from there then? Seems everywhere I go that is the best solution.Short answer: YES!

Long answer: YES, absolutely!

At least, in my opinion! I've never encountered an issue yet when installing Ubuntu from a disk image alongside Windows to dual boot.

Remember to use Windows to shrink the Windows partition first though. Windows doesn't like anything else tampering with it's partitions. You should defragment your Windows partitions thoroughly before shrinking. I usually run the defrag tool about three times to do this. It goes faster with each subsequent run.

So:

[LIST=1]
[*]Defragment Windows partitions, and then do it again, and then do it again.
[*]Shrink Windows O.S. partition using Windows.
[*]Download Ubuntu and use the disk image to burn a LIVE CD (or DVD).
[*]Install Ubuntu alongside Windows.
[/LIST]

---

### Post by Piersadept on 2013-02-02
I've got 3 hard drives, one specifically for Windows and a few games. It's only a 120 Gig SSD. The other two I have are for storage. One is full, and my 2 TB drive still has 1TB free. Could i just install Ubuntu on my 2TB drive. So i don't have to mess with the Windows Partition?

---

### Post by Kixtosh on 2013-02-02
Well, you probably could, but I'm not familiar with that kind of installation, so somebody else will have to advise you.

However, just so that you know, I actually run a full version of Ubuntu alongside Windows on a laptop with a SSD. Windows requires a lot of space on the small SSD, but Ubuntu, on the other hand, will be quite happy with less than 10GB. In fact, if you don't save too much stuff from downloads, it'll fit into less than 5GB. Just remember that you'll need some space for the SWAP partition as well, maybe 2GB, so it'll probably take about 7GB in total. You'll get a big speed boost with Ubuntu if you can squeeze it into the SDD (mine boots in 17 seconds, on a SSD that has an average read rate of just 60 MB/s, so not even a very good SSD by today's standards).

---

### Post by presence1960 on 2013-02-02
> **Piersadept said:**
> I've got 3 hard drives, one specifically for Windows and a few games. It's only a 120 Gig SSD. The other two I have are for storage. One is full, and my 2 TB drive still has 1TB free. Could i just install Ubuntu on my 2TB drive. So i don't have to mess with the Windows Partition?

Yes. Make the disk you want to install Ubuntu on as first disk in hard disk boot order in BIOS. Install Ubuntu. Make certain in the drop down box for where to place GRUB you set the location to the disk (sda, sdb, sdc, etc) that has ubuntu on it, not a partition (sda1, sdb2, etc). When installation is done reboot and boot into Ubuntu. If all is well reboot and choose windows. Make sure windows boots fine. On installation GRUB should automatically detect and add your windows installation to GRUB boot menu.

The advantage to this method is you can boot either OS from GRUB, if need be you can make the SSD first disk to boot and boot straight to windows since windows boot loader is still on MBR of windows disk. GRUB is on MBR of Ubuntu disk.

---

### Post by Piersadept on 2013-02-02
Hrm, That's not bad. I'm new to Linux and Ubuntu. So I was assuming it would need the massive amount of space that windows requires. I could easily set aside 15 - 20 Gigs on my SSD for Ubuntu. Thanks!

---

### Post by Kixtosh on 2013-02-02
If you go the SSD route, then it'll probably be worth figuring out how to create your /home folder on it's own partition in your large 2TB drive. It's more or less the equivalent of a Windows My Documents folder. That way, all your downloads and saved documents will be all be added to that automatically.

It shouldn't be hard to do, but once again, I don't know exactly how to do it, so I won't try to advise you on the details!

---

### Post by Piersadept on 2013-02-02
I can't see that being too hard. If not when i download things I could just manually set them to install on my 2TB drive; that's what I do with Windows already.

---

### Post by Piersadept on 2013-02-02
Is there anything I should know before burning the ISO onto my DVD. I read that post you asked me too earlier Presence; It said a few times that people have had issues in the past installing from an ISO. Burning the image onto a disc with the speed too high, and other issues. I don't want to mess anything up.

---

### Post by presence1960 on 2013-02-02
> **Piersadept said:**
> Is there anything I should know before burning the ISO onto my DVD. I read that post you asked me too earlier Presence; It said a few times that people have had issues in the past installing from an ISO. Burning the image onto a disc with the speed too high, and other issues. I don't want to mess anything up.

If you follow those steps you should be OK with the burning.

---

### Post by Kixtosh on 2013-02-02
> **Piersadept said:**
> I can't see that being too hard. If not when i  download things I could just manually set them to install on my 2TB  drive; that's what I do with Windows already.
Yes, I think it is quite easy.

You could also manage it "manually", as you point out, but what I don't like about that idea is that Windows seems to hate it when something messes with files on disks that it will be sharing, so I would advise creating a separate partition in any case, just to avoid that possibility. It may not be necessary at all, so I wouldn't be surprised if others may suggest there's no need, but otherwise, creating partitions is very simple to do. Just make sure you defragment your Windows stuff first, and use Windows to shrink Windows partitions as well!

---

### Post by presence1960 on 2013-02-02
> **Piersadept said:**
> I can't see that being too hard. If not when i download things I could just manually set them to install on my 2TB drive; that's what I do with Windows already.

You can keep an NTFS partition on your other drive for all your data. Both Windows and linux can read/write to NTFS.

If you want to create a separate /home partition choose Something Else on the installer. When you get to the window that lists your partition table highlight the partition you wish to use as /home. Click change. Set mount point as " /home ". Keep file system as NTFS. **DO NOT TICK THE FORMAT OPTION** or your files will be toast!!!!

At this point you need to select the partition for ubuntu and set mount point as " / " and choose filesystem (most common are ext4 & ext3)and continue with install

Personally I don't create a separate /home partition, but rather have a partition (NTFS) for all my data.

You can always back up your home folder. It contains most of the settings for your installed software. So if you ever reinstall, upgrade with a clean install, etc you can copy that stuff over and retain your software settings provided you install the software to the new installation.

---

### Post by Piersadept on 2013-02-02
Well I followed all the steps to install Ubuntu from my DVD. It installed fine. When I got to the part to restart your computer. "Remove Media and hit enter" It spat out my DVD i took it out and hit Enter, It restarted and went straight to Windows. It did not give me an option to boot from Ubuntu. I didn't have this problem with WUBI.

---

### Post by Kixtosh on 2013-02-02
Are you installing from Windows? You need to boot from the LIVE DVD version and then install, from within the LIVE version of Ubuntu. Did you get your download from here?

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Do these instructions seem familiar?

[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)

---

### Post by Piersadept on 2013-02-02
Yes, i downloaded it from there and went through that installation. When i clicked restart now, It just booted straight to windows. I did not have an option to boot up Ubuntu.

---

### Post by Piersadept on 2013-02-02
I haven't tried going into my Bios and trying to change the Boot order. But with Wubi i had the option when i booted up to choose from Windows and Ubuntu.

---

### Post by Kixtosh on 2013-02-02
You should have got a GRUB screen (**GR**and **U**nified **B**ootloader) when starting up to choose between the different operating systems. It would have looked something like this, but with Windows entries as well (including recovery partitions, if there are any):

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Where did you end up installing Ubuntu? On the SSD or the 2TB storage drive?

---

### Post by Piersadept on 2013-02-02
I installed it alongside windows But i think i had a problem with the 2nd partition on my SSD drive. It wasn't showing up on anything that it had even been partitioned. I just deleted the partition and re-partitioned it and formatted it with my windows CD, it shows up now at least. I am going to try and re-install Ubuntu again.

---

### Post by Piersadept on 2013-02-02
I reinstalled Ubuntu after messing with my partitions. This time I get a boot menu on where to launch from. I can boot Windows and Ubuntu now. My username and Password do not work that i set up for Ubuntu though. I can only log in through Guest. -_-  Ubuntu does not like me.

---

### Post by Piersadept on 2013-02-02
Nevermind, Everything is working fine now. I just had realized that Caps lock was on -_-.  Thanks for all the help, everyone!

---

### Post by Kixtosh on 2013-02-02
Hey, that's great news! It's easy to get discouraged in the beginning if things don't seem to be working right, but you handled your problems like a champ!

You'll probably find that you don't have to tweak things much to keep everything going properly now that it's working ... but then again, sometimes you might get curious and start messing with stuff that was just fine! That's when the problems might arise, but now that you've done it once, it'll be very simple to start fresh if you really break anything. I find it a lot simpler to fix my Ubuntu than to fix my Windows O.S.! YMMV.

You can mark the thread as "solved" using the "Thread Tools" menu at the top of the page (see attached image).

Have fun, and good luck!

---

