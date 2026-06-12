---
title: "Installing on a dell Poweredge 2400"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by survient on 2007-12-22
I recently purchased a Dell Poweredge 2400 with a 6 drive Seagate SCSI raid 5 array, and attempted to install ubuntu server 7.10 on it. The install went through fine, was a little slow at the partitioner(while writing the changes) but overall went ok. When I boot it however, all I get is a:

aacraid: Host adapter abort request(x,x,x,x)
aacraid: Host adapter abort request(x,x,x,x)
aacraid: Host adapter abort request, SCSI hang?

repeated.....

quite a few times til eventually it stops and puts up an idle screen(monitor goes black until you hit the keyboard). I believe I may have partitioned this incorrectly, as this is my first time messing with raid and scsi, let alone both at the same time. My partition table is as follows:

partition 1: primary ext3 /
partition 2: swap
partition 3: primary ext3 /home

If anybody knows what I'm doing wrong, please let me know. Thanks.

---

### Post by twist2b on 2007-12-22
can you explain ALL of your specs..... also are you dual booting or making it the only OS.....
and does it start booting like the main page is loading?

in grub edit the ubuntu selection you choose to boot and change it from quite splash at the ending to just splash

tell us were it goes wrong

your partition is pritty wiered to.. it SHOULD be more simple then that :P just 2 partitions

---

### Post by survient on 2007-12-22
Ok, here goes:

Single OS: Ubuntu 7.10 Server Edition

6 x 18 GB SCSI Seagate Cheetahs in a Raid 5

2 x 600 Mhz PIII's

1 GB SDRAM

SCSI devices 	integrated Adaptec AIC-7890 Ultra2/LVD SCSI host adapter supporting four 1.6-inch SCSI hard-disk drives or six 1-inch SCSI hard-disk drives in internal bays

integrated Adaptec AIC-7880 Ultra/Wide SCSI host adapter supporting up to three SCSI devices in externally accessible front bays, implemented as Ultra/Narrow. An internal SCSI backplane provides a physical connection, hot-plug capability, termination, and automatic configuration for the internal SCSI hard-disk drives.
CD-ROM drive 	SCSI CD-ROM drive included with standard system

and I can't even get to grub(it auto loads ubuntu)

---

### Post by survient on 2007-12-22
If I have the option to do a hardware raid, should I do that over a software raid?

---

### Post by azidtripz on 2008-01-11
hmm i am having pretty much the same problem though i already had 7.04 installed and running fine until i did an upgrade.....  here is the post i made elsewhere

i have a poweredge 1650.


> Hello everyone, i seem to have run into a bit of a problem when following the guide
"[How To Upgrade An Ubuntu 7.04 Server ("The Perfect Setup" + ISPConfig) To Ubuntu 7.10]("http://www.howtoforge.com/upgrade-ubuntu-7.04-server-to-7.10")"

everything was going great and then right near the end it asks to reboot the computer so i do but now when it go's to boot the kernel it gives me the error "aacraid: Host adapter reset request. SCSI hang ?" with a number in front which go's up on each line until it gets to
[1148.073507] sd 2:0:0:0 [sda] assuming drive cache: write through

and then it appears to hang,

please help as i have no idea what could have done this...

thanks in advance

---

### Post by wrenchspinner on 2008-01-17
I am having a similiar problem. The install went well, but I got an error message saying my bios was too old -  not supported. The ubuntu seemed to run fine. I updated my bios to A09. Now the installer works OK but I get messages similiar to yours when I boot to the hard drive. Trying to use hardware raid Perc 2/si. 2 18gb scssi in hardware raid 1 container.

---

### Post by punkybouy on 2008-01-17
Try reconfiguring your Raid to single drives instead of a RAID setup.  Install Ubuntu on one drive and see if that works.  It could be a driver issue but Adaptec chips are pretty common so there should be a driver.  I have seen most Linux distros use Compaq/HP Raid cards and use a driver named CCISS without any problems.

---

### Post by punkybouy on 2008-01-18
There might be more help here:

[http://linux.dell.com/storage.shtml](http://linux.dell.com/storage.shtml)

---

### Post by wrenchspinner on 2008-01-21
server ubuntu is just not supported by dell or hp. Dell sells laptops loaded with ubuntu desktop. I grabbed up anothe server and am running a perc 2/si mirror with ubumtu 7.10 on another old dell 2400 with a03 bios. Perhaps it is possible to downgrade the a09 bios on the origional server to somrthing that will work with linux. I recall a document about dell bios rollback when win2k first hit the street. Dell has a08 on the ftp site. I have not yet tried a08 with ubuntu - I know it works with a01 and a03.

---

