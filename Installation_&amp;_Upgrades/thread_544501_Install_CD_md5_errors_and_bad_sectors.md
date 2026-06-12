---
title: "Install CD md5 errors and bad sectors"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by matty_c on 2007-09-06
I am having trouble installing Xubuntu 7.04 onto a Thinkpad T20.
Specs are PIII 700 Mhz, 128 meg ram, 18-20 gb hard drive, ultra bay cd/dvd rom drive.

I used System Rescue CD to start up GParted and created several partitions.
/dev/hda1 5gb ext3 for XUbuntu
/dev/hda2 2gb ext2 for Puppy Linux
/dev/hda3 2gb ext2 for DSL
/dev/hda4 is an extended partition using the rest of the disk
/dev/hda5 ~8 gb I want to mount as /home
/dev/hda6 512 mb swap

I downloaded the Alternate Install cd for Xubuntu 7.04.
Verified the MD5 sum after downloading.
Burned the iso correctly using ImgBurn under windows Xp on my desktop pc. Burned at 6x
ImgBurn verified the cd after the burn was done and the test passed.
Booted off the CD and choose Check CD for errors, No errors, test passed.

Text installer was working fine, I get to a step in the installer called Select and Install software. It got to about 6% the stopped. Eventually generated an error.
I checked /var/log/syslog and saw some Bad Sector error messages.
I aborted the install, and rebooted off the System Rescue CD.
I ran e2fsck -c /dev/hda1 and it was ok. I am paranoid so I ran e2fsck -c -c /dev/hda1 to do the read/write test and it was ok again.

I look at the xubuntu disk and it looks clean, no scratches.
I restart the system and boot off the xubuntu disk again.
Setup is going fine until it comes time to install the kernal. It presents me with a choice of kernal
linux-generic
linux-image-generic
linux-image-2.16.20-generic
No matter which one I pick the install dies.
Checking /var/log/syslog shows an MD5 error when trying to unpack/install the kernal.

My ideas are:
Try burning a new cd.
Try a new brand of cdr and burn a new cd.
Try to do a PXE boot and a network install.
Try and get a bootable cd with usb drivers, that will let me boot of an external usb cd drive.

Any ideas?

---

### Post by zipperback on 2007-09-06
> **matty_c said:**
> I am having trouble installing Xubuntu 7.04 onto a Thinkpad T20.
Specs are PIII 700 Mhz, 128 meg ram, 18-20 gb hard drive, ultra bay cd/dvd rom drive.

I used System Rescue CD to start up GParted and created several partitions.
/dev/hda1 5gb ext3 for XUbuntu
/dev/hda2 2gb ext2 for Puppy Linux
/dev/hda3 2gb ext2 for DSL
/dev/hda4 is an extended partition using the rest of the disk
/dev/hda5 ~8 gb I want to mount as /home
/dev/hda6 512 mb swap

I downloaded the Alternate Install cd for Xubuntu 7.04.
Verified the MD5 sum after downloading.
Burned the iso correctly using ImgBurn under windows Xp on my desktop pc. Burned at 6x
ImgBurn verified the cd after the burn was done and the test passed.
Booted off the CD and choose Check CD for errors, No errors, test passed.

Text installer was working fine, I get to a step in the installer called Select and Install software. It got to about 6% the stopped. Eventually generated an error.
I checked /var/log/syslog and saw some Bad Sector error messages.
I aborted the install, and rebooted off the System Rescue CD.
I ran e2fsck -c /dev/hda1 and it was ok. I am paranoid so I ran e2fsck -c -c /dev/hda1 to do the read/write test and it was ok again.

I look at the xubuntu disk and it looks clean, no scratches.
I restart the system and boot off the xubuntu disk again.
Setup is going fine until it comes time to install the kernal. It presents me with a choice of kernal
linux-generic
linux-image-generic
linux-image-2.16.20-generic
No matter which one I pick the install dies.
Checking /var/log/syslog shows an MD5 error when trying to unpack/install the kernal.

