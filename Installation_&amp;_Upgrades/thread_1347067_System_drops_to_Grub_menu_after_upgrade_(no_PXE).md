---
title: "System drops to Grub menu after upgrade (no PXE)"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by sav2005 on 2009-12-05
I just allowed Update Manager to install the latest security updates to the Linux kernel, header and xorg and clicked on restart system. After selecting Ubuntu from the system's boot manager I'm dropped into a Grub command line and don't have any idea what to do next.

I'm running Ubuntu 9.10 inside Windows Vista on a Lenovo R61 laptop using the Wubi setup. So far I've had no problems and I've used this system since 8.04(?).

---

### Post by phillw on 2009-12-05
> **sav2005 said:**
> I just allowed Update Manager to install the latest security updates to the Linux kernel, header and xorg and clicked on restart system. After selecting Ubuntu from the system's boot manager I'm dropped into a Grub command line and don't have any idea what to do next.

I'm running Ubuntu 9.10 inside Windows Vista on a Lenovo R61 laptop using the Wubi setup. So far I've had no problems and I've used this system since 8.04(?).


Ahhh... Wubi ....

> **Re: sh:grub > desperation** 			
 			 			 		   		 		 		[SIZE=3][COLOR=DarkRed]WUBI Installs Only[/COLOR][/SIZE]

I tried wubi when it first came out a few years ago but am no longer familiar with exactly how it works. There were enough problems recently that I rearranged my laptop's partitions so I could once again install wubi. Once I got wubi installed, I experimented until I could boot from a grub prompt. 

This is how I am able to manually boot from the Grub 2 prompt *in wubi*. My Windows partition is on [COLOR=DarkRed]**sda1**[/COLOR], which would be fairly standard.

Lines starting with a # are explanatory only. Do not type them.

 	Quote:
 	 	 		 			 				# Add the ntfs module
**[COLOR=Navy]insmod ntfs[/COLOR]**
# Set root (normally would be sda1, or hd0,1  Change as necessary
[B][COLOR=Navy]set root=(hd0,1)
loopback loop0 /ubuntu/disks/root.disk[/COLOR][/B]
# Yes, set root for a second time. I don't know why...
**[COLOR=Navy]set root=(loop0)[/COLOR]**
# Set the kernel. You can (and should) use Tab (twice) to complete entries such as the kernel when possible - type vml and then TAB twice and it will autocomplete to the point where there are two possibilities. Tab complete ensures the path/file names as typed exist. Additionally, if you suspect the new kernel is the problem, you might want to select an earlier one. vmlinuz.... should be a complete kernel entry such as "vmlinuz-2.6.31-15-generic-pae" *
**[COLOR=Navy]linux /boot/vmlinuz.... root=/dev/sda1  loop=/ubuntu/disks/root.disk ro[/COLOR]**
# Set the initrd image - complete or tab to get the full name  Example: "/boot/initrd.img-2.6.31-15-generic-pae"
[COLOR=Navy]**initrd /boot/initrd/initrd.img... **[/COLOR]
[B]# Boot.
[COLOR=Navy]boot[/COLOR][/B] 			 		 	 	 


* If this line scrolls off the screen as you type it, due to its length: To make it easier type "linux root=/dev/sda1 /ubuntu/disks/root.disk ro" and *then cursor back before "root=" to type/tab in the kernel name*.


If you successfully boot, run "sudo update-grub". Also inspect your /etc/default/grub file, which contains menu timeout and default kernel selections and determine if there is a problem with the menu.
 		                   		  		  		 		 			 				__________________
				[GRUB2]("https://help.ubuntu.com/community/Grub2") : [G2-Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602") [G2-Basics]("http://ubuntuforums.org/showthread.php?t=1195275")
[G2-Tasks]("http://ubuntuforums.org/showthread.php?t=1302743") [DiskSpace]("http://help.ubuntu.com/community/RecoverLostDiskSpace")  
[Expand /]("http://ubuntuforums.org/showthread.php?t=1219270") [SUM]("http://ubuntuforums.org/showthread.php?t=818177") 			
 		 		  		  		 		 			 				 				* 					 						Last edited by drs305; 1 Hour Ago at 06:24 PM*

It is a known working solution

Just pay attention to your initrd image

> # Set the initrd image - complete or tab to get the full name  Example: "/boot/initrd.img-2.6.31-15-generic-pae"
 

Regards,

Phill.

---

### Post by sav2005 on 2009-12-05
Unfortunately I'm stuck with Wubi because the corporate image on my laptop does not give me permissions to partition my drive.

---

### Post by sav2005 on 2009-12-05
After upgrading the system and being stuck at the Grub promp: ls /dev/sd* --> file not found

---

### Post by Oriol Gordó on 2009-12-05
I have the same problem here, also after the installation of the latest security updates. I have tried the solution of phillw, and all seem correct till the last part, the initrd /boot/... It keeps telling that the disk doesn't exists, and thats all.

---

### Post by Oriol Gordó on 2009-12-05
Okey, I have tried the solution of phillw again, and now works! How can I make the solution permanent?

Thank you, phillw, by the way!

---

### Post by phillw on 2009-12-05
> **Oriol Gordó said:**
> Okey, I have tried the solution of phillw again, and now works! How can I make the solution permanent?

Thank you, phillw, by the way!


If once it runs, you carry out the last command of sudo update-grub  Then it will be permanent.

don't thank me - thank drs for taking the time to set up his system for Wubi. He has written most of the community documents on grub2 for us all.

For others having problems, I can only suggest this thread --> [http://ubuntuforums.org/showthread.php?t=1314064&page=7](http://ubuntuforums.org/showthread.php?t=1314064&page=7)  

Page 7 was where drs 1st posted his solution - there are some other things to try from there on.

I'm really sorry, I don't know enough about Wubi to break it & try fixing it. - I think (and he may well hate me for this) that u.b.u.n.t.u. has a fair bit of experience on Wubi, if that thread can't help you - hopefully, he'll pop by on his travels and help those for whom it doesn't work. drs is on holiday, so anything broken specifically by the latest update may not be applicable any more.

That thread is probably the best place to head for upto date information.

Regards,

Phill.

---

### Post by sav2005 on 2009-12-05
Thanks PhilW - I mananged to boot 31-15-generic but when I tried your trick with the new kernel (31-16-generic) I got a "Wrong Magic Number" error.

I'll try the sudo update-grub trick and post the results here.

---

### Post by phillw on 2009-12-05
> **sav2005 said:**
> Thanks PhilW - I mananged to boot 31-15-generic but when I tried your trick with the new kernel (31-16-generic) I got a "Wrong Magic Number" error.

I'll try the sudo update-grub trick and post the results here.

As I said above, I don't know enough about Wubi - you'd stand a far better chance of help on the thread I posted above.

Phill.

---

