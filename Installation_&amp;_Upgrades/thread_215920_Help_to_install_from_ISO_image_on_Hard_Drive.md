---
title: "Help to install from ISO image on Hard Drive"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by Sable683 on 2006-07-14
I have just upgraded my 10GB hard drive with an 80 GB hard drive and found that my CD-Rom no longer works. My original intent was to install winXP on the first 35 GB and leave the remaining space for Ubuntu. 
Now that I have a bad CD-Rom drive, all I am left with is attempting to install Ubuntu from the ISO image on the hard drive. I do not have a BIOS boot option for any type of external devices, external CD-Roms or USB drives. I have searched high and low on the internet, I've been unable to find if anyone has installed Ubuntu from the ISO image on a hard drive.
My most recent attempt was to use the instructions on Marc Herbert's page. I then tried instlux, however, I do not know my proxie settings and cannot connect to the internet outside of winXP. If this helps at all, I have BootMagic 8.0 installed on my hard drive.

Any help is appreciated,

~Sable

---

### Post by Paerez on 2006-07-14
I dont know how to do this, but here is my idea:
1) Create a 1 gig partition that is empty
2) Write the contents of the ISO to that partition
3) Set the partition as bootable
4) Boot your computer off that partition, which will hopefully be ubuntu live
5) Install ubuntu with no swap partition
6) use the 1 gig partition and format it as swap after ubuntu is installed.

Sorry, but I don't know how to write an ISO to a partition, ask google.

---

### Post by Sable683 on 2006-07-14
Paerez,

     I tried that, it doesn't seem to work. The system just hangs. I have the hard drive partition set up in Boot Magic to allow that partition to be booted from. 
     I don't think that I have the correct system files to make this partition bootable. I don't have access to floppy disks (or a drive) to create one. Anyone know a way to create a partition that is bootable?

~Sable

---

