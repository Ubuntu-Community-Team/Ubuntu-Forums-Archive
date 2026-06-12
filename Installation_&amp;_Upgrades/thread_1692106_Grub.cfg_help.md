---
title: "Grub.cfg help"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by ylafont on 2011-02-20
Need s ome help with grub2.
After much research and trial and error, I have been able to install grub on to a floppy disk image, in vmware with ubuntu 10.10 with the following commands. 
 
sudo fdformat /dev/fd0
sudo mkfs.fvat /dev/fd0
udisks --mount /dev/fd0
sudo grub -install --boot-directory=/media/floppy0 allow-floppy /dev/fd0 --force
 
Once I boot from this floppy disk i was able to get to the Grub2 command line. things appear normal. however, when I created a simple grub.cfg file in /media/floppy0/grub to see if the boot process was reading the files and it was. i created a few menu entries which were read correctly but found the all the other entries are being ignored. I am doing somethign wrong? did i make things worse by just having a simple cfg file? 
 
GRUB_TERMINAL_OUTPUT=gfxterm (line being ignored)
GRUb_GFXMODE=1024x768 (line being ignored)
GRUB_BACKGROUND=/grub/eclipse.png (line being ignored)
 
The png file is 8 bit and i have verifed that it is in /grub direcoty of the floppy.
 
can anyone point me in the right direction.

---

