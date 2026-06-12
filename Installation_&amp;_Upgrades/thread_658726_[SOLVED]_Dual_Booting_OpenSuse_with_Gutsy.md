---
title: "[SOLVED] Dual Booting OpenSuse with Gutsy"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by burning_man13 on 2008-01-04
Hey guys,
I have had Ubuntu running for quite awhile now... and I have just recently downloaded OpenSuse because I've heard it's pretty good, and I thought I'd give it a try. Here's the thing... I've read other forums, and people say to reinstall Gutsy after installing OpenSuse... I don't really want to reinstall Gutsy, because I have so many programs that would take me a really long time to get all back... so I was wondering what the easiest way to dual boot OpenSuse, with Ubuntu already loaded, will I have to create a smaller partition, and if so... How would I go about doing that??? Somebody please help me, I really don't want to mess this up... 
Thanks in advance...

---

### Post by PmDematagoda on 2008-01-04
I do not think it is really necessary to reinstall Ubuntu after installing OpenSUSE, all you will need to do is configure OpenSUSE's boot-loader to allow you to boot Ubuntu as well. You could also use [SuperGRUB]("http://supergrub.forjamari.linex.org/?section=download") to allow you to switch from OpenSUSE's boot-loader to Ubuntu's boot-loader from where you could configure Ubuntu's boot-loader to boot OpenSUSE as well.

---

### Post by burning_man13 on 2008-01-05
I tried Supergrub first, and from everything I read on it, it seemed like it was just to fix broken partitions... and when I was in OpenSuse, I didn't see anything to configure the boot loader like Ubuntu has... if you, or somebody else (I'm also going through OpenSuse's forums) could help me find the place to configure the boot options, that would be much appreciated... I'm sorry, but I'm a n00b at dual booting, so I'm extremely grateful for all help...

---

### Post by PmDematagoda on 2008-01-05
SuperGRUB is not a partition recovery tool, it is meant to fix or modify the MBR.

Ok, now on OpenSUSE, post the result of:-
```
cat /boot/grub/menu.lst
```
and
```
sudo fdisk -l
```

---

### Post by burning_man13 on 2008-01-07
Hey, I have successfully completed dual booting... so thanks for your help!!!

---

