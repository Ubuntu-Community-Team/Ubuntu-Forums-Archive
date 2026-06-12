---
title: "Problem with install of ubuntu 9.10"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by Iwillsurvive on 2010-10-02
I was trying to install ubuntu 9.10 as a dual boot system with windows and I recieved this error message:
 
 
 
The Grub package failed to install into /target/. Without the Grub boot loader, the installed system will not boot 
 
 
 
 
This Error comes up after 94% of the install.
 
I also cannot seem to get the side by side install option to work (sometimes this option appears sometimes it does not)
 
I am not sure but I beleive seome of the install files have been placed on the hard drive because I only get the option now to install on the hard drive and totally wipe clean or the emptiest hard drive. So how would I get the possible Ubuntu install off the Hard drive.
 
I have used this CD to Install before it has no scratches therefore should work.
 
 
Also If I have Win Xp on a Raid 0 will the Ubuntu 9.10 install ?

---

### Post by ronparent on 2010-10-03
> The Grub package failed to install into /target/. Without the Grub boot loader, the installed system will not boot 
This message will usually appears when you are trying to install the grub 2 boot loader on one disk of a raid set. That would also be consistent with the error at 94% install. At the 94% point incidently all of your files have been written somewhere. If installed to a raid 0 the grub boot loader has to be placed on the /dev/mapper device that represents the raid as a whole. By default, Ubuntu tries to place the grub boot loader usually on /dev/sda. This is incorrect, of course, resulting in the error you saw at the end of the install. If there are no other errors this is fixable by reinstalling grub (see: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2).

Although you don't say it is implied, and, yes, it is possible to install side by side with Win xp on a raid 0. I wouldn't suggest you try anything else until you have run the Boot Info script from this site following and posted the results on this post: [http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055). Although I suspect a simple grub 2 reinstall will fix your boot it would be best to see what you are working with before you try.

---

### Post by Iwillsurvive on 2010-10-05
I will do and the information you have given has been Great

---

### Post by ronparent on 2010-10-05
Good. I'll keep an eye on this thread.

---

### Post by Iwillsurvive on 2010-10-07
I tried this methoad but got no response 
sudo fdisk -l
when I restart the system goes black and never restarts
so  I can go to the next part which are these
part 7. 
      Refresh the GRUB 2 menu with sudo update-grub


I put screenshot of partitions in . could they be explained

---

