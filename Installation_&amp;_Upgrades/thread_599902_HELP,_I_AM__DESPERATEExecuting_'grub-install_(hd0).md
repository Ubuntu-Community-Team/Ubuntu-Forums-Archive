---
title: "HELP, I AM  DESPERATE:Executing 'grub-install (hd0)' failed. This is a fatal error."
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by ciuci on 2007-11-01
I tryed installing ubuntu 7.10 for a million times, and i keep getting this error at 94% of the installation:
> Executing 'grub-install (hd0)' failed.

This is a fatal error.
SOMEONE PLEASE HELP ME! I AM DESPERATE!
(I know several topics exist wich cover the same problem, but nobody seems to have the answer, and i realy need help!! )

---

### Post by Pumalite on 2007-11-01
Is it a laptop?. You might have a 'recovery partition' at the beginning of the drive.

---

### Post by ciuci on 2007-11-02
nope, it is not a laptop! AMD Athlon Xp based desktop! if you need any other info just ask, but please find a cure for my disease! :( :lol: ...I also have windows Vista allready installed! Have i done my partition table wrong? is it not possible to have a 'recovery partition'(whatever that is) even if my computer is a desktop?

---

### Post by Pumalite on 2007-11-02
If you tried a Live CD and you failed, then try the Alternate CD.
Do md5sum on the iso, burn at 4x, check for CD corruption before install.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by ciuci on 2007-11-02
thank's a lot.... i am going to download the alternate cd! let's hope it'll work! ...there's an ubuntu/kiwi meeting in my town tomorrow ... i'll see if they dont have some "original" cd's, and if not, i'll start the download :P

---

### Post by Pumalite on 2007-11-02
One more note; with Vista you have to use Vista partitioner to allocate space first.

---

### Post by unisol on 2007-11-09
PUMALITE; if i have a recovery partition at the beginning ofthe drive, what do i need to do to install gutsy? hda1 was a recovery partition (which i dont need) try changing it to swap. no good. do i need to delete hda1 and create another swap. hda2= vista. hda3 =partition to install gutsy?

---

### Post by Pumalite on 2007-11-09
DBan your drive: [http://dban.sourceforge.net/](http://dban.sourceforge.net/). Then use Gparted Live CD:[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it, make one large partition of your whole drive, formatted ntfs.
Reinstall Vista. Allocate space for Ubuntu FROM within Vista. Then install Ubuntu.

---

### Post by Steve1961 on 2007-11-09
Just a thought, but when you use the alternative CD try installing grub to the root partition rather than attempting to write it to the mbr.  You can then use EasyBCD in vista to add Ubuntu to Vista's boot manager.  I use this method and it works well.

---

### Post by Computer Guru on 2007-11-11
grub-install isn't reliable. Enter the GRUB console then use the setup command like shown here: [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux) in the reinstalling GRUB section.

---

### Post by squall14716 on 2007-11-11
I got the same type error. Additionally, trying to do it manually with grub-install greets me with: The file /boot/grub/stage1 not read correctly.

Help, suggestions, ideas? I'm a dumbass and managed to screw up my Windows bootloader anyways, and with only a single DVD-RW drive, I'm stuck in this LiveCD unable to burn a new one.

---

### Post by Pumalite on 2007-11-11
[http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5)
Get a Super Grub to fix your Windows MBR: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by [censored] on 2008-02-14
> **Pumalite said:**
> If you tried a Live CD and you failed, then try the Alternate CD.
Do md5sum on the iso, burn at 4x, check for CD corruption before install.
]

Can u install using the Alternate CD? I thought the Alternate CD was just for upgrading.

---

