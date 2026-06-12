---
title: "triple boot oops -"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by TravMan63 on 2007-11-26
I had Ubuntu and SAM running fine as a dual boot.
I installed Elive last (nice grub screen, SAM has a nice one also)

When I installed elive - I config'd elive to use the previously defined boot partition... (I should have heeded the warning - it deleted/formatted all the contents of that partition) - I did make a backup of the menu.lst - and merged that with the one that elive created; however it won't work (missing files).

other than reinstalling Ubuntu and SAM, is it possible to fix this big boo boo?

TIA

---

### Post by rsambuca on 2007-11-26
You can easily re-install grub to whatever you want from a liveCD.  Pick basically any distro's live CD.

---

### Post by TravMan63 on 2007-11-26
grub is fine (sorta) - elive boots...

hmmm maybe just run grub? is that what you are suggesting?  then it would 'fix' the custom files for SAM and Ubuntu?

I'm noticing that ubuntu install disk wants to reformat the boot partition as well... grrr

---

### Post by rsambuca on 2007-11-26
No, you don't have to re-install any operating systems, just restore your grub.  An alternative is just to add ubuntu and SAM to your elive grub menu.lst.

---

### Post by TravMan63 on 2007-11-26
I did 'merge' the data from the original menu.lst (SAM and Ubuntu) - into the one created by elive

(this is what I understand your second method to be)

I tried grub --install-partition hda5 - with no luck

elive removed many files / formatted the hda5 partition

the partition table is as follows

hda1 fat32 windows (empty)
hda5 boot
hda6 ubuntu home
hda7 ubuntu /
hda8 swap


hda9 SAM home
hda10 SAM /
hda 2 elive home
hda 3 elive /

elive would not allow me to install in hda11 and 12...

-- edit
[http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html](http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html)
might work (I'm already in the process of reinstalling ubuntu - haven't started SAM yet...

I may have mistyped the command (I read the man pages  - which led me to type
[code]
grub --install-partition hda5
[\code]

when maybe the command was

[code]
grub-install /dev/hda5
[\code]

---

### Post by rsambuca on 2007-11-26
Post your /boot/grub/menu.lst

---

### Post by TravMan63 on 2007-11-26
the default elive menu.lst
--


# See [www.gnu.org/software/grub](www.gnu.org/software/grub) for details
# By default, boot the first entry
default 0
# Boot automatically after 5 seconds
timeout 25
gfxmenu /grub/message.elive

title Elive Gem  
# kernel path-to-kernel root=rootdevice kernelarguments
root (hd0,4)
kernel /vmlinuz-2.6.18-elive root=/dev/hda4 vga=791 splash=silent
initrd /initrd.img-2.6.18-elive


title Memtest | Memory RAM diagnostic tool
kernel /memtest


--
the list I merged: (recreated)
--

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,9)/usr/share/gfxboot/themes/pclinuxos/boot/message
default 0

title linux-SAM
kernel (hd0,4)/vmlinuz BOOT_IMAGE=linux-SAM root=/dev/hda10  splash=silent vga=788
initrd (hd0,4)/initrd.img

title linux-SAM-nonfb
kernel (hd0,4)/vmlinuz BOOT_IMAGE=linux-SAM-nonfb root=/dev/hda10 
initrd (hd0,4)/initrd.img

title SAM-failsafe
kernel (hd0,4)/vmlinuz BOOT_IMAGE=SAM-failsafe root=/dev/hda10  failsafe
initrd (hd0,4)/initrd.img

title windows
root (hd0,0)
makeactive
chainloader +1

title linux-Ubuntu CE
kernel (hd0,4)/vmlinuz-2.6.18.6.dev5.lgc BOOT_IMAGE=linux-Ubuntu_CE root=/dev/hda7 
initrd (hd0,4)/initrd.img

title Elive Gem  
# kernel path-to-kernel root=rootdevice kernelarguments
root (hd0,4)
kernel /vmlinuz-2.6.18-elive root=/dev/hda4 vga=791 splash=silent
initrd /initrd.img-2.6.18-elive

---

### Post by rsambuca on 2007-11-26
Wow, that is pretty messed up :)
Try the following changes:
> **TravMan63 said:**
> # See [www.gnu.org/software/grub](www.gnu.org/software/grub) for details
# By default, boot the first entry
default 0
# Boot automatically after 5 seconds
timeout 25
gfxmenu /grub/message.elive

title Elive Gem  
# kernel path-to-kernel root=rootdevice kernelarguments
root (hd0,4)
kernel /vmlinuz-2.6.18-elive root=/dev/hda4 vga=791 splash=silent
initrd /initrd.img-2.6.18-elive


