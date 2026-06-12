---
title: "This is starting to get on my nerves - &lt;Installation&gt;"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by Ub3r-L33ch on 2006-12-22
System Specs:
CPU: Athlon64 Dual Core (opteron 175 to be specific)
Motherboard: DFI SLI-DR Expert
RAM: 2GB
HDD: 36GB SATA Raptor(2) in RAID 0 - (Windows Install)
HDD: 30GB IDE - (Trying to install Ubuntu here)
HDD:  2 other IDE drives used as backup drives
CDs used:  Kubuntu 64-bit 6.06 Live CD (mailed to me) and 
Kubuntu 64-bit 6.10 Alternate Install (burned CD)

So I've been trying to install Kubuntu lately.  I have tried the 64-bit 6.06 Live CD and I have also tried the 6.10 64-bit Alternate Install CD.  Both exhibit the same problems.  I can start the install, get most of the way through it, but it always freezes up around the time of copying files, it never completes the install.

I have tried these install switches: noapic , nolapic, acpi=off

I originally was just going to do a VMware Workstation install with Linux as the Guest OS, I was actually able to get this to install just fine using the Live CD but was not satisfied with the performance so I decided to go with a real install.

I'm not worried about trying to setup a boot manager like LILO or whatever as I have no idea how I'd set that up with Windows being on a RAID 0 setup and all.  What I was going to do is install Linux on the 30GB drive and during the boot process just press "esc" to bring up the boot menu and select that drive when I want to go to Linux.  All this is irrelevant right now anyways though as I cant even get the damn install to finish.

I've successfully installed Linux on other computers before and it was a breeze, but they were a bit older and not as new as this one.

Can someone please help me?  They say Linux isnt that hard to use but so far I'm not seeing it.

---

### Post by budgie9 on 2006-12-22
I have put this in a previous post, I don't know if it worked with that person requesting help, but it has worked on a friends computer.
We took off the SATA drive and the install went well on to the IDE, with the 6.06 version. Then we added the SATA drive back.
If it works or not  for you, please post back it would be  good for others to know.

---

### Post by Ub3r-L33ch on 2006-12-22
> **budgie9 said:**
> I have put this in a previous post, I don't know if it worked with that person requesting help, but it has worked on a friends computer.
We took off the SATA drive and the install went well on to the IDE, with the 6.06 version. Then we added the SATA drive back.
If it works or not  for you, please post back it would be  good for others to know.

Ok I'm willing to give anything a try at this point.  I'll let you know what happens.

---

### Post by GSF on 2006-12-23
> **budgie9 said:**
> I have put this in a previous post, I don't know if it worked with that person requesting help, but it has worked on a friends computer.
We took off the SATA drive and the install went well on to the IDE, with the 6.06 version. Then we added the SATA drive back.
If it works or not  for you, please post back it would be  good for others to know.

yeap, there seems to be a problem with the installer and sata... (6.10 for sure) so if you want to install on IDE it should be fine.... if you want to install on sata, you just have to retry 4-5 times or so.. (workaround) .. i think someone should add it in the known issues wiki... i just post this because im so happy i can now enjoy ubuntu on my new sata 120gb disk :D :D :D :D

---

### Post by logos34 on 2006-12-23
I agree--disconect the cables to the other hard drives before install because the bootloader (grub) wants to install to the first detected drive on the system (your raid volume i'm guessing), which causes a lot of problems for people (esp. ext, USB).  You also might want to make sure your drive with ubuntu is primary 'master' (ide channel 1/ide0), that way you can set the boot order in the BIOS to boot that drive first.  Then when grub pops up on every start you can choose where to go--no need to enter the bios each time to specify a disk.

---

### Post by Ub3r-L33ch on 2006-12-23
> **logos34 said:**
> I agree--disconect the cables to the other hard drives before install because the bootloader (grub) wants to install to the first detected drive on the system (your raid volume i'm guessing), which causes a lot of problems for people (esp. ext, USB).  You also might want to make sure your drive with ubuntu is primary 'master' (ide channel 1/ide0), that way you can set the boot order in the BIOS to boot that drive first.  Then when grub pops up on every start you can choose where to go--no need to enter the bios each time to specify a disk.

Well I dont have to go in to the BIOS to specify a disk, pressing ESC just brings up a boot menu and I tell it which drive to boot to, it takes like 2 seconds, no big deal.

I'm still having problems with the install though.  I disconnected all my SATA drives and it is still freezing up around the copying files process, sometimes even freezes up setting up the partitions.  I know the drive I'm trying to install to works fine, I've had it for years and I tested it not to long ago and had no errors.

I appreciate the help so far, what else can I try guys?

Edit:  For shits n giggles I pulled out some RAM so I only had 1GB installed, still ran in to lockups.  I also tested the 1GB of RAM with memtest and it passed just fine.

---

### Post by logos34 on 2006-12-23
Do you get any error messages before your machine freezes?

If you're getting the exact same problems with both the pressed cd and the one you burned, then we can eliminate the cd media as the source of the problem.  I assume you checked the md5sum on the downloaded .iso and that you burned it at 4X speed or less. And you said you ran memtest, so its not the ram. 

Hadware issue?  That's a fairly bleeding edge mobo you have there (at least for linux) -- it's still listed as 'new' on dfi's site. It wouldn't surprise me if edgy (not to mention dapper) was having a problem with something related to SLI or your graphics card(s).

I know you said the drive is ok, but you might just for the hell of it try the install on one of your backup disks. 

Try the x64 Ubuntu install cd (I noticed at least one other person has complained about Kubuntu install).  If it works you can add Kubuntu-desktop.  Or try the 32-bit version of each.  

That's what I'd do at this point.

Sorry, wish I had some answers.

You should start a new thread over in the 64-bit forum.

---

### Post by gonesolo on 2006-12-24
](*,) Quick question. did you check the MD5 checksums when you d/l the install iso? I had the same problems on my system about a week ago on a DFI DAGF motherboard with 2 sata hard disks did a lot of the same steps you have (including testing memory and hard disks) but it turned out to be a damaged download. 

re-downloaded and installed and worked ok.

---

