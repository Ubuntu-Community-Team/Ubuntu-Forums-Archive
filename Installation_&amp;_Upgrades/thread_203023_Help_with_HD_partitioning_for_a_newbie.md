---
title: "Help with HD partitioning for a newbie?"
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by MikeMLP on 2006-06-24
Hello!

-I've been thinking about trying out a Linux install for some time now, but hardware support and installation ease were always the two biggest hurdles.

-I recently tried the 6.06 live CD, and have been so impressed with its hardware support for my setup (and what looks like a pretty simple install process) that I've decided to try installing it to my HD. 

-I'm running an IBM Thinkpad T42 with an XP partition followed by a recovery partition that came with the machine.  I would like dual-boot Ubuntu and XP.

-I have 22 GB of free space right now, and I am wondering what the best way to repartition for Ubuntu would be.  I've looked at this site: 
[http://www.psychocats.net/ubuntu/partitioning.html]("http://www.psychocats.net/ubuntu/partitioning.html")
which has been very useful, however I still have a few questions.  

My understanding is that for best results, given the relatively quick release cycle, I should install a primary partition for the root (/) and a logical partition for the /home, plus a 1GB swap partition (I have 512 MB of ram).  

Thus, my questions are in regards to three things:

1.  What should the size of these partitions be? - (My best guess is 10 GB for the root, 5 GB for the home, 1 GB for the swap, leaving 6 GB for additional files on Windows (and swap space.  How does this sound to you vetrans?)

2.  What would be the best locations (order on the HD) for these partitions, given that I want to leave my current partitions as intact as possible, (that is, they will be sandwiched between my XP partition and the IBM recovery partition)

3.  What special rules must I know about Primary, logical, and extended partitions (I know that the root should be on a primary, at the very least, but what about the swap and /home?  Does the order of the partitions on the drive make a difference here?  What limitations of GParted (through the use of the LiveCD installation process) should I be aware of before I begin, and are there any specific tasks that I should be sure not to forget during the GParted partitioning process?

**Also:** Can I live without a FAT32 partition for going between ext3 and NTFS using the "FS-Drive" (which I've installed, and which seems to work), or is it too limiting?  If it does allow windows to read and write to ext2/3 as its site claims, then can I avoid the FAT32 partition (as I would like to)?

Finally, a word about backups:
I've been backing up critical files for more than a day, and I believe I am covered in that department.  If something goes wrong, and the XP install is destroyed, I'll see it as a blessing, since I should re-install it anyway, as it has been running for 2 years, and is becoming slow and bloated.

Thanks for helping me to plan, I would like to mess around with partitions as little as possible, and I am hoping to reach a setup that will go for many months without the need to mess around with partitions again.
Thanks for listening!

---

### Post by olsonar on 2006-06-24
1) sounds good. that's pretty close to what I have.
2) no idea. i have yet to see any evidence that order acually matters.
3) just make root primary, home and swap can be logical.

yes, something like fs-drive will work fine, although i wouldn't reccommend it.

one more piece of advice: use the stand-alone gparted rather than the one embedded into the installer to create the partitions. then just click through the one in the installer without doing anything, then select which partitions to mount where.

---

### Post by MikeMLP on 2006-06-24
Thanks for the reply!

Just to clarify... any particular reason why you would prefer to have a FAT32 partition to share files than use fs-drive?

Also, browsing around, I noticed this rather alarming thread: [http://ubuntuforums.org/showthread.php?t=186395&highlight=dual+boot]("http://ubuntuforums.org/showthread.php?t=186395&highlight=dual+boot")

Can anyone shed some light on this?  It seems to me that there are a few common threads regarding those who were unfortunate enough to have their NTFS partitions rendered useless:

1. They partitioned using the Ubuntu LiveCD installer, rather than going through the Gparted Live CD, or an alternate method.
2. They used Ubuntu, rather than Kubuntu, or Xubuntu.  See the "bug report"  on page 2 of the thread indicating that the installer changes the NTFS partition even when the Partition is nto resized.   Could there be a bug in the Ubuntu installer, and not in the others?  If so, I'll gladly install Gnome after the fact, or perhaps stick with KDE or XFCE.

It has been a few weeks since the 6.06 relese, and it looks like quite a few people have had this problem (and others hae not).  Does anyone know anything more about this?  Is there a fix, has there been any "official word?"

looking at this page for the Gparted Live CD:  [http://gparted.sourceforge.net/larry/resize/resizing.htm]("http://gparted.sourceforge.net/larry/resize/resizing.htm")
it looks like if you mess around at all with the NTFS partition, you'd better darn well restart and boot into XP before screwing around with anything else.  

Notably, the Ubuntu LiveCD installer does not reboot until all partitioning and installation is complete.  Would it make a difference then, to resize NTFS using the Gparted LiveCD, reboot, and let windows figure out what happened, then partition the liberated space with the Gparted LiveCD, then procede with the installation from the Ubuntu LiveCD?

Does anyone know anything more about this situation (before I take the leap)?

---

### Post by olsonar on 2006-06-24
hmmm. no idea about the NTFS problem. i used the old text based installer on the breezy cd to partition my disk. if you have partitioning utility for Windows, using that to free up the space would be a good idea. actually, since your windows install is not in good condition, you could just backup, repartition and reinstall windows before installing linux. that's probably a really good idea, since if you reinstall windows after you install linux, it'll wipe out your boot loader, and that can be a pain to get back. (your ubuntu install will be fine, you just won't be able to boot to it.) you could also then install windows to a fat32 partition instead of ntfs, thereby eliminating the need for fs-drive. the reason using fs-drive is not a terribly great idea, since it doesn't support journaling. that doesn't matter if you're using it with ext2fs, but writing to ext3fs can have problems. usually it'll be fine though.

---

### Post by MikeMLP on 2006-06-25
Since I wish to avoid the horror stories of other dual-booters, and refuse to leave things to chance, this is what I would like to do:

1. perform all repartitioning step-wise using Gparted live CD, that is, rebooting and checking windows after each change to the partitions.

2. Use the alternate installer to install Ubuntu and GRUB to its partition and not the mbr. [See Here]("http://users.bigpond.net.au/hermanzone/p3.htm") )

3. check the XP install to make sure it is ok.

4. Use a GAG CD to boot into Ubuntu and check the install

5. Chainload GRUB using NTLDR through [Bootpart]("http://www.winimage.com/bootpart.htm") (if desired at a later time)

In this way, I can avoid messing around with the mbr as much as possible, and can check with each step if things are starting to go badly.  There is more chance of user error, granted, but from what I've read on the forums, it seems as though the installers aren't quite up to the job.  If I'm not mistaken, the desktop LiveCD does not give the user of installing GRUB in any other location than the MBR.

Additionally, I've found more evidence that using the Desktop 6.06 LiveCD isn't a good idea for some reason: [http://bugzilla.gnome.org/show_bug.cgi?id=343790]("http://bugzilla.gnome.org/show_bug.cgi?id=343790")

Given that this is a laptop, I am sure that I will never have more than 2 OSs on this machine, nor will I be able to add a Hard Drive.  To what extent do you all think my plan is feasable / desirable / necesary?

To those of you who have taken this path before, are there certain things to watch out for?  Can NTLDR be configured properly without a large amount of hassle / risk?

---

### Post by MikeMLP on 2006-06-27
Time to change the title (which I can't do, unfortunately) because I am now dual booting Windows XP and Ubuntu!

I followed my plan to the letter, and it has performed flawlessly, however there are a few remaining configuration issues that I am hoping you can help me with.

1.  Booting:
I am now booting using the GAG live CD, because I have opted not to touch the MBR, and have installed LILO on the linux partition.  I would like to configure NTLDR to point to LILO to have a dual boot option availible on startup without the use of the GAG live CD.  If anyone has any good links on how to do this, it would be much apreciated.
-as a side note, I made a backup of my MBR before the install (but AFTER all partitioning was completed).  I have two files, one with the partition table and one without.  I shouldn't have to back the MBR up after installing again, should I?

2.  Mounting Windows
The installer would not allow me to mount my windows partition during setup (at /windows) so I opted not to set up a mountpoint in order to continue the installation.  I am assuming that I can set up that mountpoint now, but I'm not sure how to do it.  I believe I saw a link somewhere that allowed one to mount it by entering something into the terminal, but I am not certain if I saw anything that explained how to change the mountpoint (eg: from /dev/hda1 to /windows) or how to save that new configuration for use in the future.

3.  Mice setup
I've seen some info on how to set up my other buttons on threads here, and I'll give those a look, however one feature from windows that I'm really missing already is the ability to middle click and move the mouse up or down to scroll a page up or down (for example, in firefox or in openoffice)  Does anyone know how to restore that functionality?

-rather interestingly, in openoffice, a midle-click in the text-area results in a change to the scrolling cursor for a brief instant, and then puts the word "google" into the page (no joke! the MMB must be bound to insert the text "google") - rather odd indeed...

Other than these minor issues, I am breathing a huge sigh of relief that everything went smoothly, and I'm looking forward to finally joining the ranks!

---

### Post by MikeMLP on 2006-06-27
one of the 93 updates available made the MMB scroll work in firefox, and Openoffice is no longer "google" bound, but there is still no MMB scroll in Openoffice.  perhaps there is a setting somewhere...?

---

### Post by olsonar on 2006-06-27
Welcome to Ubuntu! Glad to hear your install went well. Now, your problems:

There's a version of GRUB for windows that runs without changing the MBR. [http://www.geocities.com/lode_leroy/grubinstall/]("http://www.geocities.com/lode_leroy/grubinstall/")

for the windows partition, first make the /windows folder:
```
sudo mkdir /windows 
``` then launch a root nautilus:
```
sudo nautilus
``` right-click on the /windows folder and choose properties. under permissions, check all the read boxes, and uncheck the write boxes. now, edit your fstab:
```
sudo gedit /etc/fstab
``` add a line like
```
/dev/hda1 /windows ntfs umask=0222 0 0
``` replacing /dev/hda1 with your windows partition (it's probably this anyway) if there's already an entry for your windows partition, remove it.
save. do a 
```
sudo umount /dev/hda1 
``` again, replace /dev/hda1 with your windows partition. now
```
sudo mount -a
``` and /windows should now contain your windows partition. 

I have no clue about the MMB scroll. let me know if you get it working, since i'd love to have that functionality too.

---

