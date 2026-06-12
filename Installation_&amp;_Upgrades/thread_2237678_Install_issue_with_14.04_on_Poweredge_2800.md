---
title: "Install issue with 14.04 on Poweredge 2800"
date: 2014-08-03
forum: Installation &amp; Upgrades
---

### Post by Bill_Hensley on 2014-08-03
Hi, I'm having a bit of trouble installing Edubuntu 14.04 on a Dell Poweredge 2800.

The 2800 was donated to our school a couple months ago.  To check it out, I installed Fedora 16 with LVM, that went very smoothly.  The machine has 6GB of memory, and four 146GB SCSI disks.  Fedora took each of those PVs, grouped them into an LV, and works just fine.

When I decided to use the machine as our new Edubuntu LTSP server, I downloaded and verified 14.04.  It boots the machine just fine, and starts the install process.  It goes through the two language screens, then the Preparing and Options Parts 1 and 2.  Here is where I run into the problem.

On the Installation Type page, I select Erase Disk and Install Edubuntu and Use LVM, then Continue.  One thing here, I've tried the install numerous times, and sometimes, this page reports "This computer currently has no detected operating system", and sometimes it notes that there is a Fedora installation (I'm running an install try as I type this, and this time is does not detect the Fedora.  I click Continue.  One note:  I've also tried this page without checking the Use LVM box, no difference.

The next page is Erase Disk and Install Edubuntu.  The page reports the entire disk will be used.  The drive selected is /dev/sda (ext4), and the dropdown box at the top has all four disks listed, along with the correct size of 146GB.  I click Install Now.

This is where the install goes off the rails.  The Install Now buttons greys out, about 10 seconds pass, and the title of the page changes to Installation Type, and the Back and Install Now buttons are active again.  The pulldown, entire disk will be used, and selected /dev/sda (ext4 are still there).  Clicking Install Now again results in Install Now greying out for 5-6 seconds, and then the page is replaced with the Installation Type page with options for Erase Disk and Install Edubunu and Use LVM selected.

This cycle repeats at least 10 times.  Clearly, there is something with the disks that the installer does not like.

I would appreciate ideas on what to do to fix this issue.  I wonder if the existing Fedora installation is the issue, and would zorching the entire existing Fedora LVM be an option?  Or is there a switch or other option to force Edubuntu to use the existing partition?  I am very comfortable with most aspects of system administration, but I am not strong on manually setting up file systems.  I am no expert on LVM, although I have manually built several from the command line just to experiment.

I'm going to install Edubuntu onto a plain desktop with extra memory until I get this resolved, so I will have a test system to play with for the next bit.

Thanks very much,

Cheers, Bill

[email]billhensley@earthlink.net[/email]

---

### Post by Bill_Hensley on 2014-08-03
A quick note, I am installing to a Dell Optiplex GX270 now with no issues.  This machine had a single 80GB disk with a Mint installation, I added a second NIC to it for LTSP, and it is being happily overwritten.

---

### Post by Bill_Hensley on 2014-08-06
Well, NM.  I ended up booting from a Fedora live CD, and zorched the existing LVM using the lvmdiskscan, then lvremove for the root and home partitions (and the swap partition after I disabled it with swap off -v).  Finally I used vgremove, then pvremove for the four disks.  A reboot into the Edbuntu DVD and I got a clean install.  

Tomorrow I will bring the other disks into the Edbuntu VG.

I've already booted several clients using LTSP.  The next couple of days I will tweak and adjust.  School starts in two weeks.

---

