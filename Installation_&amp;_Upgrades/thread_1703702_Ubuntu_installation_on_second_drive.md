---
title: "Ubuntu installation on second drive"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by Bob Appleby on 2011-03-09
I have been successfully using a Dell vostro with ubuntu 10.10 installed on its 8 gig SDHC for several months. For more room I want to install on a 32 gig SDHC which is installed in the card slot. 

  The procedures in:
(help.ubuntu.com/community/InstallingANewHardDrive)
were used to install ubunu 10.10 on the 32 gig drive that I formatted ext4. Its name is listed as (/dev/mmcblk0) and can be accessed by clicking on "places".

 I'd appreciate it if someone would look over what I did, to see why it didn't work.

  Installed 10.10 ubuntu on the 32 gig drive. Everything seemed normal. 

  Created a mount point:

sudo fdisk -l 		        #(to dermine the disk name
(result: Disk /dev/mmcblk0: 32.5 GB, 32462864384 bytes)
sudo mkdir /media/mynewdrive 	#create a mount point file
gksu gedit /etc/fstab
#added a line to fstab:

/dev/mmcblk0 /media/mynewdrive ext4 defaults 0 2

A reboot resulted in the login screen with the following message:
“serious errors were found while checking the disk drive for*
/media/mynew drive”
Typing I for ignore resulted in a normal boot from the 8 gig drive.

Tried to manually mount with:
sudo mount /dev/mmcblk0 /media/mynewdrive
[sudo] password for bob: 
mount: /dev/mmcblk0 already mounted or /media/mynewdrive busy

---

### Post by mikewhatever on 2011-03-10
There is a fundamental difference between "Installing a New Hard Drive" and "Installing Ubuntu on a New Hard Drive". Which one do you want?
The thread title indicates that you wanted to install Ubuntu on the new 32GB SDHC to replace the old 8GB one. If that's the case, remove the old SDHC, connect the new one and boot from the installation media. Now, install Ubuntu on the new SDHC. Done!

---

### Post by Hedgehog1 on 2011-03-10
> **Bob Appleby said:**
> I have been successfully using a Dell vostro with ubuntu 10.10 installed on its 8 gig SDHC for several months. For more room I want to install on a 32 gig SDHC which is installed in the card slot. 


Bob,

I would like to suggest an alternative solution.  This is one that will keep you from the grief you are now 'enjoying'.

Linux follows the Unix tradition of allowing you to add hard drives as part of the 'directory tree' of the first hard drive.  Using this behavior, you can still boot off of the internal 8 gig SDHC and incorporate the new 32 gig SDHC for a total to 40 gigs of active storage.

The idea is that you would move your '/home' directory to the new 32 gig SDHC.

If you have not damaged the Ubuntu install your 8 gig SDHC, then the steps are reasonably simple to move the '/home' directory: 

[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")


If you have damaged the Ubuntu install on the 8 gig SDHC and have to reinstall anyway, then you can do this during the new install.  Use the manual mode and select the 32 gig SDHC drive as your '/home' parition, and two partitions on the 8 gig SDCH as your '/' & SWAP.

You will then have a 40 gig Ubuntu system ready to go.

***The Hedge***

:KS

---

### Post by Bob Appleby on 2011-03-10
Hi Hedge,

   Many thanks for your help. The procedure was not without problems, but I think it is working. The disk usage analyzer says the the total file system usage is 11.7 gig , which is larger than the size of the 8 gig SDHC so it must be using the 32 gig disk though there are no visible files. (I stupidly put a space in the name so it can't be accessed with the terminal.) Free space is 31.5.

   For the record the problems were:
     1. The Check Copying Worked section (diff -r /home /media/home)
        Produced a list 3 pages long. 
     2. The Deleting the old Home section (cd /;sudo rm -r /old_home)
        refused to delete, but since the system seems to be working,
        I'll just ignore it. 

   Thanks again.

Bob

---

### Post by Bob Appleby on 2011-03-10
I give up. How do I mark this thread as being solved?

---

### Post by Hedgehog1 on 2011-03-12
Bob,

I know it's a little late for you, but I wanted to add this graphic for the next person:

[IMG]http://img863.imageshack.us/img863/6315/netbooksd.png[/IMG]

I am working on a larger post that this image is a part of.

The idea to to help folks think in 'Linux **fstab** (**f**ile **s**ystem **tab**le) mode, not DOS/windows mode.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-12
I missed your other question:

To mark a thread as being SOLVED, there is a pull down menu on the upper right hand side of the thread.  One of the options is to 'mark as solved'.

***The Hedge***

:KS

---

### Post by sephiroth42496 on 2011-06-25
i dont know if this thread has been marked as solved but ive been tryng to do the same thing with my 4gb asus 701 4g (soldered ssd) ive tryed installing and partitioning and changing the home directory forubuntu 10.10 on the 32sdhc i have but no luck im at my wits end and ran of ideas some advice would be sooooooo much appriciated](*,)

---

