---
title: "Ubuntu Installation Trouble - Affected Other Hard Drive"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by Barakka on 2007-09-16
Hello, 

I have a bit of a problem with Dual booting FC and Ubuntu:

Our machine has two hard-drives (both IDE). Before, the Master (Maxtor 160GB) ran FC6, and the slave (Western Digital 40GB) ran XP. Today, I decided to give Ubuntu a try - I switched the hd boot order in BIOS, load XP -
 popped in the live CD; clicked the "Install" on the desktop when it booted.

When the partition screen came, I made sure to select "Guided- take entire disk - hdb (Western Digital - the one that had the XP on it)"

Everything seemed to be going alright. It asked for username, pass, timezone, etc. When it rebooted, however - the screen says: 

"Error: Operating system could not be booted"

I thought that was odd, so I changed the boot order to boot to the Maxtor (FC6) drive. Grub loaded.. and then it passed it to Ubuntu. 

Luckily, I had Knoppix at hand (using at right now to post this) - so i went to investigate. Under the media folder, Knoppix recognizes three devices - /boot, 36G HD.. and floppy.

I looked in the 36G HD - and it had the standard "/" GNU/linux folders, i.e. "bin, usr, home.. so forth". They are the ubuntu ones, because I went into /home.. and saw the "Examples" that are packaged with the system.

So, Ubuntu hasn't written over FC6, which is a good thing. in the /boot folder, the grub.conf still has the FC6 in it.. (says it hasn't been modified since last night) - but is missing Ubuntu.

So, I'm puzzled. My guess is that Ubuntu installed itself on the Western Digital, but wrote over the MBR of the Maxtor. 

Does anyone know how I can get Fedora working again?

Much thanks in advance..

---

### Post by peabody on 2007-09-16
If you can chroot into your fedora root partition, you may be able to do a grub-install from there.  Keep in mind, this will probably make your ubuntu unreachable :).  Best bet, since it sounds like you can boot into Ubuntu, is to manually configure grub for both OSes.

---

### Post by Pumalite on 2007-09-16
Sure, edit your Ubuntu menu.lst and stick Fedora in it, but decide which order you are going to leave your hard drives in and then post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by Barakka on 2007-09-16
Thanks for the quick replies = ).

I'd.. like to leave the drives in the way they are. 

I'm a bit of a noob at linux in general, so I may need some help locating things to edit.

As for editing Ubuntu's menu.lst : is it under /boot/grub?

Should I copy/paste the fedora kernel descriptions from the grub.conf ... to the end of the menu.lst?

---

### Post by Pumalite on 2007-09-16
First backup:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back, the:
gksudo gedit /boot/grub/menu.lst
(Do the same with Fedora and copy+paste relevant portion in Ubuntu's menu.lst)
Then, save, exit and reboot.

---

### Post by Barakka on 2007-09-16
Did the back up and editing. Will reboot and see what happens = )

---

### Post by Barakka on 2007-09-16
It booted to Fedora - Thank you so much.

as you said above, here are the results of 

"sudo fdisk -lu" :

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63      208844      104391   83  Linux
/dev/hda2          208845   312576704   156183930   8e  Linux LVM

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    74862899    37431418+  83  Linux
/dev/hdb2        74862900    78156224     1646662+   5  Extended
/dev/hdb5        74862963    78156224     1646631   82  Linux swap / Solaris

---

### Post by Pumalite on 2007-09-16
You are welcome. Good luck. I imagine you can boot both OS's, right?

---

### Post by Barakka on 2007-09-16
Yes, the grub menu now lets me choose which one I want = )

Out of curiosity-  if I were to remove the Ubuntu disk, would the other one still load?

I ask, because Ubuntu is loading the /boot at startup, but fedora isn't mounting the Ubuntu disk by itself.

Thanks

---

### Post by Pumalite on 2007-09-16
You can mount the ubuntu partition in the terminal if you need to. Or you can add it to fstab

---

