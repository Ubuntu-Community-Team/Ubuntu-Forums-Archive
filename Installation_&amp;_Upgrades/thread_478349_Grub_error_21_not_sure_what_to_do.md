---
title: "Grub error 21 not sure what to do"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by CDiablo on 2007-06-19
I looked at other posts and the web and could not find a solution. I recentely bought an old junker of a laptop and wanted to install ubuntu on it. The installation process through the actual laptop was taking hours and stalling (the laptop does work and has xp on it now) so I figured I could install ubuntu on this spare laptop drive I had and plug it in to the laptop. So I hook up the spare drive to my desktop (ubuntu/xp)through a usb adapter and install ubuntu. I remove the laptop drive from my desktop and my old ubuntu/xp setup gets the grub error 21 problem. Is there anything I can do to fix the grub manager?


NOTE:This problem has been solved thanks galego(his second method worked) and dannyboy

---

### Post by galego on 2007-06-19
when you installed Ubuntu did you specifically tell Grub where to install? if not it woudl have re-written itself to show the "new" drive you installed on the desktop to perform the install. i understand that you are trying to start ubuntu on your desktop but are getting the grub error in the process -- when the boot screen comes up highlight the Ubuntu Kernel you want to run then press "e" this will allow for edits to the path of your installation. if you installed origianlly to the first hard drive and first partition the line that says "root" should look like this:
root(hd0,0)
NOTE: if this worked make sure you edit your menu.lst file to show the correct numbers, because this  is only for this boot!

play around with those "zeros" and try different numbers if you do not know where the origianl install is. if that does not work then you will need to use your live cd and boot into it. once there do the following:

open a terminal

```
sudo grub
```

```
find /boot/grub/stage1
```

this will return where grub is in this manner (hdx,x) write this down

```
root(hdx,x)
```

where 'x' are the coresponding numbers from the previuos command -- ex. if it returned (hd1,1) you would enter root(hd1,1)

```
setup (hd0)
```

```
quit
```

this will install grub to the MBR and you are done.

good luck

---

### Post by dannyboy79 on 2007-06-19
> **CDiablo said:**
> I looked at other posts and the web and could not find a solution. I recentely bought an old junker of a laptop and wanted to install ubuntu on it. The installation process through the actual laptop was taking hours and stalling (the laptop does work and has xp on it now) so I figured I could install ubuntu on this spare laptop drive I had and plug it in to the laptop. So I hook up the spare drive to my desktop (ubuntu/xp)through a usb adapter and install ubuntu. I remove the laptop drive from my desktop and my old ubuntu/xp setup gets the grub error 21 problem. Is there anything I can do to fix the grub manager?

Error 21 means "Can not find disk". Try to install grub onto the master boot record of the laptop hard drive again. You need to boot to a live cd, chroot into your Ubuntu Installation that resides on your laptop hard drive, then install grub, and make sure that you install it to the correct master boot record hard drive. here's some good instructions for installing grub after chrooting into a ubuntu install from using a livecd.

[http://ubuntuforums.org/showthread.php?t=224351&highlight=chroot+to+install+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=chroot+to+install+grub)

read the code box where it talks about chroot and don't only read the very first suggestion.

---

