---
title: "line 317: sed: Permission denied"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by dave.com on 2008-10-20
I've edited /grub/menu.lst from LiveCD in Hardy using a few shortcuts:
```
~$sudo -i
/#mkdir /mnt/root 
/#mount -t ext3 /dev/sdc1 /mnt/root
/#mount -t ext3 /dev/sdc2 /mnt/root/boot
/#mount -t reiserfs /dev/sdc3 /mnt/root/home
/#mount -t proc none /mnt/root/proc
/#mount -o bind /dev /mnt/root/dev
/#sudo chroot /mnt/root /bin/bash

/# sudo nano -w /boot/grub/menu.lst
 <edit menu.lst>
/#update-grub
```

About 30% into the Ubuntu loading progress bar, Linux flips out and drops to a text screen while everything checks off [ok] then it hits an error:
"/etc/init.d/rc: 317: sed: Permission denied". As near as I can guess, at line 317 in /etc/init.d/rc a "Startup: scripts actions" init routine is concluded and this is where the Permissions error occurs. That narrows my guess down to the shell. Ubuntu LiveCD uses dash, and I invoked bash. 

Is this guess correct, and can I set the correct permissions for the init script? (Whichever one it is?)

I found this: ```
 # NOTE: The next line is critical for boot!
none			/proc		proc		defaults		0   0 
```
in an old Gentoo /sbin/rc script bug report... [bugzilla description]("http://bugs.gentoo.org/show_bug.cgi?id=21068") ntfs-config auto set the /etc/fstab line with a 'proc' entry where the example above shows 'none' at the beginning of the proc line, it could be anything.

I followed a lot of clues to get this answer... re-install Ubuntu (I have /home on its own partition).

---

### Post by amitkr on 2009-06-27
**/etc/init.d/rc: 2: sed: Permission denied** 			
 			 			 		   		 		 		I am not able to login to ubuntu 7.04. As the bootin starts and the bar starts filling, a black screen appears and it says - /etc/init.d/rc: 2: sed: Permission denied, almost 20 times. I tried to login from recovery mode, but failed. I don't have any clue now, how to recover my data. I got the ubuntu 7.04 live cd, somebody said run it, but it doesn't shows my data, so I am not installing it. Please, help me out.........plzzzzzzzzzzzz. My position is very bad and I despeately need my data. I don't have any backup of those. plzzzzzzzzzzzzzzzzz:sad:

---

### Post by swisstone198 on 2009-06-27
you can mount your partitions from the live CD. Just run 

sudo mount /dev/sda1 (or whatever partition it is on) /mnt

---

