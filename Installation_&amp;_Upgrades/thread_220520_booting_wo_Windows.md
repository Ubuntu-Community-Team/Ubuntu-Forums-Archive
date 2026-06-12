---
title: "booting w/o Windows"
date: 2006-07-21
forum: Installation &amp; Upgrades
---

### Post by Donald F. Robertson on 2006-07-21
I've installed Umbutu-6.06 with root at /dev/hda2 ext3 and Swap at /dev/hda1 without Windows.  When I try to re-boot my machine, it does not recognize the hard drive.  I must have overwritten the boot commands.  Is there any way to recover?

I can boot into the CD.

Thanks!

-- Donald

---

### Post by Jagot on 2006-07-21
You could try and restore GRUB - it may have been overwritten somehow:

[http://ubuntuos.com/2006/03/howto-restore-grub](http://ubuntuos.com/2006/03/howto-restore-grub)

---

### Post by Donald F. Robertson on 2006-07-21
I could not make this work.  The Umbuntu-6.06 partition and installation programs do not appear to have these features.  I re-installed from scratch with the same result -- it won't boot from the hard drive.

Thanks!

-- Donald

---

### Post by Donald F. Robertson on 2006-07-21
I don't know what I did, but this time I'm in.  Thanks again!

-- Donald

---

### Post by Herman on 2006-07-21
Here are some up to newer methods you can use with Dapper that might be a little easier if there are others who wish to re-install Grub viewing this thread.

The easiest is the new 'Alternate' Install CD method, if you have the 'Alternate' Install CD, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub").

Also very easy, if you have the 'Desktop' Live/Install CD, you just open a terminal, get a Grub Shell, by typing; sudo grub
and do it similar to what you see illustrated in the following link, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD").

Regards, Herman :lol:

---

