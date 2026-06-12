---
title: "Installing XP after Ubuntu"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by blazemore on 2008-11-05
We all know how easy it is to install Ubuntu on a Windows-only system (Automatic resize, format etc).

But how easy can it be done the other way?
I understand the ext3 resize operation takes a long time.
And the Windows XP bootloader would surely eat GRUB?

Can anyone give me any tips?
I want a Windows XP install for gaming, and I have the proper media.

---

### Post by crate2k5 on 2008-11-05
if you're using a desktop I'd suggest buying another hdd and install it on that one then reconfigure grub. Yeah, windows loader will eat grub. As far as the same hdd, that's a new one to me.


Let me know how this turns out.

---

### Post by ronnielsen1 on 2008-11-05
It's possible. I would use a live cd to resize the partitions and then reinstall grub after you install XP. I wouldn't format the new partition. Let XP do that - just create a new unformatted partition.

---

### Post by crate2k5 on 2008-11-05
My question is does it do the "install inside windows" thing or does it actually create partitions out of empty space?

---

### Post by haylun98 on 2008-11-05
It isn't difficult to do providing you're comfortable or a bit adventurous in reinstalling GRUB after Windows overwritten GRUB. This follow site (Illustrated Dual Boot Site)I found most usful with tones of informations about dual booting, MBR, Boot Loaders including GRUB (configure/reinstall), etc

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

They really done a good job for all those who are unwilling / scare to give up Windows for the time being, including me.

---

### Post by m_duck on 2008-11-05
A couple more links...
[If you're using XP]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm")
[And for vista...]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm")

---

### Post by blazemore on 2008-11-05
So just to make it clear:
I should use the LiveCD to resize my ext3 partition, leaving the rest as unformatted space
I should install Windows XP, letting it format the space as NTFS
I should then look into reinstalling GRUB (Which I know to be quite straightforward)

---

### Post by haylun98 on 2008-11-05
I think you need to at least prepare anempty unallocated space. Since Microsoft is not exactly linux friendly, the Windows installer will not recognise anythings unless they are empty/FAT,FAT32/NTFS partitions. Providing you have an empty space or a partition you can delete that installing Windows should be easy. You still need to reinstall GRUB because Windows installer will replace it with its own boot loader.

---

### Post by ronnielsen1 on 2008-11-06
> So just to make it clear:
I should use the LiveCD to resize my ext3 partition, leaving the rest as unformatted space
I should install Windows XP, letting it format the space as NTFS
I should then look into reinstalling GRUB (Which I know to be quite straightforward)
 		                   		  		  		 		 			 				__________________

yes

---

### Post by blazemore on 2008-11-07
Okay I installed but it gave my local disk the drive letter K, which is causing all kinds of problems

---

### Post by ronnielsen1 on 2008-11-07
> Okay I installed but it gave my local disk the drive letter K, which is causing all kinds of problems 	

> 1. Open the **Control Panel**
2. Select Classic View (if not already setup that way)
3. Click **Administrative Tools **Folder
4. Double-click the **Computer Management **icon
5. Computer Management window will open.  Click **storage** in the left page.
6. Double-click **Disk Management**
7. Right-click the drive you want to change
8. Select **Change Drive Letter and Paths**
9. Click the **Change** Button
10. Select the drive letter to which you want to assign it
11. Note the warning and agree if you accept the risks
12. Close out the disk management

[http://www.tech-recipes.com/rx/506/vista_xp_reassign_change_drive_letters/](http://www.tech-recipes.com/rx/506/vista_xp_reassign_change_drive_letters/)

---

### Post by yibe on 2008-11-07
Hey guys I had windows xp on C drive and ubuntu on F drive. But After I re installed windows on the C drive I couldnt find the ubuntu. And I installed DrCom but it keeps saying configuration file error at line 3, device cant get mac address and couldnt connect to the internet. 
please can anyone help me out?

---

### Post by ronnielsen1 on 2008-11-07
> Hey guys I had windows xp on C drive and ubuntu on F drive. But After I re installed windows on the C drive I couldnt find the ubuntu.
You would have to reinstall grub
> [INDENT]sudo grub
 > root (hd0,0)
 > setup (hd0)
 > exit
 [/INDENT]
You would have to substitite where your ubuntu partition is. hd0 is hard drive 1 - hd1 is hard drive 2 

The ,0 is the partition - ,0 is partition 1 - ,1 is partition 2 etc

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

> And I installed DrCom but it keeps saying configuration file error at line 3, device cant get mac address and couldnt connect to the internet.
not sure about this

---

### Post by yibe on 2008-11-08
Thanks Ronnielsen. But where am i gonna write those commands? I couldnt even loged on to ubuntu system. when my system boots it directly log on to windows.

---

### Post by ronnielsen1 on 2008-11-08
> Thanks Ronnielsen. But where am i gonna write those commands? I couldnt even loged on to ubuntu system. when my system boots it directly log on to windows.

Use a live cd to boot from

Click on Applications > Accessories > Terminal

Then follow the previous post. It will work

---

