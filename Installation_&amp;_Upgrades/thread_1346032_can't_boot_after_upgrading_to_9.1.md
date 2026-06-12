---
title: "can't boot after upgrading to 9.1"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by bisc19 on 2009-12-04
I just upgraded from 9.04 to 9.1 and when it tries to boot up, I get this message:
 
init: ureadahead main process (2737) terminated with status 5
mountall:/proc: unable to mount: Device or resource busy
mountall:/proc/self/mountinfo: No such file or directory
mountall: root filesystem isn't mounted
init: mountall main process (2738 ) terminated with status 1
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
Give root password for maintenance
(or type Control-D to continue):
 
If it's any help, my grub is on a different drive to this new 9.1 installation but that has never mattered for upgrades before.
 
Any ideas?

---

### Post by HighInBC on 2009-12-29
I just upgraded Ubuntu Server Jaunty to Karmic and now I cannot boot.

I am having the same issue described above:

```

Begin: Running /scripts/init-bottom ...                                                                                 
Done.                                                                                                                   
init: ureadahead main process (2166) terminated with status 5                                                           
mountall:/proc: unable to mount: Device or resource busy                                                                
mountall:/proc/self/mountinfo: No such file or directory                                                                
mountall: root filesystem isn't mounted                                                                                 
init: mountall main process (2167) terminated with status 1                                                             
General error mounting filesystems.                                                                                     
A maintenance shell will now be started.                                                                                
CONTROL-D will terminate this shell and re-try.                                                                         
Give root password for maintenance                                                                                      
(or type Control-D to continue):                                         
```

This is a remote server and it does not have a root password so I am not sure how to get into it.

Can someone please tell me how to rescue this system, I am running a few websites on this which are now down and I don't fancy recovering from backup on a fresh server.

**Update:**

I found a way to get in using my hosting providers rescue mode which allows me to boot from a rescue image and mount the machine's hard drives. I still do not know how to fix this issue now that I am in. I have read a few bug reports on this but no solution is provided.

---

### Post by y.hahn on 2010-02-01
I got the same error but successfully rescued the system.

I found out that the problem was in the grub menu file (/boot/grub/menu.lst). Somehow, the file was outdated and did not list the kernels I have in /boot.

So, I simply edited the menu.lst file:

For example, if you have only old kernels in your menu.lst:

[FONT="Courier New"]title           Ubuntu 9.4, kernel 2.6.22-15-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-15-server root=UUID=### ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-server[/FONT]

But you have 2.6.31-17-generic kernel in your /boot for example.

Simply replace above lines to:

[FONT="Courier New"]title           Ubuntu 9.10, kernel 2.6.31-17-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.31-17-generic root=UUID=### ro quiet splash
initrd          /boot/initrd.img-2.6.31-17-generic[/FONT]

(Actually, you don't need to edit the 'title' line)
And then, reboot the system.

When your system is up, run "sudo update-grub" to update the menu.lst

---

### Post by HighInBC on 2010-02-01
Thank you very much for the solution to this problem. I tore down the old system and rebuild it from backup a few weeks back but perhaps this information will save other people the trouble.

---

### Post by Freak Of Nature on 2010-02-05
> **y.hahn said:**
> I got the same error but successfully rescued the system.

I found out that the problem was in the grub menu file (/boot/grub/menu.lst). Somehow, the file was outdated and did not list the kernels I have in /boot.

So, I simply edited the menu.lst file:

For example, if you have only old kernels in your menu.lst:

[FONT="Courier New"]title           Ubuntu 9.4, kernel 2.6.22-15-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-15-server root=UUID=### ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-server[/FONT]

But you have 2.6.31-17-generic kernel in your /boot for example.

Simply replace above lines to:

[FONT="Courier New"]title           Ubuntu 9.10, kernel 2.6.31-17-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.31-17-generic root=UUID=### ro quiet splash
initrd          /boot/initrd.img-2.6.31-17-generic[/FONT]

(Actually, you don't need to edit the 'title' line)
And then, reboot the system.

When your system is up, run "sudo update-grub" to update the menu.lst
Wow Y.Hahn,

That worked a treat.  For Noobs like me we sure appreciate an concise easy to follow fix.

1000 thanks,
Kind regards,
Noel

---

