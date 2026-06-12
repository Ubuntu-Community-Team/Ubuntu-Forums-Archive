---
title: "restoring ubuntu groups"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by biddy on 2008-02-04
Hi,

I have just been reading the following post about restoring ubuntu groups

[http://ccollins.wordpress.com/2007/07/02/restore-default-ubuntu-groups/](http://ccollins.wordpress.com/2007/07/02/restore-default-ubuntu-groups/)

it refers to "So, to recover I had to use the Ubuntu live CD. I booted Ubuntu from the live CD and when I logged in I was able to mount my root partition (/). Once this was done, I could manually edit the /etc/group file and add myself to the admin group. A quick reboot later and I was able to use sudo and su again, and add myself to all the other groups I’d lost."

now i'm a complete tulip when it comes to linux but if I load the CD will it affect any of my files on my hard drive like my pictures etc, I have another disc in my pc which I use for backups but cannot mount it since i've been removed from all the groups.

any advice would be most aprreciated.

thanks

---

### Post by jrib on 2008-02-05
It will only affect what you tell it to affect.  In other words, it won't do anything unless you explicitly tell it to do it.

But, there are easier ways to resolve this problem without the CD.  Just choose "recovery mode" from the grub menu when you boot.  Issue the command ```
adduser YOUR_USERNAME_HERE admin
``` and reboot.  Then you can sudo again and add yourself to the groups normally.

---

### Post by biddy on 2008-02-07
HI Thanks for the reply, I have sorted this now, what I did was boot in recovery mode added a few lines of command that was offered by chris collins, check the link it proved very useful for me:

[http://ccollins.wordpress.com/2007/07/02/restore-default-ubuntu-groups/](http://ccollins.wordpress.com/2007/07/02/restore-default-ubuntu-groups/)

I added the following commands in recovery mode but of course used my own user name:

sudo usermod -G ccollins,adm,uucp,dialout,cdrom, \
floppy,audio,dip,video,plugdev,scanner,netdev, \
lpadmin,powerdev,admin ccollins

sudo usermod -g ccollins ccollins

thanks for your help/input once more & a big thanks for ccollins 

:guitar::guitar:

---

### Post by gosub3000 on 2008-07-15
Yeah, that [Chris Collins]("http://ccollins.wordpress.com/") is one helluva guy :)

Thanks for the tip Jason.  That's the thing with Linux, there's always an easier way.  I'll make a note in the comments for that blog post.

I'm glad my original post helped.  And don't worry about being a "Linux tulip", we all start out that way :)

-Chris

---