title Memtest | Memory RAM diagnostic tool
kernel /memtest


--
the list I merged: (recreated)
--

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,9)/usr/share/gfxboot/themes/pclinuxos/boot/message
default 0

title linux-SAM
kernel (hd0,[COLOR="Red"]**9**[/COLOR])/vmlinuz BOOT_IMAGE=linux-SAM root=/dev/hda10  splash=silent vga=788
initrd (hd0,[COLOR="Red"]**9**[/COLOR])/initrd.img

title linux-SAM-nonfb
kernel (hd0,[COLOR="Red"]**9**[/COLOR])/vmlinuz BOOT_IMAGE=linux-SAM-nonfb root=/dev/hda10 
initrd (hd0,[COLOR="Red"]**9**[/COLOR])/initrd.img

title SAM-failsafe
kernel (hd0,[COLOR="Red"]**9**[/COLOR])/vmlinuz BOOT_IMAGE=SAM-failsafe root=/dev/hda10  failsafe
initrd (hd0,[COLOR="Red"]**9**[/COLOR])/initrd.img

title windows
root (hd0,0)
makeactive
chainloader +1

title linux-Ubuntu CE
kernel (hd0,[COLOR="Red"]**6**[/COLOR])/vmlinuz-2.6.18.6.dev5.lgc BOOT_IMAGE=linux-Ubuntu_CE root=/dev/hda7 
initrd (hd0[COLOR="Red"]**,6**[/COLOR])/initrd.img

title Elive Gem  
# kernel path-to-kernel root=rootdevice kernelarguments
root (hd0,4)
kernel /vmlinuz-2.6.18-elive root=/dev/hda4 vga=791 splash=silent
initrd /initrd.img-2.6.18-elive

---

### Post by TravMan63 on 2007-11-26
hey - way to see the partitions...

unfortunately - still 'flie not found errors'

Grub error 15's...

(used DSL 2.01 and Beaver to edit menu.lst)

---

### Post by rsambuca on 2007-11-26
You'll just have to find the correct name for the 'vmlinuz' and initrd.img files now.

---

### Post by TravMan63 on 2007-11-26
btw elive is installed on 3 and 4

---

### Post by TravMan63 on 2007-11-26
> You'll just have to find the correct name for the 'vmlinuz' and initrd.img files now.

and where would these files be found? in the / dir of the installations (/ of the / partitions)

thanks for your input

will try more tomorrow night...

---

### Post by meierfra on 2007-11-26
> I should have heeded the warning - it deleted/formatted all the contents of that partition) -

> and where would these files be found? in the / dir of the installations (/ of the / partitions)

I'm not sure. But I would expect that the kernel and initrd files were on the /boot partition which you reformated. So they should be gone.

---

### Post by TravMan63 on 2007-11-27
yes - I bet the files DO belong in the boot partition. (odd that they are not in say 'root' of the distro install)

initrd (hd0,6)/initrd.img

seems to me it is looking for the initrd,img in hd0,6 - should be a four not a six...

changed hda0,7 back to hda0,4 (the boot partition) - allowed ubuntu to load - I'll keep working on the others - I have an install of elive (on another pc - can grab those files) - but no SAM

So it appears I must reinstall - at least SAM...

I'll keep working and post my 'final' menu.lst and results

---

### Post by rsambuca on 2007-11-27
Sorry TravMan, I wasn't thinking straight the other day.  I wasn't considering the fact that you have a separate /boot partition.  As meierfra indicated, the kernels and initrd images are stored there, so if elive wiped the partition, then I am afraid you are probably hosed.  Maybe that is why I don't use a separate /boot for all of my different OS's! :)

---

### Post by meierfra on 2007-11-27
> allowed ubuntu to load

But then the ubuntu kernels could not have been on the /boot partition.
Was the /boot partition just used for  SAM?

---

### Post by TravMan63 on 2007-11-27
rsambuca
not to worry hehe (just booted (SAM) and I'm feeling pretty good)....

Correct - the files are stored in the boot folder (partition in my case - with all three there)

I was able to browse the SAM cd - and find kernel and 'other files'--- edited grub
and it's going....

I'll copy and post later... 

but - lesson learned - it may be better to have a separate boot (partition if needed) for each distro --- note tho - that I used the same - install Ubuntu, then SAM - SAM played nicely - elive did not, and when I reinstalled Ubuntu - it did not either... so it CAN be done - (sharing the same boot partition) - but - you might spend HOURS fixing it (or a lucky user can find this post and fix it faster)

thanks again

---

### Post by meierfra on 2007-11-27
deleted.

---

