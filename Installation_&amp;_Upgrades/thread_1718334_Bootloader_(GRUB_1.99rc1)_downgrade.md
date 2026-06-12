---
title: "Bootloader (GRUB 1.99rc1) downgrade"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by JH6 on 2011-03-31
Hello everyone.

I'm trying to make a bootable USB drive with one partition for data storage, one extended patition which holds a full ubuntu install and a third extended partition for a persistend backtrack linux on it.
This went just fine, but the problem I have is in my bootloader.
I installed Ubuntu 11.04 (natty) because I need the new kernel to use ubuntu on my laptop (other kernels don't work because of the hybrid graphiccard).
Ubuntu natty uses grub 1.99rc1. Ubuntu loads just fine on my laptop but the boatloader wont display properly, on some computers it will give an out of range error, on my laptop it doesn't display at all. Ubuntu boots fine though, but I would like to be able to select Backtrack also. The older version of grub 1.98 works just fine (tested it with an opensuse installation on een usb drive). 
So I would like to "downgrade" my grub version to an older one. I would prefer one which still uses the menu.lst (which grub 1.99 doesn't) becuase I now how to add other boot options to that (so I can add backtrack easily).

Could anyone please explain to me how to remove grub 1.99rc1 and install an older version (which uses menu.lst). I tried some different things but I can't succeed, also tried searching the forum but could find anything. 

So please explain this to me or point me to a good forum post or website which explains how to do it.

Thanks a lot.

~JH6

---

### Post by malangaman on 2011-03-31
Did you try ? :
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
or
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
or
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
or
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by JH6 on 2011-03-31
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto) 
Not yet. will read it and see if it helps.


[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Yes tried it, read it, couldn't solve it with that. Maybe doing something wrong dough. 

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
did parts of it. Some things where difficult to understand.

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
Not yet. Will also read it and see if it helps.

Thank you so far.
Will come back if those links doesn't help me

---

