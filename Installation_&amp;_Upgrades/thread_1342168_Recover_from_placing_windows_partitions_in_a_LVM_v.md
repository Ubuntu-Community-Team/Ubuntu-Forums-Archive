---
title: "Recover from placing windows partitions in a LVM volume"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by software mechanic on 2009-11-30
I did something stupid while installing Ubuntu Studio 9.10 (x64) on an IBM T61 tablet notebook. I placed the windows partitions in an LVM volume. I can't boot to windows from grub. Grub sees the windows partition, SW_Preload, and when I attempt boot to Vista, nothing happens. PhotoRec was used to recover all the data from the windows partitions.

Testdisk was used to make the windows partitions visible by changing the filesystem type to NTFS and remove the LVM identifier. The Vista CD was used to fix the boot sector and MBR.
[FONT=Arial]
[/FONT] [FONT=Arial][SIZE=2]gParted recognized the windows partition as [/SIZE][/FONT][FONT=Arial][SIZE=2] /dev/sda2, SW_Preload. /dev/sda2 is seen as bootable and shows no used space. [/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2]When the Windows Vista CD was used in rescue mode, the following was observed:
[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]-Start up repair discovered 1 error. Log file showed no failing tests and the root cause was “Boot status indicated that the OS booted successfully.”[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]-The flowing commands were executed: Bootrec /fixmbr, Bootrec /fixboot, Bootrec /rebuildbcd. Vista did not boot.[/SIZE][/FONT]

[SIZE=2]I considered reloading Vista, but didn't since it would do a clean install.

Is it possible to recover from my stupid user trick and be able to boot to boot Ubuntu and Windows?

Thanks,
John
[/SIZE]

---

### Post by lemming465 on 2009-12-01
Ouch!  I don't see a way out of this that doesn't involve saving your data, scrubbing the disk, and reparitioning and reinstalling from scratch.  Sorry.

---

### Post by software mechanic on 2009-12-02
> **lemming465 said:**
> Ouch!  I don't see a way out of this that doesn't involve saving your data, scrubbing the disk, and reparitioning and reinstalling from scratch.  Sorry.
Further investigation shows that:

   [COLOR=black]From grub.cfg:[/COLOR]
  
  [COLOR=black]menuentry &#8220;Windows Vista (loader) (on /dev/sda2)&#8221; {[/COLOR]
  [COLOR=black]                        insmod ntfs[/COLOR]
  [COLOR=black]                        set root=(hd0.2)[/COLOR]
  [COLOR=black]                        search &#8211; no-floppy &#8211;fs-uuid &#8211;set 000000000000[/COLOR]
  [COLOR=black]                        chainloader +1[/COLOR]
  [COLOR=black]}[/COLOR]
[COLOR=black]
The UUID for the Windows partition in the grub.cfg file is set to all 0's. 
[/COLOR]  
  [COLOR=black]From sudo blkid -c /dev/null[/COLOR]
  [COLOR=black]/dev/sda1: UUID=&#8221;K6X762-pVgZ-HeVr-dicv-MEhh-tl9o-040Ddb&#8221; TYPE=&#8221;LVM2_member&#8221;[/COLOR]
  [COLOR=black]/dev/sda2/: LABEL=&#8221;SW_Preload&#8221; TYPE=&#8221;ntfs&#8221;[/COLOR]
  [COLOR=black]/dev/sad3: UUID=&#8221;01CA670375A83080&#8221; ; LABEL=&#8221;Warped&#8221; TYPE=&#8221;ntfs&#8221;[/COLOR]
  [COLOR=black]/dev/sda5/; UUID=&#8221;9ff1a425-8a35-4456-97fa-76db2d361d7d&#8221; TYPE=&#8221;ext4&#8221;[/COLOR]
  [COLOR=black]/dev/sda6/; UUID=&#8221;d7d7e73b-8114-42f1-a754-3d04d8c1d4c6&#8221; TYPE=&#8221;swap&#8221;[/COLOR]

It is seen that /dev/sda2 does not have a UUID. [COLOR=black]fstab has entries for /dev/sda5, /dev/sda6, and /dev/scd0[/COLOR].

It appears that the windows boot problem could be caused by the ntfs partition, /dev/sda2, not having a UUID. If so, how do I fix it?
[COLOR=black]
[/COLOR]

---

### Post by lemming465 on 2009-12-06
Try booting without the *search ...* line.  Particularly with a chainloader scenario, I don't see why it would be necessary.  (Booting from an external USB fob would be a different story; there it would tend to matter.)

---

