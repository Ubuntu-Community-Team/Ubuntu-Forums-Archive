---
title: "Adding one disk, removing one disk, - How to correctly move files, mount and umount?"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by ozite on 2007-05-25
Adding one disk, removing one disk, - How to correctly move files, mount and umount?

Current Setup:
Ubuntu 7.04 and MythTV as Combined Backend, Frontend, & Regular Desktop
Asus A8N-E S939, AMD 3200+ Venice, 1 GB (2x512MB) DDR400 Corsair Value Select, Jaton MX400 NVidia 64 MB (PCI)
Hauppauge PVR-250, and
WD(?) 13 GB IDE  (/home, swap)  (IDE1 M)
NEC DVD-RW (IDE1 S)
Seagate 80 GB IDE for MythTV recording storage  (/var/lib) (IDE2 M)
Maxtor(?) 10 GB IDE for MythTV video (AVI) and music (MP3) storage  (/musicmov)(IDE2 S)

I primarily use this setup for MythTV and I have been very happy with it.  I initially installed with Edgy, then upgraded to Feisty. Surprisingly easy, except for a small problem with LIRC that was easily corrected.

Goal:
I want to add a Seagate 7200.8 250 GB SATA150 to the box and remove the 10 GB drive. The 250 GB disk is currently formatted for Windows.
The 250 GB disk will be the new storage location for MythTV recordings (/var/lib)
The 80 GB disk will be the new storage location for music and movies (/musicmov)
The 10 GB disk will be removed from the system.
I would like to move current MythTV recordings from the 80 GB to the 250 GB disk.  I would like to move data from the 10 GB disk to the 80 GB disk. 

Here is what I though I should do, based on what I read. I am not an expert, so I would be comfortable using GParted. Physically install the 250 GB SATA disk and start Ubuntu. Execute "sudo lshw -C disk" to see if the disk was installed and get the logical names for each of the drives.   Open GParted, find the drive, remove the Windows partition and add a new primary partition and use the ext3 filesystem, then apply to complete and say good-bye to Windows. 

Stop the MythTV backend, since it may be using /var/lib "sudo /etc/init.d/mythtv-backend stop".

Here is where I am confused about how to proceed, since the idea I have seems too complex.

Choose a mount point to for temporary storage "sudo mkdir /tempstor".  

I don't know the logical names yet, so I'll just put the capacities and a '?' for now.

"sudo mount /dev/hd(250?) /tempstor"

Have automatic mount at boot.
"sudo nano /etc/fstab" and add   "/dev/hd(250?)    /tempstor   ext3    defaults     0        2" then "sudo mount -a".

Make subdirectories  /tempstor/mmov and /tempstor/vlib.  Copy files from /musicmov to /tempstor/mmov and copy files from var/lib to /tempstor/vlib.  

Unmount the 10GB disk
"sudo umount /dev/hd(10GB)"
Unmount the 80GB disk
"sudo umount /dev/hd(80GB)"
Mount the 80GB disk
"sudo mount /dev/hd(80GB) /musicmov"
Mount the 250GB disk
"sudo mount /dev/hd(250GB) /var/lib"
Move the files from /tempstor/mmov to musicmov, then move the files from /tempstor/vlib to /var/lib.
Unmount temporary storage using "sudo umount /tempstor"
Then edit "sudo nano /etc/fstab"  to have lines...
"/dev/hd(250?)    /var/lib   ext3    defaults     0        2"
"/dev/hd(80?)    /musicmov   ext3    defaults     0        2"
"sudo mount -a"

Shut down and remove the 10GB drive.

Will the above procedures work, or is there an error in my understanding of mount and umount and how filesystems work in general.
It seems since I mounted the 250 GB drive twice...that will not work. I'm sure it is much simpler than this.

Thanks for any help and I welcome an elegant (or even better - a correct!) solution.

---

### Post by Paperclips4u on 2007-05-25
I'm not sure about the mount/unmount procedures, but if you want to transfer data from the 10GB drive over to the new drive to save data you can use the dd command. In the terminal type" :$ dd --help"
This will tell you everything you need to know about dd.

---

