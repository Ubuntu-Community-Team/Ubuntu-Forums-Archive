---
title: "Need help with chainloading grub2 for a multiboot setup"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by streamsanddragonflies on 2010-11-24
Hi!

 I have attempted to multiboot 3 Windows versions and the problem I had was intalling a second Ubuntu. (Don't ask!) I had success multibooting with grub legacy on an older computer but this computer has a tricky mb which won't let me install grub to the second drive on an IDE port. (I have other HDD installed in RAID 0 on the other sata ports supported by mb (fakeraid) but I will use these for video editing  as scratch disks later. One other HDD used for data is on the Raid port but not in an array).  

I succeeded in installing Ubuntu desktop only after realising that I had to first switch my disk order in bios- otherwise the system would just hang.  U. Desktop grub had sucessfully found Win bootloader links to both XP and Vista.  I then installed Win 7 and used easy BCD and grub2 boot entry to link back to my Ubuntu Desktop grub 2 menu.  

The problem occured when installing Ubuntu Studio ( for which I created a separate /boot partition) and I decided to install grub2 to mbr since it had correctly detected all my OSes!  But then it seems it never installed correctly to the mbr.  I still had Win 7 BCD bootloader in MBR! I tried to link easy BCD boot entry to the /boot drive but that didn't work and I ended up having to reinstall Win7 because I had overrid the BCD with faulty neogrub mapping entries- which I then removed and kept the orginal neogrub that still points to Ubuntu Desktop grub menu.

I also now realise that because I installed Ubuntu Desktop before I switched the HDD boot order in bios- U. Desktop's grub.cfg sees root of Desktop grub differently than neogrub BCD does root=(hd4,7) vs multiboot kludge (hd3,6) and at first I tried to install grub in the wrong hdds and partitions- I based mapping on neogrub's to find /Boot (hd3,2) and (hd3, 1) which is wrong!

What I am attempting to do now is to chainload grub2 from my Ubuntu studio located in /Boot with what I thought was the right mapping but still no success:

menuentry 'Chainloader' {
    insmod chain
    set root=(hd4,2)
    chainloader +1
}

yielded    error: hd 4,2 cannot get C/H/S values   press any key to continue

Can someone guide me in identifying the right mapping of my boot drive to chainload and also force install-grub there as well in the hopes that that is all I need to boot into U. Studio!

I will attach Boot_info_script; at this point I am too tired and afraid that I will keep on installing grub to the wrong drive!


Note: I somehow got a problem loading into XP after all these failed attempts and a system 32 file seems to have gotten lost-haven"t attempted to fix yet.  Just wondering in passing what happens if I chainloaded into Windows by error- if that could have corrupted it? Right now 3 out of 5 OS are bootable. I hope I can repair it without messing up my mbr again.

---

### Post by streamsanddragonflies on 2010-11-24
Since I was tired last night, I want to clarify that all my HDDs are Sata2.  I just set the ports connecting the 2  HDDs with all the OSes (which are controlled by a separate chip) to IDE mode, while I set the other Sata ports to Raid mode.

My MB is Gigabyte GA-790XTA-UD4 and is supposed to allow me to set any HDD in any boot order exept for those in the Fakeraid array, I suppose.  My mb has other quirks; like the IRQ suddenly changing, and a PCI ethernet card installed as a backup, suddenly freed up again and can be used. I had to install it since once in a while, my onboard lan suddenly stops working, claiming that the cable is broken. And then starts working again without my touching the cable....go figure!

---

### Post by oldfred on 2010-11-24
Not sure how easyBCD works, but when booting grub the boot drive is always hd0. I have 3 drives and have some entries to chainboot to the other MBR, but the number is not always consistent as I can boot any of my 3 drives. I put a setting in but sometimes have to manual edit grub as I boot.

I find my SATA drives are in order by SATA port and each drive follows that order for Ubuntu sda, sdb & sdc. And grub makes each drive in order except boot is hd0 or first. Ubuntu uses UUID in the search so drive number is not critical in all cases.

---

### Post by streamsanddragonflies on 2010-11-25
from my first post > Note: I somehow got a problem loading into XP after all these failed attempts and a system 32 file seems to have gotten lost-haven"t attempted to fix yet.
 Just wondering in passing what happens if I chainloaded into Windows by error- if that could have corrupted it? Right now 3 out of 5 OS are bootable. I hope I can repair it without messing up my mbr again.


booting into safe mode with a console (forget the exact term) and applying CHKDSK C: /F  allowed me too boot back into XP - YEAH!- and now both my onboard lan and network card work too!  Somehow the first CHKDSK must have not recovered all errors.

 That was it?! Now I really really don't want to put grub in the wrong partition again lol!


oldfred, I will look into sata ports as /dev designation but I think the RAID array complicates this, judging from my f disk -l 

also can you chainload grub to a boot drive using UUID? ok will try to figure out how to script it right and will go with that since I notice that my dev mapping may get skewed but the UUID remains the same no matter wether booting from a HDD or live disk etc... thanks!

---

### Post by oldfred on 2010-11-25
The rule on chkdsk is to run it until there are no errors as it does not fix everything on one pass.

I have never seen a chainload by UUID, just drive, partition. I find RAID and LVM more complicated than I want and do not offer any real advantages for me. 

I see RAID as important for servers as uptime, and response time are vital. Then with the hardware RAIDs you can also hot swap a drive to keep system going. For standard desktops RAID offers little, I cannot type faster and my one internet connection will not be any faster with RAID. Do not confuse RAID with backups as once deleted or changed it is changed in all copies of a RAID set.

---

### Post by streamsanddragonflies on 2012-01-21
I'm really behind on the forum, I've been busy...just realised that alot of threads should be marked solved. 

 Turns out grub got installed on one of the drives in the fake raid array! Go figure. I've been succesfully chainloading once I figured out where grub ended up.

---

