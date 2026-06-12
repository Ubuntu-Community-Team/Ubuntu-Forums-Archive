---
title: "Ubuntu and Windows. Better with 2 drives?"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by jedispork on 2009-12-07
I'm thinking of picking up another hard drive. I'm going to use 1 for windows and another for ubuntu.  I would like to stay with 1 drive but aren't separate drives usually a better idea? I plan to start using the system image tool with windows 7 and not sure how well that would work with a ubuntu partition already loaded onto the disc if I needed to restore. I also have a storage drive formatted in ntfs. 

I had a suggestion for using a drive caddy.  This seems like a good idea too except switching the drives out could turn into a hassle.  I also thought about wubi but problems with sleep mode turned me off that idea.

Edit: Decided to stay with 1 drive for both o/s.

---

### Post by Ginsu543 on 2009-12-08
I have personally found it easier to have separate hard drives for Windows and Ubuntu because then I don't have to worry about Grub writing over NTLDR and vice versa. I can still dual-boot by telling Grub to look for NTLDR on the other drive to chainload, but I can also boot into Windows by simply changing the boot order in BIOS. But there is also nothing wrong with having both systems on the same drive as long as it does what you want. I also agree that a drive caddy would be a total hassle.

---

### Post by jedispork on 2009-12-09
I have 9.10 dual booting with windows 7 on a 160 gig ide drive.  Since its ide it shows as the second drive on my system. This caused me some trouble because the ubuntu installer kept wanting to use my storage drive (sata green) when I choose to "install side by side" with windows.  I had to manually partition and install grub for the configuration that I wanted. 

When I tried 9.04 with windows 7 grub simply would not work with my configuration. I received the ntldr error. Only way I could get it to work was to use easybcd and have the windows boot loader point to grub instead of the other way around. If I tried to load windows from grub then it came up with ntldr missing and I had to use bootrec and repair. This was very frustrating for a new user. 

I'm all set for now with 9.10. Still thinking about upgrading my hard drive. Would I notice any performance increase going from a 7200 rpm ide drive vs something like the western digital black?  I've read that drive performance in most situations are comparable from ide to sata.  I was hoping to hold out and go straight for a solid state drive when they come down in price a bit more.

thanks for the info

---

### Post by darkod on 2009-12-09
> **jedispork said:**
> I have 9.10 dual booting with windows 7 on a 160 gig ide drive.  Since its ide it shows as the second drive on my system. This caused me some trouble because the ubuntu installer kept wanting to use my storage drive (sata green) when I choose to "install side by side" with windows.  I had to manually partition and install grub for the configuration that I wanted. 


The first/second thing is not always related to IDE/SATA. Sometimes the boot order in BIOS makes the choice which will be hd0 and which hd1. Also, if a drive has all 4 partitions as primary, and in some other cases, it will not be offered for the guided install because no more partitions can be created on it. Before starting the installer it is best to have unallocated unpartitioned space ready on the drive. Otherwise using manual is a must because ubuntu can't make the choice for you which partition to delete. And it's better that it doesn't. :)

---

### Post by Zoot7 on 2009-12-09
The Thing I like to do is install my OS's on separate hard drives and tell my motherboard which one to boot from. It cuts out out a lot of hassle IMO. :)

---

### Post by jedispork on 2009-12-16
I couldn't resist and picked up a vertex ssd. Now I need to accomplish fitting windows 7 and ubuntu on a 30 gig drive. 

I'm planning to go with 8gb for ubuntu and disable swap unless I have issues.  I can get the windows install down really low also by disabling hibernation and system restore.

---

### Post by presence1960 on 2009-12-16
> **darkod said:**
> The first/second thing is not always related to IDE/SATA. Sometimes the boot order in BIOS makes the choice which will be hd0 and which hd1. Also, if a drive has all 4 partitions as primary, and in some other cases, it will not be offered for the guided install because no more partitions can be created on it. Before starting the installer it is best to have unallocated unpartitioned space ready on the drive. Otherwise using manual is a must because ubuntu can't make the choice for you which partition to delete. And it's better that it doesn't. :)

In legacy GRUB the designation (hdx,y) where x = device is strictly determined by the hard disk boot order in BIOS. Example you want to chainload windows which is on sda1, but your BIOS boots sdb first because Ubuntu is on sdb1 and GRUB 0.97 is on MBR of sdb. That means your designation for windows in the chainload stanza of GRUB 0.97 is (hd1,0) and would look like this:

```
title         Windows XP
rootnoverify  (hd1,0)
chainloader   +1
```

even though windows is on sda because BIOS loads the disks in the order sdb (hd0) then sda (hd1).

Now GRUB 2 has changed that and is for the most part automated. You can put GRUB 2 on MBR of a disk and it automatically finds other OSs and adds them to the GRUB menu. The only thing one needs to do to get GRUB 2 to boot is make sure that the disk that has GRUB 2 installed is first disk to boot in the BIOS hard disk boot order. GRUB 2 takes care of the rest.

Another thing that helps with GRUB 2 is this command from terminal ```
sudo dpkg-reconfigure grub-pc
```
This will allow you to choose which MBR Grub should be installed to during updates. Example: you have GRUB2 installed to sdb and sdb is booting first. Unfortunately when you update GRUB through Update manager the updates will go to sda thus causing problems. So to avoid that run the above command, you will go through a series of windows- one of which is to select which device should be used to install the updates to GRUB2. Choose the device which has GRUB 2 installed and that is used for booting your 9.10. Of course if you only have one hard disk this does not apply.

---

### Post by PhilMize on 2009-12-16
I run two 250gb drives installed windows 7 first then Mint. Grub recognized my windows install and I told it to install on the other hard drive. Grub sees my window install and I can boot into either just fine from grub. When in Linux I can see my Windows drive, but when in Winblows I cannot see my Ubuntu drive.:lolflag:

---

### Post by khelben1979 on 2009-12-16
> **jedispork said:**
> I'm thinking of picking up another hard drive. I'm going to use 1 for windows and another for ubuntu.  I would like to stay with 1 drive but aren't separate drives usually a better idea?

In my opinion, yes! Creates less hassle and this includes if you get a problem with the drive as well.

---

### Post by Shazaam on 2009-12-16
My setup...
sdb (sata)-
Extended partition taking up most of the drive with 2 versions of Ubuntu inside as Logical partitions (including one shared swap partition) and some unallocated space.
sda (pata)-
Windows XP taking up the whole drive.
Grub2 is on sdb and it is first in bios boot order. If the XP drive (or XP itself) decides to flake out I'm still good to go.

---

