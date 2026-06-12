---
title: "How to upgrade grub2 EFI boot loader"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by etnba on 2011-03-31
Hi all,
 
I installed UEFI Ubuntu 10.10. Its grub2 version is 1.98. I want to upgrade it to 1.99.
 
I try to use 'grub-install' and 'grub-setup' commands but I faild to upgrade the grub2.
 
Can somebody help me? 
 
Thanks
 
And, when I add my ram to 4G, the system hangs and displays 
'Not syncing: VFS: Unable to mount root fs on unknow-block(1,0)'
 
Is this a known issue?
 
Thanks

---

### Post by etnba on 2011-04-01
Hi all,
 
I reference 

[https://help.ubuntu.com/community/MactelSupportTeam/EFI-Boot-Mactel](https://help.ubuntu.com/community/MactelSupportTeam/EFI-Boot-Mactel)
 
to update GRUB2.
 
After typping 'svn co svn://svn.sv.gnu.org/grub/trunk/grub2', it comes error message
 
svn: URL 'svn://svn.sv.gnu.org/grub/trunk/grub2' doesn't exist
 
Does somebody know the correct svn location?
 
 
I also try to use a live CD Ubuntu 11.4 to upgrade GRUB2 from 1.98 ro 1.99rc.
 
I reference 

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
 
to do this.
 
And I still faild. :(
 
Has anyone been done this?
 
Thanks a lot.

---

### Post by etnba on 2011-04-06
Hi all,
 
  Finally, I upgrade successfully. Here is my reference:
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)
 
After I copy *.mod to grub folder, I change the folder name to Ubunto.
 
Hope this can help someone.

---

