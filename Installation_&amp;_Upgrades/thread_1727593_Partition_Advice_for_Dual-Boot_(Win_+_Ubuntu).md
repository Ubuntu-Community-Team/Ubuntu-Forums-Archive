---
title: "Partition Advice for Dual-Boot (Win + Ubuntu)"
date: 2011-04-12
forum: Installation &amp; Upgrades
---

### Post by danielgrosvenor on 2011-04-12
As much as I'm loving learning about Linux, the problems I'm running into on this laptop have started affecting my job so I'm going to do the sensible/boring thing and partition the drive to run Windows as well.

I have a 320GB hard drive, and would like to allocate approximately 70GB to Ubuntu and the rest to Windows.

I'll store my media and other big stuff on the Windows partition, so Ubuntu will primarily be used for Word documents and playing with Linux. Would you say 70GB is a good size to aim for or should I go higher/lower?

Of course, there are also SWAP partitions and things which I know nothing about.  Could someone please advise me on exactly which partitions I'll need to create?  I plan to use G-Parted to create them (ideally shrinking the current Ubuntu partition, although I can format and reinstall if need be).

Also: what's the recommended way to dual-boot? Should I be looking to use GRUB ideally, or the Windows boot file?

---

### Post by oldfred on 2011-04-12
I like grub2, windows will not boot Ubuntu, but some third party windows boot loaders will. Some that are more windows folks prefer the windows way.

You will have to have a primary partition formated to NTFS with the boot flag (active partition in windows). Primary partitions are any of sda1 thru sda4. But you want to use one of the 4 primaries as an extended partition to hold logicals. I strongly suggest you create another shared NTFS partition which can be  a logical partition for any data you may want in either system. I have photos, Firefox & Thunderbird profiles in the shared so everything is the same in both systems. Saves rebooting to check email. Same bookmarks. Same Picasa. etc.

I also prefer to keep system partitions small for both windows & Ubuntu but they still need plenty of  free space. But then all the data goes into shared partition(s). 

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Besure to backup all important data before changing partitions around.

A windows install will overwrite the MBR and you have to reinstall that to get grub to boot again.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

After booting you can run this and it will find your windows install and let you choose what to boot.

sudo update-grub

Dual Boot Win7 & Ubuntu
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

### Post by Adrastus on 2011-04-13
I'd like to second Oldfred's advice.  I built a computer this past fall with a 640GB HD and I use a similar partition scheme dual-booting Win7 and Ubuntu.  I use ~70 GB partitions for each of Windows and Ubuntu with the first a primary partition for Win7 then a shared 400GB NTFS partition where I keep all of my media and working project files (although most of my stuff gets synced through dropbox--I haven't been able to figure out how to do a single shared dropbox folder between both OSs yet though), and then an extended primary partition for Ubuntu with /boot, /, /home, and swap.  It's been working great so far.

It is best that you install Windows first and it does have a kind of Darwinian desire to wipe out everything else on the disk, though that's gotten somewhat better with Win7.  And I strongly recommend using GRUB2 or a derivative as your boot loader, it's been very good to me.  Once you're comfortable with GRUB you might try switching to something a bit prettier like BURG which is basically GRUB2 with a graphical front-end.

And last, but not least I will reiterate, BACKUP before you start!

Goodluck,

--Adrastus

---

