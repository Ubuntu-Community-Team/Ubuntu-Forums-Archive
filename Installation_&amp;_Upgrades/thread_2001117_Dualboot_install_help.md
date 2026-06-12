---
title: "Dualboot install help"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by Toon1 on 2012-06-10
[FONT=Verdana, sans-serif]Hi,[/FONT]
 
 [FONT=Verdana, sans-serif]I'm finally ready to try out Ubuntu (actually Xubuntu) again, after a long break. I can run the live image of 12.04 from a USB stick just fine, and my laptop's hardware (Lenovo E120e Intel version) seems well supported. However, I still want to continue using Windows XP, at least for a while.[/FONT]
 
 [FONT=Verdana, sans-serif]My 320GB HDD currently has 2 partitions, a 32GB boot partition for XP and apps, and the rest of the drive formatted as NTFS, for my data. I have backed up the boot partition and MBR using TrueImage, and the files on my data partition, and am ready to start playing. What I want to do is set things up with the 32GB XP partition as it stands (don't want to have to re-install everything), and 32GB used for all Xubuntu's partitions (boot, swap, and home, assuming things are still like that). Then I want the rest of the drive formatted as an NTFS partition I can share with both OSs. I'm sure that GRUB will do what I want it to, IE can be configured to wait 2 seconds before booting my last selected OS. I do need a little hand-holding to start off the installation. Any help most appreciated![/FONT]
 
 [FONT=Verdana, sans-serif]Thanks for reading.[/FONT]
 [FONT=Verdana, sans-serif]Toonie.[/FONT]

---

### Post by sudodus on 2012-06-10
I think you know a lot, so it will work fine. If you are sure that the backup is OK, go ahead.

With a good backup of the data files (of the ntfs partition), I suggest that you wipe the ntfs partition and create the partitions for Xubuntu and use the rest of the drive as the new shared ntfs data partition. It is possible to shrink the ntfs partition, but it is much slower than to repartition, format and restore the data.

Boot Xubuntu live from a CD or USB drive, and from there run gparted to make the partitions and linux file systems.

But boot Windows to make the ntfs file system!

And then install Xubuntu selecting the partitions manually, choose 'Something else' in the install wizard.

---

### Post by oldfred on 2012-06-10
How full is NTFS partition. NTFS partitions like 30% free. At 10% free they just about stop working.

Have you run chkdsk and defrag on your data partition recently. If you have the space and an available primary partition, you should just be able to shrink your data partition and create one new primary as an extended partition. That extended partition then is the container for all your logical partitions for Ubuntu.

If data partition is  fuller and not defragged then sudodus's suggestion is probably better as that in effect does some of the housecleaning.

I often suggest the separate /home as that would have all your (hidden) user settings and data. Then a clean reinstall is easier as you can just reuse the /home partition and just reformat the system install partition. 

But if most data is going into the shared NTFS partition, then you have less need for the separate /home. I find my /home is about 1GB with .wine most of that, but I am aggressive about moving data to my data partitions. So I have /home inside  (root) and at 1GB is easily backed up. Even some hidden data folders like my Firefox & Thunderbird profiles are still in my NTFS data partition from when I booted XP. Now most new data goes into a ext3 data partition as I rarely boot XP anymore.

---

### Post by Toon1 on 2012-06-10
> **sudodus said:**
> I think you know a lot, so it will work fine. If you are sure that the backup is OK, go ahead.

There is a lot I DO know, for sure. What I lack, is knowledge of the tools Linux has to offer

> **sudodus said:**
> It is possible to shrink the ntfs partition, but it is much slower than to repartition, format and restore the data.

Thanks, I'll give that a try!

> **sudodus said:**
> Boot Xubuntu live from a CD or USB drive, and from there run gparted to make the partitions and linux file systems.

This is where I fall over a little. If I'm not using the installer to create the partitions, I have no default partition sizes, so I'd be a bit lost for how to set them up correctly, and to appropriate sizes.

Thanks for the comments!

---

### Post by black veils on 2012-06-10
you dont *need*  to create all those xubuntu partitions, unless you actually want to?  


in windows, disk clean and defrag.


have you already shrank windows/data partition and left unallocated space for xubuntu?  i recommend you do that before entering the xubuntu install wizard. boot the xubuntu live environment, open the app gparted. if it isnt there, then open terminal and install via ```
sudo apt-get install gparted
``` shrink whichever partition is last, to a safe size (make sure your data is saved somewhere else first). then you will be left with free space or unallocated space, whatever its referred to.


now you may close the app, restart windows a couple of times, check everything is ok, let it do any disk checks it might want.


now onto the xubuntu install wizard. its very simple, it holds your hand the whole way. choose the **something else** option from the 2nd or 3rd wizard screen, then from the free hdd space, make 2 partitions, one with format as ext4 and mount point  /    the other partition as swap.

---

### Post by Toon1 on 2012-06-10
Thanks Black Veils. Actually from reading this, what I might end up doing, is simply removing the data partition altogether, then do the install, then from within XP, create the NTFS partition and then copy my data back into it. That way the Linux stuff will be nearer the beginning of the drive. Assuming there's still an advantage to that these days.

---

### Post by black veils on 2012-06-10
i wouldnt know. i thought you couldnt do disk management (edit and create partitions) from win xp. you might be best doing the shrinking/deleting from win xp then, instead of gparted, then follow the rest as i said.

Edit:
i am unsure of the technicalities of having a data partition after both operating systems, to share data between the two. not my area of knowledge, i dont deal with data partitions, i just know FAT32 can be used, and might be best.

---

### Post by oldfred on 2012-06-10
Unless it is an older computer that has the 137GB BIOS boot limit, you do not need the separate /boot.

I normally suggest 25GB for / (root) if you have most of your data elsewhere. I find I use about 7GB of / with many apps and my 1GB of /home. I prefer the smaller system partition for some minor efficiency of drive not searching all over for the most used system files. 

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)
Herman even now use a swap file, not a swap partition. But I still keep a 2GB swap partition as I do not hibernate.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

### Post by varma1993 on 2012-06-10
using gparted seperate a 32 GB drive from the NTFS part.
select something else while installing without selecting  install alongside windows or any other option.
You don't have to allot size for all the directories like home, tmp etc.
you can just allot space for swap and select the remaining space for the root folder i.e., "/" option.
thats it.

---

