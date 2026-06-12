---
title: "XP Partition Issue"
date: 2014-12-20
forum: Installation &amp; Upgrades
---

### Post by RCramdon on 2014-12-20
Hi all! Running Win XP. Decided to try linux, downloaded 14.04 LTS and created dvd. Took a test drive from the dvd. It worked well with no hardware issues, even satellite internet connect worked great.
 
I’m trying to make a dual boot os on a single 970GB hard drive. I use xp for business and want to slowly transfer over to ubuntu.
 
I spent a month cleaning the system and backing up 50GB of data. XP runs much, much better and is ready to partition.
 
Per instructions I downloaded gparted-live-0.4.6-1.iso and created a cd. When trying to boot to the cd… I get a “Boot Failed error message” “Unable to find a medium containing a live file system”.
 
There seemed to be a newer version of gparted-live at the download page but only one was described as stable. 0.4.6.1.iso.
 
No idea at this point. I used the “check if already posted” link and read back to 2008 with out finding any post similar.
 
I’m unfamiliar with this new software and terminology. Without a partition I can’t install ubuntu.
 
XP is still there and boots fine with no unusual issues. Single user, no password protections.

Any help will be appreciated..

---

### Post by oldfred on 2014-12-20
Not sure what gparted you downloaded?
I often use gparted and have it just as another way to boot, but usually use the gparted that is on the live installer of Ubuntu.
What flavor of Ubuntu did you download? Ubuntu has gparted but some of the other flavors like Lubuntu or Xubuntu which may be better for older systems may have other similar partitioning tools.

If you want just the default install of / (root) and swap you just need unallocated space, or can use Something Else and the installer has its own partition tools. I consider gparted a bit easier to use and do recommend partitioning in advance and using Something Else to install, but it is a bit more advanced as users have to understand partitions.

You mention a 1TB drive. Is this a newer system that just had XP? As some very old BIOS, may not boot from beyond 137GB on a hard drive. Then you need either / (root) fully inside the first 137GB or a separate /boot inside the first 137GB. I suggest / of 20 or 25GB and rest for /home then.

If BIOS has AHCI better to use that, but then XP will not work as it does not have those drivers. I turned off AHCI (and XP) when I got my first SSD as SSD required AHCI.

What processor, amount of RAM and video chip/card does your system have?

---

### Post by RCramdon on 2014-12-21
Quote - *Not sure what gparted you downloaded? I often use gparted and have it just as another way to boot, but usually use the gparted that is on the live installer of Ubuntu.*

   
  While reading commity files about installation possibilites I found this page.  [https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions) 
   
  &#8220;If using Windows XP (or an older Windows OS), you should use [GParted partition manager]("https://help.ubuntu.com/community/GParted") to shrink the Windows partition and leave free space on the hard drive for the Ubuntu partition.&#8221;
   
  The link &#8220;GParted partition manager&#8221; took me to this page. [https://help.ubuntu.com/community/GParted](https://help.ubuntu.com/community/GParted) which stated....
   
  &#8220;GParted preinstalled on Ubuntu liveCD
  Boot a Ubuntu live-CD (or live-USB), select "Try Ubuntu", open GParted. 
   
  GParted LiveCD
  Download the GParted .ISO image [here]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779"). Follow [these instructions]("https://help.ubuntu.com/community/BurningIsoHowto") to burn the .ISO image to CD. Boot the GParted LiveCD as your partition manager. &#8220;
   
   
  I was unsure if the first option would start an installation, details were lacking. So I opted for the second option which took me to [http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.4.6-1/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.4.6-1/)
   
  There were 3 downloads available with drastically different file numbers. There was description of file version that was not available. Confusing to say the least. The above link provided on the community/GParted page ended with the numbers 0.4.6-1 so I downloaded that file and created a disk.

   
  That disk gave the &#8220;Boot Failed error message&#8221;
  
Quote - [I]What flavor of Ubuntu did you download? Ubuntu has gparted but some of the other flavors like Lubuntu or Xubuntu which may be better for older systems may have other similar partitioning tools.
 [/I]
 
  I &#8220;downloaded 14.04 LTS and created dvd&#8221; ubuntu-14.04.1-desktop-amd64.iso 

   
  