My ideas are:
Try burning a new cd.
Try a new brand of cdr and burn a new cd.
Try to do a PXE boot and a network install.
Try and get a bootable cd with usb drivers, that will let me boot of an external usb cd drive.

Any ideas?


If the md5 checksum verifies correctly, and the cd that you burned verifies correctly then more than likely it isn't the media that you are installing from.

That partition scheme you are using is a REALLY BAD IDEA in my opinion. You should "NOT" be trying to use your single /home partition for all your different distribution installations of Linux which you will be actively using. It's just a really bad idea. 

My advice is to insert your xubuntu installer cd, boot it, and just install it to it's own partitions. You can run more than one distribution on your system, that is not much of an issue, but you should allow each of the different distributions to have their own partition scheme, and not try to share it between them.

Just my opinion, but it's good advice.

- Jack
- zipperback

---

### Post by logos34 on 2007-09-06
> **matty_c said:**
> Try to do a PXE boot and a network install.


I'd try the latter--the network installation approach (using **[UNetbootin]("http://lubi.sourceforge.net/unetbootin.html")**).  Your iso and media are fine...sounds like the laptop cdrom is producing read errors and corrupting the data (it may be as simple as a dirty lens).  That's my best guess. You might also want to run memtest86+ just to verify your ram is ok.  


[http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540)

---

### Post by matty_c on 2007-09-06
What exactly is saved in /home? I was under the impression that is simply used for storing user files (documents, mp3s, etc). Doing some searching I see that application settings are also saved here? Is this correct?

Could I have xubuntu mount the partition as /home, and have any other distribution I install mount it as read only with a name such as /mnt/share to allow me read access to files saved there?

Any idea on the md5 errors? I suspect the cd drive is at fault, however using the Check CD for Defects option works fine. So that means I am able to read the entire cd at that point....

I will try again tonight using xubuntu's default partitioning scheme (after blowing away the current structure, nothing is installed yet) and post any error messages I get.

---

### Post by merlinus on 2007-09-06
Yes, /home contains things like email, bookmarks, preferences and configurations.

Better idea is to create a separate partition for your data, which then can be easily shared amongst any number of distros.

-merlin

---

### Post by matty_c on 2007-09-06
Ok, im in a bit of a bind.

Ran 3 passes of memtest with no errors.
So then I used the PXE booting method to point my laptop at a tftp server I setup on my desktop.
I served up the netboot folder from the xubuntu cd I have.
It was able to do the install without a problem hardware wise.
When I got to the software selection screen, it told me the core system was installed and to pick a desktop such as [x|e]ubuntu-desktop. Well I didn't read the instructions and just pressed enter.
It didn't install anything else besides the core system.

Ok, that wouldn't be a problem because I know I could apt-get install the xubuntu desktop..... However my laptops ethernet port gave up on me. The laptop is 7 years old, and the network jack has seen too much abuse over the years, it wiggles alot... I am surprised I even got it to work long enough to do the install. Now the connection from the jack to the motherboard must be broken, because if I plug a cable in and try and wiggle it I get all kinds of pci bus errors coming from eth0.

I have a D-Link Pcmcia 10/100 ethernet adapter. Any advice on how I can get this installed and working on my system. Any useful guides out there for getting a pcmcia card support up and running from cli only obviously.

My brain is a little tired right now, and don't remember how to search the google for correct answers.

Thanks 
-matt

---

### Post by matty_c on 2007-09-06
Ok so I figured it out. Those man pages can be helpful.

Inserted the D-Link network adapter into the pcmcia slot and powered up the system.
ifconfig -a showed I had eth0 and eth1 adapters. The mac address for eth1 was my D-Link adapter.
Edited /etc/network/interfaces to use eth1 instead eth0 as root
Restarted network services with sudo /etc/init.d/networking restart and now I get an ip address
sudo apt-get install xubuntu-desktop and 45 minutes later I am back to my command prompt.
startx and now I am up and running.

So if anyone needs to know a D-Link DFE-670TXD 10/100 pcmcia card works with ubuntu 7.04 out of the box.

-Matt

---

