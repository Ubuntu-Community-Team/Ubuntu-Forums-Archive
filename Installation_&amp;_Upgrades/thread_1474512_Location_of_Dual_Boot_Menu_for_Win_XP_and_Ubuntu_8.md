---
title: "Location of Dual Boot Menu for Win XP and Ubuntu 8.10"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by novicee on 2010-05-06
**6 May 10**
  

 I have a dual boot system that was created when I installed Ubuntu 8.10 to a second hard disk drive (HDD2). I already had Win XP (Home Ed) installed on a first hard disk drive (HDD1).  The Ubuntu 8.10 install created a dual boot menu.  
 

 In order to fix a problem with Win XP's startup I  need to know if the record that holds the dual boot menu is on HDD1 or HDD2 and if that record is in the Master Boot Record (MBR) ?  
 

 Thanks,
 Novice

---

### Post by lechien73 on 2010-05-06
On your Ubuntu system, download boot_info_script from the following location:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Run this and check the RESULTS.txt file. It will tell you exactly where your bootloader is stored.

---

### Post by novicee on 2010-05-10
10 May 10

Thanks for the advice. I now have all the info I need.

I noticed that the command at  [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
namely:

Applications>Accessories>Terminal > bash ~/Desktop/boot_info_script*.sh

only worked when I omitted the ~/

---

### Post by novicee on 2010-05-24
**25 May 10**  
 

 As described in my post of 10 May I used the command at [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

namely:

Ubuntu 9.10 > Applications>Accessories>Terminal > bash Desktop/boot_info_script*.sh

 to obtain the RESULTS.TXT file.  The following info from that file puzzles me:  
 

 [B]=> Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2  
     in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst. 


  => Windows is installed in the MBR of /dev/sdb            [/B]  
 

I originally installed Win XP to the HDD that RESULTS.TXT refers to as &#8220;sda&#8221; and Ubuntu 9.10 was installed to "sdb".  
 

 1. When Ubuntu 9.10 was installed and created the dual boot menu did it move all or part of the MBR of sda to sdb?
 

 2. Does &#8220;boot drive #2&#8221; refer to sdb (i.e. is this just inconsistent terminology or something more)?
 

 Any help with these questions would be appreciated.

---

### Post by mikewhatever on 2010-05-24
The grub menu file is on the Ubuntu hdd, /dev/sdb, the exact location is probably /boot/grub/menu.lst.
Note, 9.10 and 8.10 have different versions of grub, and thus, different menu files. /boot/grub/menu.lst is the file you'd find in 8.10. I suggest you post the results of the boot scrip to clarify that.

---

### Post by novicee on 2010-05-25
**25a May 10**
 

 **1. Correction to my post of 25 May 10**
 

 In my post of 25 May 10 I said :
 

 **Start quote**
 

 I originally installed Win XP to the HDD that RESULTS.TXT refers to as “sda” and Ubuntu 9.10 was installed to "sdb". 

1. When Ubuntu 9.10 was installed and created the dual boot menu did it move all or part of the MBR of sda to sdb?

2. Does “boot drive #2” refer to sdb (i.e. is this just inconsistent terminology or something more)?


 **[B]End quote **[/B] 
 

 I made a mistake with the versions of Ubuntu above. The “9.10” in the above should have read “8.10”. That is, I first installed 8.10 and it originally created my dual boot menu. I by-passed 9.04 and next installed 9.10 which updated the dual boot menu that 8.10 had created.


 **2. RESULTS.TXT file attached**
 

 As suggested …

---

### Post by mikewhatever on 2010-05-27
> 1. When Ubuntu 9.10 was installed and created the dual boot menu did it move all or part of the MBR of sda to sdb?

No. Perhaps Windows was installed on sdb in the past, and the MBR remained.

> 2. Does “boot drive #2” refer to sdb (i.e. is this just inconsistent terminology or something more)?

Yes, it appears so. What is inconsistent about the terminology?

Anyway, hope that helps at all.

---

### Post by novicee on 2010-06-01
[FONT=Arial][SIZE=3]**2 Jun 10**[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]Thanks Mike for the answers.[/SIZE][/FONT]
 
 
[FONT=Arial][SIZE=3]**RECORD.TXT Terminology**[/SIZE][/FONT]
 
[FONT=Arial][SIZE=3]I was fairly sure that in RECORD.TXT (refer my post of 25a May 10) that "boot disk #2 was being used interchangeably with "sdb" but it raised questions like "why use different names for the same thing?" and "is it just a random choice or is there more to it?". [/SIZE][/FONT]
 
[SIZE=3][FONT=Arial]What I meant by "inconsistent" was this use of different names for the same thing. It is fine in poetry but in tech lit it unsettles me.[/FONT][/SIZE]

---

