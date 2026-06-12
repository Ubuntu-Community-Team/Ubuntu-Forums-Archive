---
title: "Cloning an ubuntu installation on mutiple PCs"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by saltydog on 2008-03-14
I am on the process to start a massive installation of Ubuntu 7.10 on a large number of new PC (identical hardware).
I have made a lot of modifications to the default system (new drivers, new themes, different filesystem), so now I have a perfcet machine to be replicated hundreds of time.

I can make a DVD disk image of the machine with Clonezilla and them replicate the DVD on each new PC, but I am wondering how can I do for the username/password issue... A large number of customizations are in the /home directory, so how can I easily duplicate the system, leaving to the user the option to choose his username/password withoput loosing all the customizations I made in /home?

---

### Post by mrsteveman1 on 2008-03-14
What about the OEM install option? Like, do the single install with the OEM cd and set it to do setup on first boot. I think it's supposed to ask the user for their name and password on first boot, or do you already have that stuff setup?

I think there is also a way to force a system to do this on the next bootup regardless of how you installed it.

Perhaps you could make a new .deb package that reads the user name from the machine and modifies the files you want relative to the correct home dir?

---

### Post by saltydog on 2008-03-14
Yes, I will try to give OEM-setup a try.
I'll be back with results.

---

### Post by ryanhaigh on 2008-03-14
When a new user is created the files in /etc/skel are used as a template for what goes into their home directory, Ubuntu has a symbolic link to the Examples but you could put whatever you want in there.

---

### Post by loyeyoung on 2008-03-14
A deployment of a large number of identical Ubuntu machines in an organizational setting is not a trivial task. The assumptions baked into the default Ubuntu installation and configuration routines are not optimized for that situation. Fortunately, though, this is open source, so the tools are available to tailor Ubuntu to your particular situation. 

The problem with using a DVD image for a replicated installation is that the /etc/fstab file and udev need to know the UUID of the specific hardware on the machine. If the /etc/fstab file and the udev directory have the wrong UUIDs, you are going to get unpredictable results when the machine is booted on its own.

My company is a manufacturer of computers that ship with Ubuntu preinstalled; here's our strategy:

We set up a PXE netboot on a server. The PXE server directs the client machine to a repository that runs the OEM install. Because we already know what the answers to the questions that the install routine will ask, we have a preseed file that provides the answers for an automatic install. Thus, we simply turn the machine on and press Enter when the boot menu appears. The system installs the OS, reboots itself at the end, and we have a completely installed system, ready for burn in and testing. 

Because we don't have an operating system on the hard drive when the machine is booted the first time, we set the BIOS boot order to HDD > CD-ROM > PXE. The great thing about that order is that it boots to the PXE image and installs the operating system on the first boot, but boots to  the hard drive and runs the new OS on the reboot. Obviously, if you are overwriting another OS, you'll need to change the boot order and then change it back when you are done. 

It's taken us some work to figure out all the pieces, and we are still learning and getting the kinks worked out, but we are steadily reducing manufacturing time using this strategy. You'll have to get PXE, DNS, DHCP, and the local repository mirror all working correctly, and you'll have to write the preseed file and adjust the install script for your particular situation. It's work, but once the work is done, it's extremely efficient. 

One other thing that I've learned from bitter experience: When you are setting up an entire organization's network on Ubuntu, BE SURE THAT YOU REMOVE AVAHI, ITS mDNS COUSINS, AND NETWORK MANAGER FROM THE PACKAGE INSTALL LIST. Unless you do, setting up and managing a stable network configuration will be an arduous and frustrating ordeal. If you are in the United States and are subject to the Sarbanes Oxley control objectives (CoBIT), your SOX auditor may have problems with the way that Avahi and Network Manager override the network configurations to connect contrary to the information control policies of the organization. 

Let us know how it all turns out. 

Good luck!

Loye Young
Isaac & Young Computer Company
Laredo, Texas
[http://www.iycc.biz](http://www.iycc.biz)

---

### Post by Dave_Man on 2008-03-14
Hi, 

I was in your exact situation.
I just used ghost4linux to make an image and distributed the image to all the stations.
My stations had different hardware and it sill worked great.
I set an FTP to host the image itself and g4l just contacted that FTP server and downloaded the image by itself.

Not as efficient as using a PXE server but its way easier.

Dave.

---

### Post by saltydog on 2008-03-16
One last question. Once I'll have the iso image (Clonezilla) of the whole installation, how can I setup an easy bootable DVD that will restore in just one shot the image on the new PCs?

---

### Post by saltydog on 2008-03-19
> **loyeyoung said:**
> 

The problem with using a DVD image for a replicated installation is that the /etc/fstab file and udev need to know the UUID of the specific hardware on the machine. If the /etc/fstab file and the udev directory have the wrong UUIDs, you are going to get unpredictable results when the machine is booted on its own.
[http://www.iycc.biz](http://www.iycc.biz)

Loye, you can avoid this but replacing the UUID with /dev/sda1

---

### Post by ryanhaigh on 2008-03-19
I don't know whether it will work the same with clonezilla but when I have used Acronis TrueImage to backup/restore the UUIDs of the restored partitions have matched those of the original backup. 

If however you do have this issue remember that grub also uses UUIDs.

---

### Post by loyeyoung on 2008-04-13
>Loye, you can avoid this by replacing the UUID with /dev/sda

It is possible, but that merely brings you back to the problem the UUIDs were meant to overcome, which is that one cannot be sure that the /dev/sda will get assigned to the same drive on every reboot. The only way that udev knows which drive should get assigned which device name is the UUID.

---

### Post by mrsteveman1 on 2008-04-13
Perhaps instead of uuid, you can use filesystem labels?

I believe ubuntu (all recent versions, since the recent ones use udev), by default creates devices in /dev/disk/by-label for any local drive with the labels found on disk.

Perhaps simply label your root filesystem as root, and then specify this as your root drive in grub and in fstab?

---

### Post by ryanhaigh on 2008-04-13
> **loyeyoung said:**
> It is possible, but that merely brings you back to the problem the UUIDs were meant to overcome, which is that one cannot be sure that the /dev/sda will get assigned to the same drive on every reboot. The only way that udev knows which drive should get assigned which device name is the UUID.

Thanks for that bit of information I always wondered why they made the decision to use UUIDs. I think using labels would be a better idea as they would be more intuitive and I believe this might be what RH/Fedora uses?

---

### Post by gza on 2008-04-20
I use clonezilla to do this for both linux and windows. Takes a little work to get going but, it is worth it.

I recently started using this instead of renewing ghost. I have better ways to spend that money.

I even had to write up a little guide. Click on my name to view it. I don't want to spam up the thread with long links.
[Mike]("http://packratstudios.com/index.php/2008/04/20/how-to-setup-clonezilla-on-linux-ubuntu-quick-start-guide/")

---

### Post by saltydog on 2008-04-21
> **loyeyoung said:**
> 

It is possible, but that merely brings you back to the problem the UUIDs were meant to overcome, which is that one cannot be sure that the /dev/sda will get assigned to the same drive on every reboot. The only way that udev knows which drive should get assigned which device name is the UUID.

Your are right, but in this case /dev/sda is the only hard disk of the PC.

---

### Post by loyeyoung on 2008-06-18
> Your are right, but in this case /dev/sda is the only hard disk of the PC.
Your CD-ROM or DVD drive will use the same device naming convention, so you could well end up with /dev/sda being the optical drive and /dev/sdb being the hard disk.

---

