---
title: "Growing raid5 help"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by DKP on 2012-11-25
[FONT=Times New Roman, serif][SIZE=2]Hello[/SIZE][/FONT] [FONT=Times New Roman, serif][SIZE=2]I am trying to grow my raid5 from 5 HDD to 9 HDD are these the correct commands 

[/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=2]formant and partition one ext4 full disk partition on each of the new 2TB drive.[/SIZE][/FONT]

[FONT=Times New Roman, serif][SIZE=2]mdadm --add /dev/md0 /dev/sdX1 [/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=2]dev/sdX1[/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=2] dev/sdX1[/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=2] dev/sdX1[/SIZE][/FONT] 
 
 [FONT=Times New Roman, serif][SIZE=2]mdadm --grow /dev/md0 &#8211;raid-devices=9[/SIZE][/FONT]
 
 [FONT=Times New Roman, serif][SIZE=2]/etc/mdadm/mdadm.conf [/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=2]**:**[/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=2]edit num-devices=9[/SIZE][/FONT]
 
umount /dev/md0

 [FONT=Times New Roman, serif][SIZE=2]fsck.ext4 /dev/md0 [/SIZE][/FONT] 
  [FONT=Times New Roman, serif][SIZE=2]resize2fs /dev/md0[/SIZE][/FONT] 

 [FONT=Times New Roman, serif][SIZE=2][SIZE=2]A[/SIZE]ll the new HDD with add by a pci-e sata III card and I have data of my raid5 that I ne[SIZE=2]ed[/SIZE] to keep.[/SIZE][/FONT]
 
[FONT=Times New Roman, serif][SIZE=2]when I build my system I forgot to change the BIOS HDD host controller form IDE to AHCI if a go to the bios now and change it will ubuntu desktop 12.04  and raid5 be ok, I know that windows dose not boot after you do this, until you make a change in the REG.[/SIZE][/FONT]

---

