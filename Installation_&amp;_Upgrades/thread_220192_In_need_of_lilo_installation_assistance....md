---
title: "In need of lilo installation assistance..."
date: 2006-07-21
forum: Installation &amp; Upgrades
---

### Post by squidward_tentacles on 2006-07-21
Hello,
OK here is the problem, I have an older box (P3 Micron Millenia) I used to run brezzy on it, but I had semi-retired it to the closet. I brought this out today with plans of making a dual-boot XP/ Dapper for the neighbour. I installed XP on hda1 and resized the partition to 5.86 gb with gparted, I then installed Dapper into the remaining space (8 gigs)on hda2. (its a small 14 gb disk) everything went well with both installs until the reboot after the live install of Dapper. Now all I get is a; 

"GRUB loading, please wait...."
"Error 17"

and alas, nothing more:( At this point I remembered I had  the identical problem when I first installed Breezy on this machine in the first place, something with the boot sector sizing, I thought I could correct this with a BIOS update, but there are none available. Anyway, the way I resolved the issue originally was to install LILO instead of GRUB, and it worked fine on Breezy. On the live install Dapper CD there does not seem to be any option for LILO. At this point I inserted the live CD, pulled up gparted, and and both OS's seem to be there but I cannot boot either. I think what I need to do is use the live CD and add a LILO boot loader for both OS's ( if this is possible):-| Unfortunantly I have no idea how to go about doing this...any help at all would be greatly appreciated, I have searched the threads, but I could not find any relevant instruction. If someone could post a link or a step-by step "how-to" I would be eternally grateful.
tia

---

### Post by Gannin on 2006-07-21
I'm not sure if the live CD has the ability to install LILO or not, but I know you can get the text-mode CD and go into the advanced installation options and install LILO that way.

---

### Post by squidward_tentacles on 2006-07-21
Thanks for the quick reply:) All right, If I booted the text/alternate cd in resucue mode, that would probably allow me to install LILO, do you know if LILO will recognize the XP partition? Or should I load the windows cd and run "fixmbr" ( a utility to recover the mbr) and then install LILO?? I would much rather fix this tha reinstall  both OS's again...

---

### Post by Gannin on 2006-07-21
I don't know if you'd need to run fixmbr or not, but it wouldn't be a bad idea to try it, just to be safe.

---

### Post by koshari on 2006-07-21
ranesh xosl is another option, i find it a very capable freeware boot manager,

---

### Post by squidward_tentacles on 2006-07-22
A day later, I have arrived at the conclusion that this particular box is a P.O.S., lol, I ve tried everything imaginable to fix the issue, live install, alt/text install,multiple complete removals of all partitions except the NTFS in partition 1, rescue options, reinstalling grub, reinstalling lilo( grub starts to install but fails quickly, and lilo just locks up entirely at 50%) I managed to rescue the windoze install using a truly awesome boot manager program ,(and a whole lot more) available here: [http://www.sysresccd.org/Sysresccd-manual-en_System_boot_floppy_disks](http://www.sysresccd.org/Sysresccd-manual-en_System_boot_floppy_disks) 
its basically a mountable disk already in .iso format, just download, burn, and insert in the damaged system, this utility is truly a mircale worker. I had trashed the mbr 9 ways to sunday with various install attempts, and a slew of dos utils (fixboot, fixmbr, bootcfg, etc](*,) ) and this program quickly booted XP in a matter of minutes and wrote a new mbr:)(even after I managed to change the error message from "GRUB error 17" to the dread "ntldr is missing" error, that none of the fixes given in other windozes forums would correct) 
However even using this util, I still could not get Dapper to install.
Grub error 18 or 17 every attempt, and lilo install just locked the system. I even inserted a different harddrive and tried to install Dapper on that after erasing the entire disk with the same exact same results. For some reason (unknown to me) lilo WOULD install and function correctly in Breezy:-? While im sure that this is a uncommon anomaly releated to the outdated BIOS on this Micron PC, I am passingly curious as to whats changed with lilo between Dapper and Breezy? At this point im downlaoding Breezy, guess ill just have to install Breezy and upgrade it to Dapper...

---

