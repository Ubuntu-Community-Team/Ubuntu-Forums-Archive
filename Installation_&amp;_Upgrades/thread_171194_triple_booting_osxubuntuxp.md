---
title: "triple booting osx/ubuntu/xp"
date: 2006-05-06
forum: Installation &amp; Upgrades
---

### Post by wilfordbrimley on 2006-05-06
i'm trying to figure out how to triple boot with ubuntu, i've got win xp and os x working fine, and set up my partitions manually with diskutil resizeVolume, as described in these howtos:
[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)
[http://www.ethicalhack.org/howto/triple_boot_howto.html](http://www.ethicalhack.org/howto/triple_boot_howto.html)
I've got a gentoo live cd and i'm downloading an ubuntu-5.10-install-i386 cd. I'm new to linux, and I'm not expecting this to go too smoothly, but i want to have a better idea of what i'm getting into. how much different is installing ubuntu different than the howto guides, specifically the second one that installs suse?  I'd really appreciate if anyone could help clarify the specifics for boostrapping ubuntu, so i don't end up having to scrap things and start over.  here are the questions i've had so far and some dumb guesses at answers i've made based on the howtos

1) where do i mount the ext3 partition?
/mnt/ubuntu 

2) where do i place lilo.conf? 
/mnt/ubuntu/etc/lilo.conf 

3) what should lilo.conf look like?
# Global LILO settings
boot=/dev/sda3          
prompt                  
timeout=50              
default=Ubuntu 	
# Kernel specific LILO settings
image=/boot/vmlinuz initrd=/boot/initrd
label= Ubuntu		
read-only               	
root=/dev/sda3

4) How do I install lilo, do I need to do the mounting that the SuSE guide does before executing "/sbin/lilo"

5) what do i do to mount the windows partition?
mkdir /mnt/windows && mount -t vfat /dev/sda4 /mnt/windows
cd /mnt/windows
dd if=/dev/sda3 of=ubuntu.mbr bs=512 count=1
echo 'C:\ubuntu.mbr="Ubuntu Linux"' >> /mnt/windows/boot.ini
cd && umount /mnt/windows

6) do i need to change the fstab file...and mount the windows partition and swap file like in steps 27 & 28 on the SuSE howto?

sorry for all the questions, i'm new to linux and most of the install guides in the getting started section were all how to use an install wizard now click the 'next' button and that didn't answer my questions and googling "bootstrapping ubuntu" got me a lot of stuff that was quite different than the general idea of the howtos.

i'm pretty well lost, and i'd really appreciate any help you all can offer.

thanks!
will

---

