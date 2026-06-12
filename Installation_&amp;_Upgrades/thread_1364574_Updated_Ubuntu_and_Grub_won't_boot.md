---
title: "Updated Ubuntu and Grub won't boot"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by LakatosI on 2009-12-26
So I recently installed Ubuntu 9.10 and after I did all the updates this morning and rebooted the computer for some reason when I want to boot Ubuntu (My main OS installed on this computer is Windows XP, and Ubuntu was installed ith Wubi), it takes me to the GRUB command line with absolutely no options besides hitting TAB to see the possible commands. Can somebody help me here? How do I boot into Ubuntu. Or should I reinstall Ubuntu?

---

### Post by LakatosI on 2009-12-26
AM i really the only one with this problem?

---

### Post by newbebrym on 2009-12-26
i have installed 7.10 and have the same problem,
my version stops after boot  up and freezes with 
a error code 2.whatever that is 
help someone!
 please
brym

---

### Post by nerdtron on 2009-12-26
(If someone is more knowledgeable please correct me)

So you installed Ubuntu using wubi? Then rebooted to open Ubuntu and then installed ALL possible updates?

Well if this is the case, it's really a problem. Wubi doesn't install GRUB. Instead i uses the Windlose XP's boot record. If you  installed updates, GRUB will be installed too and the boot process will be just a mess...
So try booting from your Windlose XP CD and enter the recovery console (just google it up on how to repair the mbr and ntldr using recovery console). Now you will be able to boot to XP and then install wubi again...
Sorry I'm not 100% sure but you can try it...

---

### Post by phillw on 2009-12-26
Ahh... Wubi ...

Try this after doing an update in Wubi

> **e: sh:grub > desperation** 			 			 			 		   		 		 		[SIZE=3][COLOR=DarkRed]WUBI Installs Only[/COLOR][/SIZE]

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
 		 		  		  		 		 			 				 				* 					 						Last edited by drs305; 4 Weeks Ago at 06:24 PM.. 					 					 				* 			


The thread is it from is here --> [http://www.uluga.ubuntuforums.org/showthread.php?t=1314064&page7](http://www.uluga.ubuntuforums.org/showthread.php?t=1314064&page7)  The previous pages are various trials of stuff, that page and the ones after it have how people got on. I'm not sure why updating is 'killing' Wubi.  At some point, if you're going to stay a while with ubuntu, I'd suggest dual-booting - you only need about 10GB of disk space to start off with.

Regards,

Phill.

---

