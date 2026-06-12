---
title: "Cannot get linux to dual boot again"
date: 2012-01-08
forum: Installation &amp; Upgrades
---

### Post by Kubinb on 2012-01-08
Hello,
Whelp I decided to upgrade my computer mobo processor ram vidcard etc basically everything except my hdd's. Now prior to the hardware upgrade i had my computer dual booting windows 7 and ubuntu 11.10 with grub2 with no issues each os being on its own separate hdd. By a friends suggestion, no formatting or any preparation was needed when upgrading hardware (last tim ei changed motherboards i had to format i was told this is no longer the case with new chipsets) so i put in the new goods and fired it up. sure enough i get a 

hd0 out of disk
grub rescue>

i said ok maybe i just need to reinstall grub and did so... did not solve issue

ok i guess ill just format Linux drive and reinstall... did not solve issue

well lets see if i can at least recover mbr for windows... file not found cant boot or fix mbr for windows

ok maybe i need to format both os hard drives and reinstall obviously windows must install first... istalled windows and it boots to windows.

now to reinstall ubuntu...

hd0 out of disk
grub rescue>

and mbr is screwed again back at square 1. as much as i tried to manually configure grub and install it and try booting to different disks and trying to install grub on different disks i cannot fix the issue. even tried to manually set boot partition and root for linux to no resolution. im almost thinking that maybe this cheap asrock mobo i put in just doesnt have the bios capabilities to handle grub for dual boot? i just dont see this being true...
at this point if i boot into the windows drive i get:

hd1 out of disk

if i boot into the linux drive i get

hd0 out of disk

could it possibly be that i have 2 different grub installs which is messing everything up? but i dont understand how that can be since i formatted the linux drive probably 12 times and reinstalled linux trying different methods... 

i read about the system config txt script and can run that and post it if it will help with interpreting my issue (right now im on my laptop) 

please help ubuntu forums! linux is what my school runs on and all my programming is done on linux.

---

### Post by Kubinb on 2012-01-08
My mother board is an asrock A770DE+ with a phenom II x4 the bios is latest (1.70 i believe) and all settings i could think of in the bios is set right. even tried default configuration...

here is my boot info script results:

---

### Post by raja.genupula on 2012-01-09
The first default try for Grub errors we can do is grub restore using boot -repair.
look at my signature for that and please post the output of boot info script with in code tags by placing total code in # tags (in this window at 2nd menu list 3rd one from last) . 

All The best.

---

### Post by Mark Phelps on 2012-01-09
> **Kubinb said:**
> Hello, Whelp I decided to upgrade my computer mobo processor ram vidcard etc basically everything except my hdd's. Now prior to the hardware upgrade i had my computer dual booting windows 7 and ubuntu 11.10 with grub2 with no issues each os being on its own separate hdd. By a friends suggestion, no formatting or any preparation was needed when upgrading hardware... 
While this is often true with Linux distros (new hardware is automatically detected and drivers installed), this is nearly NEVER true with Windows -- if it was, there wouldn't be all these software vendors out there selling products that let you restore/migrate Windows to different hardware!

> (last tim ei changed motherboards i had to format i was told this is no longer the case with new chipsets) 
Whomever told you that about Windows is mistaken...

Can you boot Win7 from its own drive, with only that drive connected?

If so, then do all your Ubuntu boot repairs with only the Ubuntu target drive connected.  

It's a simple matter to get dual-boot OS selection restored once you get both OSs running again from their individual drives.

---

### Post by Kubinb on 2012-01-09
Well i fixed windows mbr. windows boots. I disconnected all other hdd's except for the linux drive fixed the boot boot-repair
no luck same hd0 out of disk

i then formatted the hard drive and clean installed ubuntu (with no other hdd connected at all) 
rebooted:

hd0 out of disk
grub rescue>

as previously thought is it something to do with my bios?? it seems like my mobo just does not like GRUB. are there any certain settings grub does not work with on a mobo?

as of right now there is only the linux drive connected and all i get is 
hd0 out of disk
grub rescue>

---

### Post by dino99 on 2012-01-09
as grub has been built with your previous hardware, i suppose that now uuids have changed, but grub only knows the old ones.

in recovery mode , check the uuids:

sudo blkid
take note of them to modify, if necessary, the grub loader:

sudo gedit /etc/default/grub

compare the uuids, and set the new ones if they are differents

sudo update-grub

---

### Post by Kubinb on 2012-01-09
Shouldnt the UUID's not matter after formatting the hard drive completely? This is a fresh ubuntu and fresh grub install. all previous information has since been replaced...
as of right now i have a single hdd with a clean linux install on it and clean grub install that boots to hd0 out of disk.

i appeciate all  the help

---

### Post by Kubinb on 2012-01-09
Any other suggestions? Im willing to try anything to get this to work since i do all my school work on Linux.

please and thank you :-D

---

### Post by Slim Odds on 2012-01-09
Change the ordering of the hard drives in your BIOS.

---

### Post by Kubinb on 2012-01-09
Slim,
Currently there is only (1) hard drive connected to my mobo and in bios. I disconnected all other hard drives to rule out that possibility.

but thanks for the response

---

### Post by Kubinb on 2012-01-10
Is there no one with any experience with this issue? anyone know how to contact the developers?

---

### Post by lsemmens on 2012-06-17
Just as a thought. Have you deleted all partitions on your HDD and recreated them before reformat and re-load. There may be issues with the MBR that format alone will not fix.

---

### Post by black veils on 2012-06-17
could the ubuntu-designated drive be defective?  or maybe there are issues regarding UEFI ?

---

