---
title: "update failure in 10.10 has messed up ubuntu"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by chaozuper on 2011-04-08
Hi. Today, I installed Ubuntu 10.10 on a desktop computer, using a working live disk. While installing, i opted not to install updates. I restarted when installation was complete and ubuntu was working fine. But when I tried to do an update, it got stuck at

```
Running post-installation trigger man-db
```Then the screen went really dark and ubuntu completely froze up. i switched off the computer, switched it on again, and got this error:

```
uncompression error 

--System halted
```

I restarted again, and the GRUB menu appeared (i think that's what it's called). I selected Linux 2.6.35-22-generic (recovery) and got another error when the computer was "Loading initial ramdisk". I restarted AGAIN, this time selecting Linux 2.6.35-22-generic from the GRUB. But this just put the computer into a loop of rebooting and showing the GRUB menu. I tried Linux 2.6.35-22-generic again, this time getting this:

```
error: couldn't read file
```

This is a real problem for me, as i don't have very much experience with ubuntu. Sorry the post is so long. Thanks, chaozuper.

---

### Post by mörgæs on 2011-04-08
The screen turning dark grey is not an error. It only means that there is a heavy work load. When you see it again, just give the machine some time. 

Best is to install all updates as soon as possible, that is during installation.

---

### Post by chaozuper on 2011-04-09
well, i switched the computer back on this morning and ubuntu loaded up! the update manager told me i should do a partial upgrade, so i did that but the screen went completely black with only my cursor left whilst upgrading (not the same as before). i rebooted and now i'm getting this error again:

```
uncompression error

--System halted
```and also a new one:

```
error: reloc offset is out of the segment
```any more help would be greatly appreciated

EDIT: just tried reinstalling 10.10 using live disk and got this error

```
Input/output error during read on /dev/sda
```

---

### Post by mörgæs on 2011-04-09
Partial upgrades are dangerous:
[http://ubuntuforums.org/showthread.php?t=1641400](http://ubuntuforums.org/showthread.php?t=1641400)


The input/output error could (among other things) be a sign of a hard drive going bad. You could try wiping it completely with Killdisk and see if it still reports errors.

Killdisk has an ISO which burns to a CD just like Ubuntu.
[http://www.killdisk.com/](http://www.killdisk.com/)

---

### Post by chaozuper on 2011-04-09
so i could just run killdisk on the computer, then try installing ubuntu? or would i have to do extra stuff to get it to work?

---

### Post by mörgæs on 2011-04-09
Yes, just run Killdisk and install. Since the machine seems to have some trouble with 10.10, I would try 10.04.2, which is supported two years from now.

---

### Post by chaozuper on 2011-04-09
ok, i tried killdisk, but it just stays at 0%. i'm using all the default options.

EDIT: could it possibly be that my hard drive has failed?

---

### Post by mörgæs on 2011-04-10
Yes, it sounds like a hard drive going bad. I assume that you have not changed cable connections and the like.

There are many ideas on the web about how to bring a dying hard drive back to life, but it is not worth the while. A new (or used) hard drive is so cheap that there is no point in messing with the old one.

---

