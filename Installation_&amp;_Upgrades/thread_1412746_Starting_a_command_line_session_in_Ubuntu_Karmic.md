---
title: "Starting a command line session in Ubuntu Karmic"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by lz1dsb on 2010-02-21
Hi guys. 
I just had a terrible lockup (my keyboard and mouse were completely locked) after inserting one USB flash drive while running Windows 7 as a virtual machine in Virtual Box (basically I wanted to check whether the virtual machine will detect the USB device and use it). So anyway, I've waited for a while to give a chance to the system to recover, but no, nothing really helped. So I had to hard reset my laptop to get back in control of the situation :) After that, as usual in such cases, I had an error message telling me that my /home partition couldn't be mounted. So in the recovery console I've mounted it and rebooted (I didn't performed file system check on that partition before mounting it though, which I regret). Usually in such cases after this step, I don't have any further issues. But now, each time I reboot I get and message like "Filesystem checks are in progress:" and it shows me that my /home partition is being checked. There's no indication of the progress though. I've left in for more than 3-4 minutes, but it doesn't shows signs of finishing. I'm able to boot to X by pushing the ESC button and skipping these checks, but after several reboots, I still see the above mentioned message. So basically my question is: how to get rid of it? I was thinking that if I could run fsck on my home partition I could solve this (and of course I need to umount the partition to perform the file system checks), but for this I need to be on a console with the ability to shut down the X manager (at least this is the way I've done it so far on other machines, but it could be another way...). On older versions of Ubuntu I was able to use Ctrl-Alt-F1 or other functional key to get from the X session to a console session (which also works on my brother's Slackware). But here in Karmic, this combination isn't working at all. So has something changed in Karmic in that respect? Any ideas on that issue?

Cheers,
Boyan

---

### Post by lz1dsb on 2010-02-24
All right, so this output is showing that I do have virtual sessions running:
bsotirov@boyan-laptop:~$ ps -eaf | grep tty
root      1453     1  0 16:04 tty4     00:00:00 /sbin/getty -8 38400 tty4
root      1458     1  0 16:04 tty5     00:00:00 /sbin/getty -8 38400 tty5
root      1476     1  0 16:04 tty2     00:00:00 /sbin/getty -8 38400 tty2
root      1477     1  0 16:04 tty3     00:00:00 /sbin/getty -8 38400 tty3
root      1479     1  0 16:04 tty6     00:00:00 /sbin/getty -8 38400 tty6
root      1678  1649  7 16:04 tty7     00:28:32 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-bP5iQY/database -nolisten tcp vt7
root      2670     1  0 16:04 tty1     00:00:00 /sbin/getty -8 38400 tty1
bsotirov 12018 11521  0 22:49 pts/0    00:00:00 grep --color=auto tty
bsotirov@boyan-laptop:~$ 

Than why the Ctrl+Alt+F1 or other F key isn't working? I was thinking that it might be that my functional keys have also additional functions (like showing battery status, shutting down the wireless interface etc.), so maybe they aren't recognized as functional keys... I'm using Dell Studio 1555 laptop. Does anybody has any idea?

Cheers,
Boyan

---

### Post by lz1dsb on 2010-02-25
All right, so here there's a problem with my Dell Studio for sure. I just run on this interesting article:
[http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html](http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html)
where the Ctrl+Alt+F1 is a valid key combination for accessing a virtual console line. Because there's an additional function on each functional key, I guess there's the problem. Does anybody out there with Dell Studio laptop has the same problem? ](*,)

Cheers, 
Boyan

---

### Post by lz1dsb on 2010-03-16
All right. I forgot about this thread. So I just read somewhere in the forums that I need to use the Fn button with the key combination in order to start a tty session, like Ctrl+Shift+F1+Fn for example. And it works. So I don't need to remap any button, plus I can still enjoy the multimedia buttons I have. To return to the desktop, Alt+Fn+F7. So I'm marking this as solved.

Regards,
Boyan

---

