---
title: "Upgraded to 9.10 ... mounting error"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by istock1 on 2009-11-13
All,

I recently upgraded from 9.04 to 9.10, but after shutting down my system will not come back up. I first got this error:

"One or more of the mounts listed in /etc/fstab cannot yet be mounted"

followed by:

"mountall: Cancelled
init: mountall main process terminated with status 1
General error mounting file systems"

So I did some research, and ended up checking my menu.lst file. It looks like Update Manager didn't update the list, so the first entry was for 9.04

"
title        Ubuntu 9.04, kernel 2.6.28-16-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=e358b2be-5a5d-4291-95b9-f5192fe0517b ro vga=769 quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet
"

I attempted to update this manually, but even though I have the 2.5.31.14 vmlinuz file, I am missing the initrd.img file. Can I just get a copy of someone else's initrd.img file? Would that work? I'm not sure where to go from here ...

Thanks for any help.

---

### Post by istock1 on 2009-11-14
Haven't figured it out yet ... any suggestions? Are all the initrd.img files the same for a given kernel?

---

### Post by istock1 on 2009-11-16
Bump ... I am getting tired of using Vista people ... please help if you can :(

---

### Post by Kjeldgaard on 2009-11-20
Have you found a solution to this problem? If not take a look at this post, and if you understand it can you explain it to me? [http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8304687&postcount=8](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8304687&postcount=8)

---

