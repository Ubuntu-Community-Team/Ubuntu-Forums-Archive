---
title: "Grub problem again"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2009-12-10
I have just run update manager after that my I can not start my computer it goes to grub, what can I do to get out of it then launch my desktop ?

---

### Post by phillw on 2009-12-10
> **hoboy said:**
> I have just run update manager after that my I can not start my computer it goes to grub, what can I do to get out of it then launch my desktop ?

Hi,

what version of ubuntu are you running ? is it an Wubi install ?
How did you install it ?
Regards,

Phill.

---

### Post by hoboy on 2009-12-10
> **phillw said:**
> Hi,

what version of ubuntu are you running ? is it an Wubi install ?
How did you install it ?
Regards,

Phill.

it is wubii install.
Kermic

---

### Post by phillw on 2009-12-10
Hi, try these instructions ..

>  				 				**Re: sh:grub > desperation** 			
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
 		                   		  		  		 		 			 				

There is an active thread on Wubi & Grub over here --> [http://ubuntuforums.org/showthread.php?t=1314064](http://ubuntuforums.org/showthread.php?t=1314064)

I don't know about Wubi, darkod has a little knowledge, u.b.u.n.t.u. seems to be the best one to ask for Wubi support.

Hope that solution by drs305 gets you up and running.

Regards,

Phill.

---

### Post by hoboy on 2009-12-11
ok I will reinstalled ubuntu again as I can not solve my grub problem :(
but this time I will install a differnet type of linux.. it seemed like this release of ubuntu is no better then windows

---

### Post by darkod on 2009-12-11
> **hoboy said:**
> ok I will reinstalled ubuntu again as I can not solve my grub problem :(
but this time I will install a differnet type of linux.. it seemed like this release of ubuntu is no better then windows

The instructions Phill gave you DO solve that problem. And besides, wubi is NOT full ubuntu. Install it side-by-side with windows, the way it's supposed to work, and then comment whether it's good or not.

---

### Post by bhuvi on 2009-12-11
i too installed the kernel updates and faced the same problem in karmic and i enabled pre-released updates in the repositories and thought that it was a problem due to applying updates after enabling pre-released updates.my karmic was also a wubi install.
i also have a karmic desktop which is direct install,i applied both the grub and the kernel updates and didnt face the same problem in my desktop

---