Quote - *If you want just the default install of / (root) and swap you just need unallocated space, *

   

  Xp claims the entire drive. There is no unallocated space. This is why I need to shrink the partition and create another for ubuntu.
   
   
  Quote - *or can use Something Else and the installer has its own partition tools. I consider gparted a bit easier to use and do recommend partitioning in advance and using Something Else to install, but it is a bit more advanced as users have to understand partitions.*

   
  I don&#8217;t understand? Is &#8220;Something Else&#8221; a program? Where do I find it?

Quote - *You mention a 1TB drive. Is this a newer system that just had XP? *

   

  The motherboard in my old system was failing. In years past I would have built a new system. I simply didn&#8217;t have time or inclination. I didn&#8217;t want to choose a new os, win7 or 8, I intended to get a few more years of use out of XP then make another choice.

 I took the pc down to a local shop I&#8217;ve bought parts from for years and sell organic produce to, folks I know. They built me a new pc and ghosted the old drive to the one in this new pc. I know none of the details of how this was accomplished, just big picture.
   
    Quote - [I]As some very old BIOS, may not boot from beyond 137GB on a hard drive. Then you need either / (root) fully inside the first 137GB or a separate /boot inside the first 137GB. I suggest / of 20 or 25GB and rest for /home then.

If BIOS has AHCI better to use that, but then XP will not work as it does not have those drivers. I turned off AHCI (and XP) when I got my first SSD as SSD required AHCI.[/I]

XP is working fine&#8230; it&#8217;s just old. I just want to shrink the partition it&#8217;s using and try Ubuntu.

   
  Quote - *What processor, amount of RAM and video chip/card does your system have?*

   
  Processor - Pentium G2120 @ 3.10GHz

  Ram &#8211; 3.2GB
  Video &#8211; intel HD graphics
  I don&#8217;t understand why this is important to shrinking a partition.
   
  Thank you for your help. :smile:

---

### Post by oldfred on 2014-12-21
If I go to gparted's page I get a much newer version, either 32 bit or 64 bit. 
I would not use old version. It says that version is from 2009, and right above it is the link to the newest version.
So download newest or use gparted in Ubuntu's live installer.

 [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
gparted-live-0.20.0-2-i486.iso
gparted-live-0.20.0-2-amd64.iso

Since you have a newer 64 bit system you should use 64 bit versions (amd64), which you have.

Use whichever new version of gparted you want, either Ubuntu's or gparted's .20 and shrink XP's partition. If still using XP (which is not recommended) be sure to leave 30% free. NTFS partition start to slow when available free space inside it is less than 30% and at 10% free gets very slow and you probably cannot do a defrag.

As soon as you have shrunk the NTFS partition, reboot XP so it can run chkdsk and repair itself to its new size. 

How much space were you planning on allocating to Ubuntu? 
Since drive is very large at 1TB, I would suggest smaller system partition / (root) and larger /home partition where you data goes. I used to do the same with XP and have XP in a smaller system partition and have another NTFS partition for data.

      
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by grahammechanical on 2014-12-21
Something Else. What is that?

When we run the Ubuntu installer we see some dialogs similar to the images in this link.

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

You must have already seen the Welcome screen where you chose to Try Ubuntu. When we choose the Install Ubuntu option we get the second dialog - Preparing to Install Ubuntu. If we have a wired connection to the Internet we do not get the third dialog. It is at the next dialog that we get a choice of ways to install Ubuntu. You will see something similar to,

Install Ubuntu alongside them - that is other operating systems
Erase disk and Install Ubuntu
Encrypt the new Ubuntu installation for security
Use LVM with the new Ubuntu installation
Something Else

If we choose Install Alongside then the installer will do all the work. See image 5.
If we choose Erase and install Ubuntu, then the installer will erase the existing OS and data on the drive.
If we choose Something Else then a partitioner will load and examine the hard drive and we will be required to tell the installer what partitions should be used for Ubuntu. That may mean resizing existing partitions to create unallocated space and then creating a new partition out of the unallocated space. This method is more complicated, especially when doing it the first time.

I often use Gparted from the live session. Load the live session until you get to a desktop. Click the Ubuntu icon at the top of the Launcher - the panel on the left side and search for Gparted and load the application.

Regards.

---

### Post by RCramdon on 2014-12-22
I downloaded gparted-live-0.20.0-2-i486.iso and will make a disk. I will give it a try in a few days, dealing with new born calves at the moment. The detailed information you provided should get me through the process. I&#8217;ll keep this thread open until I get ubuntu installed successfully and then close it.
 
Thank you very much &#8220;oldfred and grahammechanical&#8221; for your patience with a noob and your help. ;)

---

