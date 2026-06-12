---
title: "Update failed for linux-image-2.6.31-20"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by budman21901 on 2010-03-26
Problem is i am having trouble updating 2.6.31-20.  It keeps failing, and i can't figure it out.  The system runs excellent other then this problem.  All help will be much appreciated.     

**Kernel Info:**  
[PHP]Linux budman-laptop 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64 GNU/Linux[/PHP]

**Error Information: **
[PHP]The following packages will be upgraded:
  linux-image-2.6.31-20-generic 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/28.9MB of archives. After unpacking 4,096B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 178183 files and directories currently installed.)
Preparing to replace linux-image-2.6.31-20-generic 2.6.31-20.57 (using .../linux-image-2.6.31-20-generic_2.6.31-20.58_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.31-20-generic ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.31-20-generic_2.6.31-20.58_amd64.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.31-20-generic_2.6.31-20.58_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done[/PHP]

---

### Post by Chame_Wizard on 2010-03-27
```
sudo aptitude safe-upgrade
```

See if it's work.

---

### Post by budman21901 on 2010-03-28
> **Chame_Wizard said:**
> ```
sudo aptitude safe-upgrade
```

See if it's work.

No, the same thing happened.

---

### Post by draperdt on 2010-03-28
I have the same issue. Can we revert to an older version of the kernel?  Man I hate upgrades.

---

### Post by vishnumrao on 2010-03-30
I too have the same problem, and my system won't boot up with any of the older kernels on Lucid beta 1. Any solutions anyone?

---

### Post by krainey2106 on 2010-03-30
I saw this message after I posted my version of the problem:

 				[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG] 				**Re: Error message when doing updates...** 			
 			 			 		   		 		 		I have had the same problem, but the ¨$sudo dpkg --configure -a¨ does not solve the problem. In the terminal I get an endless stream of:

Found linux image: /boot/vmlinuz-2.6.31-15generic-pae

Is there any way I can fix this short of reinstalling 9.10?

I tried 
sudo aptitude safe-upgradeI still get the endless stream of Found  . . . .

Thanks to all for all suggestions!!

---

