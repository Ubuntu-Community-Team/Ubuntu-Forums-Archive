---
title: "How to install from CD"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by Bumpalot on 2012-04-29
Created CD from iso - Version 12.04 amd64, but it will not boot. Midsums match. Wish to run it first for testing, then install. Can't find help on KDE forums - hoping someone here can offer advice or suggest alternate help sources.

---

### Post by SeijiSensei on 2012-04-29
OK, I'll ask the obvious question first.  Does your machine have a 64-bit processor?  The 64-bit release that you downloaded won't install on a 32-bit machine.  You need to use [this one](http://cdimage.ubuntu.com/kubuntu/releases/precise/release/kubuntu-12.04-desktop-i386.iso) instead.

---

### Post by Bumpalot on 2012-04-29
Yes, have 64 processor.

---

### Post by oldos2er on 2012-04-29
Can you tell us your hardware specs? Also have you checked your BIOS to set it to boot from your CD/DVD drive?

---

### Post by Bumpalot on 2012-04-29
Bios set to boot from this CD drive.
On boot, cd disc active for about 2-3 mins. No screen activity except pulsating - cursor, then quits.
Nvidia GeForce GTX 550 Ti installed with NVIDIA-Linux-x86_64-295.40
Athlon Amd64, 8g Ram
Ubuntu 10.4  & KDE 12.4 Installed on ATA ST3500 500g drive
  	 	 	 	 	 	   Disk /dev/sdd: 500.1 GB, 500107862016 bytes  
 255 heads, 63 sectors/track, 60801 cylinders  
 Units = cylinders of 16065 * 512 = 8225280 bytes  
 Sector size (logical/physical): 512 bytes / 512 bytes  
 I/O size (minimum/optimal): 512 bytes / 512 bytes  
 Disk identifier: 0x000cc0f2  
     Device Boot      Start         End      Blocks   Id  System  
 /dev/sdd1            9962       11266    10482412+  83  Linux  
 /dev/sdd2               1        9960    80000001    5  Extended  
 /dev/sdd3           13880       21712    62918572+  83  Linux  
 /dev/sdd4           11268       13878    20972857+  83  Linux  
 /dev/sdd5               1        1245     9999360   83  Linux  
 /dev/sdd6            1246        3735    19998720   83  Linux  
 /dev/sdd7            3735        8715    39999488   83  Linux  
 /dev/sdd8            8715        9960     9999360   82  Linux swap / Solaris  
 

blkid

   	 	 	 	 	 	   
/dev/sda1: LABEL="Pagefile" UUID="06948A49948A3B67" TYPE="ntfs"  
 **/dev/sdd1: UUID="5ffdcaf8-d78e-4d32-b0bd-f4dbad346d86" TYPE="ext4" ** 
 **/dev/sdd3: UUID="366b0692-499d-4567-89f6-6922886acb1a" TYPE="ext4" ** 
 **/dev/sdd4: UUID="eacab7b3-b8c7-4e70-bfb6-aa40fc4835ba" TYPE="ext4" ** 
 **/dev/sdd5: UUID="cae46b8b-f7bc-48d4-84e0-9b72dc8e7825" TYPE="ext4" ** 
 **/dev/sdd6: UUID="48a78591-f70b-4cc3-8acd-d6440efef9ee" TYPE="ext4" ** 
 **/dev/sdd7: UUID="892dfa06-5998-4ce7-9b9f-52d8889b2b02" TYPE="ext4" ** 
 **/dev/sdd8: UUID="f6c76aa9-6132-4b43-aa21-c41edda87a7c" TYPE="swap" ** 
 /dev/sdb1: UUID="0EBC8528BC850B81" TYPE="ntfs"  
 /dev/sdf1: LABEL="USB" UUID="42E8AAB7E8AAA89D" TYPE="ntfs"

---

### Post by SeijiSensei on 2012-04-29
Try hitting F6 at the initial Kubuntu menu screen after the CD boots and pick "nomodeset".  Then hit enter to boot with that option enabled.  Any better?

---

### Post by Bumpalot on 2012-04-30
Thanks for the info, it worked.

---

