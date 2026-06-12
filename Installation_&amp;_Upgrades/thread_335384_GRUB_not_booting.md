---
title: "GRUB not booting"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by arnaldo on 2007-01-10
I had a functioning dual-boot edgy installation on my notebook.  Then I had to reinstall XP.  I knew it would hose the MBR, but never mind, I can always reinstall grub.
So I did.  After the windows install, I rebooted from an Ubuntu CD, and reinstalled grub, marking the linux root partition as the boot one.
Now, when turning on the computer, it does not boot; the cursor stays there, with no messages at all.  I think it reads the MBR, but doesn't proceed afterwards.

The reason for thinking that is that if I mark two partitions as bootable, then the message "Invalid partition table" appears on the screen.

Now, some more details:

There is only one disk. hda1 is windows, hda2 is swap, hda3 is the linux root (ext3) and hda4 is lvm managed.  /boot is on hda3.  After booting from CD, I can mount the linux partitions correctly. /boot/grub/menu.lst is readable, and looks correct.

On grub I executed:
root (hd0,2)
setup (hd0)
quit

The messages printed by grub indicated a successful installation.  However, the problem I mentioned persists after repeated attempts.

Any suggestion?

---

### Post by bichopro on 2007-01-10
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by arnaldo on 2007-01-11
Dead on!
Solved my problem on the first try; just wish I could recover the time I wasted before posting the question.
Thanks.

---

### Post by ububaba on 2007-01-12
I have a totally different, yet extremely irritating situation. After the login, I get a black screen
which asks me to login at the root but it disppears quickly. Then the login screen reappears 
requesting login. Any one knows how can I get out of this loop.

I found nothing peculiar in **/boot/grub/menu.lst**. Perhaps, I am missing it or the fault lies 
somewhere else.:mad:

---

### Post by arnaldo on 2007-01-15
As the login screen does appear, the problem is not grub.  It looks like a problem in starting X.
Try to login into the second console; Alt+F2 or Alt+Ctrl+F2 will usually land you there, with a pristine login screen.  Check, using ps, whether gdm is running; actually, try   pgrep X   a few times.  If the number keeps changing, it is a safe bet that  gdm is looping on starting X.  Have a look at /var/log/Xorg.0.log .  That may point you to an error in /etc/X11/xorg.conf.

---

### Post by ububaba on 2007-01-15
Thanks I will try.:)

---

### Post by ububaba on 2007-01-15
> **arnaldo said:**
> As the login screen does appear, the problem is not grub.  It looks like a problem in starting X.
Try to login into the second console; Alt+F2 or Alt+Ctrl+F2 will usually land you there, with a pristine login screen.  Check, using ps, whether gdm is running; actually, try   pgrep X   a few times.  If the number keeps changing, it is a safe bet that  gdm is looping on starting X.  Have a look at /var/log/Xorg.0.log .  That may point you to an error in /etc/X11/xorg.conf.

I tried but I get this flag[HTML]GDM could not write your authorisation file. 
This could mean that you are out of disk space or that your home directory 
could not be opened for writing. In any case, it is not possible to log in. 
Please contact your system administrator.[/HTML]
With my untrained eye, I could not find anything out of the ordinary in **/var/log/Xorg.0.log** 
Would you know what sort of stuff one should try to locate there?

---

### Post by arnaldo on 2007-01-15
You did find an error message pertaining to gdm!  Follow up on that, checking whether all relevant filesystems are mounted rw, and have some free space.  At least, /var, /tmp and /home should be on rw mounts.
Is gdm being run by root?  

As for the Xorg log, I don't know for sure what to look for, but I remember that its messages are quite informative, with telltale tags like "missing" or "error".

---

### Post by ububaba on 2007-01-15
> **arnaldo said:**
> You did find an error message pertaining to gdm!  Follow up on that, checking whether all relevant filesystems are mounted rw, and have some free space.  At least, /var, /tmp and /home should be on rw mounts.
Is gdm being run by root?  

As for the Xorg log, I don't know for sure what to look for, but I remember that its messages are quite informative, with telltale tags like "missing" or "error".

The error is supposed to be that **/etc/X11/xserver/SecurityPolicy** cannot be opened by the 
upstart process. Besides [COLOR="Red"]file system check fails[/COLOR] as well, which ought to be repaired [COLOR="Red"]manually[/COLOR].

---

