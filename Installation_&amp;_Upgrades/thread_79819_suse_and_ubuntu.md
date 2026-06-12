---
title: "suse and ubuntu"
date: 2005-10-20
forum: Installation &amp; Upgrades
---

### Post by sirtux42 on 2005-10-20
I just installed  ubuntu  on my dell...

 I use it as dual boot with windows/ suse93. I should say I added UB
 to make it  3 OS's ..  suse as my default

 UB is installed on a  external hard drive.The other 2 are installed on my internal drives.
  When I go to boot up. Grub gives a error (line 21 ) If I remember right..
 And nothing will boot up..   So..
 I have to  go and repair the grub mbr from my suse cd.
  Would it be cause  the external drive does not list as hda drive? 
OR does the grub set up on the ubuntu side mess up the  current grub from  suse ?

 Any tips or aid ?

---

### Post by jamesstansell on 2005-10-21
Grub gets its boot menu from /boot/grub/menu.lst and it sounds like you want your system to use the Suse version of that file.  I'm not sure what you might need to add there since I've never worked with an external drive.

Someone else with a setup closer to yours may be able to help.  But they will probably need more detailed information.  The ubuntu version you used and how it reported your drive during the installation would be good starting points.

-james.

---

### Post by sirtux42 on 2005-10-21
Ubuntu ver  5.04

 the external  HD  that ubuntu is installed on.Is listed within suse linux as  dev/sda1

---

### Post by sirtux42 on 2005-10-23
I repaird my grub through suse.
  seems linux lists  external  IDE harddrives as    sda's
  my bios does not list or  notice if it has scsi drives..
 I might just  say heck with it.. and  install the  external HD internally .
 And  try it that way.. see if  any grub issues pop up..
  
 my  grub list things as..
    suse  hd0,5    /dev/hda6, root=/dev/had6
  windoez  hda0,0  /dev/hda1
  Ubuntu  hda2,0  /dev/sda1

---

