---
title: "HEEELP!!! Something's wrong with my kernel!"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by titsmcgee1230 on 2011-02-24
Ok so today when i went to turn on my computer it came up with this message...
 
Loading please wait...
mknod: File exists
19+0 records in
19+0 records out
kinit: name_to_dev_t (/dev/disk/by-uuid/84effa58-ee21-420d-9c45-233a552636af) = dev(8,2)
kinit: trying to resume from /dev/disk/by-uuid/84effa58-ee21-420d-9c45-233a552636af)
kinit: no resume imgae, doing normal boot....
mount: mounting /dev/disk/bu-uuid/ac67818a-4afa-4a75-b78a-b53758624b2b on /root failed:invalid argument
mount: mounting /root/dev on /dev/.static/dev failed: no such file or directory
mount: mounting /sys on root/sys failed: no such file or directory
Taget file system doesn't have /sbin/init
no init found, Try passing init=bootarg
 
Busybox v1.10.2 (ubuntu 1:1.10.2-1 ubuntu7) built in shell (ash) Enter 'help' for a list of built in commands
 
(initramfs)
 
idk wat this means.... 
 
Can anyone help me fix this? Any help would be greatly appreciated. Thanks!

---

### Post by dino99 on 2011-02-24
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by titsmcgee1230 on 2011-02-24
??

---

### Post by sanderd17 on 2011-02-24
I assume you want to resque your installation and not do a complete reinstall?

Can you give us the output of the bootscript inside CODE tags? [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by dino99 on 2011-02-24
> **titsmcgee1230 said:**
> ??

you have to follow , step by step, this little help to understand how to install ubuntu.

---

### Post by titsmcgee1230 on 2011-02-24
I didnt really have any files that i really need to keep. but can i fix it with the 9.10 LiveCD? im running 10.04.

---

