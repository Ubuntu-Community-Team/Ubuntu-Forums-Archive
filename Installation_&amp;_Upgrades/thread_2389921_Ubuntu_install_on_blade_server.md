---
title: "Ubuntu install on blade server"
date: 2018-04-23
forum: Installation &amp; Upgrades
---

### Post by supert8ch on 2018-04-23
I have installed Ubuntu on many desktops with no issues. I acquired a Dell R200 blade server with dual drives and having issues. Server came by default with Windows 2003 server edition. Bios shows 2 500 gig drives, Windows shows 1 drive for C: and the other drive un-allocated. During install of Ubuntu it sees the main drive and states "One or more drives containing Serial ATA RAID configurations have been found. Do you wish to activate these RAID devices." I tried doing no and  manual, which takes me to "Partition disks" and only shows a SCSI2 drive. So this is the point I am lost. I am looking to set this up for home to use with media sharing. I want to set up so I can install 3 virtual system, camera system, media sharing and a test bench for some applications. nothing hardcore as for usage. I can provide some screen
 [ATTACH=CONFIG]279421[/ATTACH][ATTACH=CONFIG]279422[/ATTACH][ATTACH=CONFIG]279423[/ATTACH][ATTACH=CONFIG]279424[/ATTACH]

---

### Post by TheFu on 2018-04-24
If you don't want HW-RAID, say no about activating and wipe both disks during the install.
Might need to flash boot into "Try Ubuntu" mode and completely wipe the disks.  Use gparted for that and clear any flags.

---

### Post by SeijiSensei on 2018-04-25
I built a firewall router on a similar Dell blade.  The server came new from the factory with the two 500GB drives in a hardware RAID1 configuration.  Dell uses SAS controllers which are well-supported by Linux.  I use CentOS on servers, and it recognized the configuration immediately and set up the array as a single /dev/sda device.  I believe I gave Ubuntu a try at the time (five years ago or more), and it was less capable of configuring itself during installation.  Given your comments about the installation process, that may not be as true today.

If you decline using the devices in a RAID configuration, is that "SCSI2" drive one of the pair of 500's?  If, during boot, you enter the configuration for the RAID adapter, what does it show?

Given that you intend to do media sharing, you're going to need another fairly large hard drive anyway.  So I'd put the 500's in a RAID1, install Ubuntu on that, and buy one or more 4 terabyte drives for data storage.  Does this machine support hot-swap devices?  If so, you might want to buy drives that work with hot-swap adapters.  NewEgg has some Dell original equipment drives, but they're a bit [pricey]("https://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100167523%2050010772&IsNodeId=1&Description=hot%20swap%20drive&bop=And&PageSize=36&order=BESTMATCH").

---

### Post by supert8ch on 2018-04-25
> **SeijiSensei said:**
> I built a firewall router on a similar Dell blade.  The server came new from the factory with the two 500GB drives in a hardware RAID1 configuration.  Dell uses SAS controllers which are well-supported by Linux.  I use CentOS on servers, and it recognized the configuration immediately and set up the array as a single /dev/sda device.  I believe I gave Ubuntu a try at the time (five years ago or more), and it was less capable of configuring itself during installation.  Given your comments about the installation process, that may not be as true today.

I have never tried CentOS but willing to try anything. My old servers where just old desktops, now I hope to get this going. 

> If you decline using the devices in a RAID configuration, is that "SCSI2" drive one of the pair of 500's?  If, during boot, you enter the configuration for the RAID adapter, what does it show?

During bootup I see nothing about RAID. The SCSI is one of the drive installed as it matches numbers. I am thinking the other drive has never been used. I have never dealt with RAID so that is a learning curve. 

> Given that you intend to do media sharing, you're going to need another fairly large hard drive anyway.  So I'd put the 500's in a RAID1, install Ubuntu on that, and buy one or more 4 terabyte drives for data storage.  Does this machine support hot-swap devices?  If so, you might want to buy drives that work with hot-swap adapters.  NewEgg has some Dell original equipment drives, but they're a bit [pricey]("https://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100167523%2050010772&IsNodeId=1&Description=hot%20swap%20drive&bop=And&PageSize=36&order=BESTMATCH").

I currently have 3T of drives running on external USB docking stations for the media. System only has space to 2 internal drives, no they are not hot-swap-able. 

I am open to try anything. Just looking for proper directions to get it going. Thank you for responding with what you have.

---

### Post by supert8ch on 2018-04-25
So on bootup you select the try it before installing, Ubunut have gparted included?

---

### Post by TheFu on 2018-04-25
> **supert8ch said:**
> So on bootup you select the try it before installing, Ubunut have gparted included?

On the Live "Try it" run, you can install programs as needed.
Open a terminal and run
**sudo apt install gparted**
Or you can use the GUI software installer, but that is harder to explain.
The only downside is that at reboot, any software you installed is gone.  That isn't always bad.

---

### Post by SeijiSensei on 2018-04-26
If you enter the storage adapter BIOS, which should be an option at boot, what is it set to?  I'd set it to RAID1 and see if Linux sees the array as a single device.

---

### Post by supert8ch on 2018-04-26
Went through all BIOS settings and there is nothing listed as RAID. On bootup of cd, it has nothing listed as Try It, I am thinking this is because it is a server not a desktop cd? I am going to download CentOS and see if it shows me anything different on install. 
CD options
Install Ubuntu
Install MAAS Region Controller
Install MAAS Rack Controller
Check disc for defects
Test Memory
Boot from first hard drive
Rescue a broken system

---

### Post by SeijiSensei on 2018-04-26
You may not have a RAID controller; here's how to tell.

[https://www.dell.com/community/PowerEdge-HDD-SCSI-RAID/How-do-I-know-if-my-Poweredge-R200-has-RAID-controller/td-p/3698339](https://www.dell.com/community/PowerEdge-HDD-SCSI-RAID/How-do-I-know-if-my-Poweredge-R200-has-RAID-controller/td-p/3698339)

It's a bit concerning that the installer doesn't see the second hard drive if they are independent drives.  For the moment, I wouldn't worry about that drive and just install Ubuntu to the drive it sees.  If you don't care about whatever might be on that drive, let the installer configure the drive itself.

I'd check in the system BIOS one more time to see if both drives are marked active.

---

### Post by supert8ch on 2018-04-26
think i may have misspoken about RAID. Upon running install at detect storage i get this.

One or more drives containing MDADM containers (Intel/DDF RAID) have been found. Do you wish to activate these RAID devices? 
Activate MDADM containers (Intel/DDF RAID)?
If i say no. 
One or more drives containing Serial ATA RAID configurations have been found. Do you wish to activate these RAID devices? 
Acitvate  ATS RAID container?

---

### Post by TheFu on 2018-04-26
18.04 was just released. The server install does have a "try it" option, though I don't remember _exactly_ what it says.
[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes)
If I were installing a fresh system today, it would be 18.04 if I didn't have some reason to go with 16.04.
There is a bug in the release notes about RAID.

As for the mdadm (software RAID), if you don't wipe the disks first, there are issues.  I'd use **dd** to wipe it, then use parted to create a new GPT partition header and at least 1 partition on each disk.  If using UEFI, I'd create 3+ partitions as recommended.

---

### Post by QIII on 2018-04-26
@ supert8ch --

A surfeit of asterisks is more distracting than useful.  If you want to quote portions of a previous thread to make it clear what you are responding to, break the quote into chunks as I have done for you.  This will make your posts much easier to read and much more understandable.

Cheers!

---

