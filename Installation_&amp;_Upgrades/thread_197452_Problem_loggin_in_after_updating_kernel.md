---
title: "Problem loggin in after updating kernel"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by ltrinh on 2006-06-15
Hello All,

I'm a linux newbie and I need help.

My setup is dapper drake final on a dual core amd processor.

I was able to compile the 2.6.16 kernel cleanly with the ck12 patch without any problems. However, after rebooting I am not able to get past the login screen. The first time I logged in I got that message that my home directory is /home/loc but that it does not exist. So to check, I booted into failsafe mode and it turned out that it was gone. In fact the home directory was empty. I then reverted back to the old kernel and rebooted into my system just fine. I then copied the home directory /home/loc to a backup directory. Next, I edited menu.lst with gedit and uncommented the the compiled ck12 kernel and rebooted.

This time when I logged in I got this message:

"Users's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

Do I need to copy the directory with some kind of special permission other than just using Sudo? I have compiled 3 to 4 times now both with and without the patch and each time I have not been able to get past the login screen.

Any help would be greatly appreciated. I'd love to get this working.

---

### Post by ltrinh on 2006-06-15
Also here is some more info on my issue:

~/.xsession-errors file

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp

/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -x "/var/lib/gdm/:0.xservers" -h "" -l ":0" "loc"

/etc/gdm/Xsession: Beginning session setup...

could not set mode 0700 on private per-user gnome configuration directory '/home/loc/.gnome2_private/': Operation not permitted

------------------------------------------------------------------------

Here is my menu.lst printout from /boot/grub:

title Ubuntu, kernel 2.6.16-ck12
root (hd0,0)
kernel /boot/vmlinuz-2.6.16-ck12 root=/dev/sda1 ro quiet splash
initrd /boot/initrd.img-2.6.16-ck12
savedefault
boot

title Ubuntu, kernel 2.6.16-ck12 (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.16-ck12 root=/dev/sda1 ro quiet splash
initrd /boot/initrd.img-2.6.16-ck12
boot

---

### Post by bcj891 on 2007-01-16
I assumed you already have this problem solved. I had the same problem after I installed ubuntu over the FC6 partition. I found the answer to this problem in this thread in the general help forum:

[http://ubuntuforums.org/showthread.php?t=156964&highlight=could+mode+0700+on+private+per+gnome+configuration+directory](http://ubuntuforums.org/showthread.php?t=156964&highlight=could+mode+0700+on+private+per+gnome+configuration+directory)

---

