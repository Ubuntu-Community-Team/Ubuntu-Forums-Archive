---
title: "Trouble with 10.04 Server and Compaq Proliant ML330 G2 w/ATA RAID"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by sha.goyjo on 2010-05-25
Hey guys,

Been fiddling around with this for a while,  but with no success. I've got a Proliant ML330 g2 with ata raid (with all the latest firmware) set up like this:

CPU: 1.4ghz P4 x2
RAM: 768MB
Built in Video
Built in ethernet

IDE1 Master: CD Drive
IDE1 Slave: Empty
IDE2 Master: 80gb Seagate HDD
IDE2 Slave: Internal Zip Drive
Raid1 Master: 40gb Seagate HDD (stripe1)
Raid1 Slave: 40gb Maxtor HDD (stripe1)
Raid2 Master: 40gb Maxtor HDD (stripe2)
Raid2 Slave: 40gb Maxtor HDD (stripe2)

Now, my problems right now are that:
1. Ubuntu does not detect the 80gb seagate HDD (which I want to install the OS on)
2. Ubuntu fails any attempt to format the raid stripes.

It's quite possible that I have no idea what I'm doing with this, so feel free to ask any particularly obvious questions.

I'm trying to get this up and running so that my IT startup can have a CRM server, so any help would be appreciated. Thanks

EDIT:
I'm thinking I might have some luck fixing the non-detection of the 80gb hdd by putting the zip drive on the same channel with the CD drive. Might that help?

---

### Post by tgalati4 on 2010-05-25
I would disconnect the RAID drives and move the Zip drive to the ribbon shared with the CDROM drive.  If you don't need the zip drive, then remove it.  Disconnect the RAID drives.  Now try to boot with an Ubuntu Live CD.  If you can see the 80 gb drive with the following command (open a terminal):

sudo fdisk -l

Then you should be able to partition it and then install Ubuntu.  The server edition is not a Live Disk, so you will end up having two disks.  One will the the Ubuntu Desktop Live CD (32-bit) and one will be the Ubuntu server install disk 32-bit.

Test the network, video, and other functions with the Live CD.  If everything works to your satisfaction, then reboot with the server CD and perform the installation.  Be sure to select the LAMP stack during the install.

Once you have a valid server installation, then replug the RAID drives and set them up using the RAID BIOS (Control-S during boot perhaps?).

After booting the server:

sudo fdisk -l 

And see if your RAID drive shows up.

---

### Post by ronparent on 2010-05-25
I'm not familiar with the 10.04 server, but this is true for 10.04 desktop - gparted will not format the raid drives, and if by chance the 80Gb was at one point setup as a raid then the meta data that was written to it must be erased for the drive to be seen and formatted.

---

### Post by sha.goyjo on 2010-05-25
Thanks folks. Will try and report back on results.

---

### Post by sha.goyjo on 2010-06-01
Oooookay. Weird. I can install Ubuntu to the non-raid HDD, but the system won't let me boot from it. Even if I disable the raid controller in the bios.....

Is my only option to use a CD to boot from the HDD? Every time? Or do we have a better idea?

---

### Post by NaderNewman on 2010-06-06
I have the same system but a G3. I've tried everything in the book and can not get Ubuntu to install or boot from an install since version 8.10. Last thing I'm going to try before I install Fedora again is try and disabling the RAID controller. Under the server's config "F9" settings menu there is an option to select the boot controller RAID or IDE. I think I need to disable RAID or flip a couple of switches on the smaller bank to be able to make the change.

---

### Post by sha.goyjo on 2010-06-07
Yeah. There is a bank of switches marked "reserved"....I wonder.

---

### Post by sha.goyjo on 2010-06-09
Nobody? No help from anybody? I have a complete no-go on this system. I'd hate to have to eat my words and just say "no" to ubuntu.

---

