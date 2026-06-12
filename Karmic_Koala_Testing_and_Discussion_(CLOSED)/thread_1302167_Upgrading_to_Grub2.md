---
title: "Upgrading to Grub2"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by humphreybc on 2009-10-26
Hey guys,

Firstly, what are the benefits of using grub2 over grub? What's changed, what's new, what should I know?

Secondly, if it turns out to beneficial for me to go to grub2, how do you upgrade to grub2 from grub? Currently I am on Karmic RC, upgraded from Jaunty, so I still have grub.

My boot menu is very simple, all I have is one OS: Karmic RC 64 bit, with two kernels, .31 and .28

Thanks
Benjamin

---

### Post by MasterNetra on 2009-10-26
> **humphreybc said:**
> Hey guys,

Firstly, what are the benefits of using grub2 over grub? What's changed, what's new, what should I know?

Secondly, if it turns out to beneficial for me to go to grub2, how do you upgrade to grub2 from grub? Currently I am on Karmic RC, upgraded from Jaunty, so I still have grub.

My boot menu is very simple, all I have is one OS: Karmic RC 64 bit, with two kernels, .31 and .28

Thanks
Benjamin

Fresh Install. Sorry.
Its prettier and faster I guess. Your system won't explode if you don't install it for 9.10 though :p

---

### Post by MasterNetra on 2009-10-26
**Accidental Double Post**

---

### Post by humphreybc on 2009-10-26
Are you sure you have to do a fresh install? I've heard that you can update it after an install, it's just a bit risky. I was thinking that since I only had one OS, i'm sure I could reconfigure a boot list via LiveCD if anything went wrong.

---

### Post by oldfred on 2009-10-27
this should do it:
[http://www.techenclave.com/guides-and-tutorials/grub-2-installation-92883.html](http://www.techenclave.com/guides-and-tutorials/grub-2-installation-92883.html)

```
sudo aptitude install GRUB2
sudo update-grub
```

Then to understand what is going on:
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Info, examples & links Oct 8,2009 
[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)
Revert from grub2 to legacy grub - not a tutorial! 
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

---

### Post by Elfy on 2009-10-27
This too [https://help.ubuntu.com/community/Grub2#Upgrading to GRUB 2](https://help.ubuntu.com/community/Grub2#Upgrading to GRUB 2)

The package to install appears to be grub-pc though not GRUB2

---

### Post by humphreybc on 2009-10-27
Hmm well that didn't go according to plan. I followed those instructions exactly and I'm getting an "Error 15" message from grub. I think it's the old grub, it looks like the old grub...

Anyway, I'm in LiveCD at the moment. I've chroot to my drive and ran these commands:

[CODE]
root@ubuntu:/# sudo dpkg-reconfigure grub2
sh: cannot create /dev/null: Permission denied
sh: cannot create /dev/null: Permission denied
Package `grub2' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: grub2 is not installed
root@ubuntu:/# update-grub
grub-probe: error: cannot find a device for /.

root@ubuntu:/# 
[/CODE

... but as you can see, they didn't work too good :(

Here's a thread with the _exact_ same problem i'm having: http://ubuntuforums.org/showthread.php?t=1293917

---

### Post by Elfy on 2009-10-27
Try following this, I know it works I have used it, however you will likely need to install the grub-pc package as I said earlier, grub2 isn't in the repos as far as I can tell - I would guess the earlier how to was older.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

You will likely need to install the grub-pc package as I said earlier, grub2 isn't in the repos as far as I can tell - I would guess the earlier how to was older.

---

### Post by dino99 on 2009-10-27
better to stay with grub: too much problems with grub2.

[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18](http://ubuntuforums.org/showpost.php?p=8071880&postcount=18)

---

