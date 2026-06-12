---
title: "How does one revert to a previous version?"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by ArbitraryVitae on 2010-06-16
Greetings all,

I recently upgraded to 10.04 on my older laptop. It's causing some unacceptable slowdown. So I'd like to go back to 09.10 and I'm fairly new to the world of using Ubuntu, how do I do this?

Thanks in advance!

---

### Post by lechien73 on 2010-06-16
There's no easy way, and no rollback facility to go back to a previous version of Ubuntu.

Your best option would be to:

[LIST=1]
[*]Back up your /home folder and files.
[*]Use [APTonCD]("http://aptoncd.sourceforge.net/") to make a backup of all your currently installed packages.
[*]Perform a fresh installation of 9.10, the ISO can still be downloaded from [http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)
[*]Restore your /home folder and files, and restore any missing packages from your CD created with APTonCD.
[/LIST]

---

### Post by Martiini on 2010-07-04
to downgrade a Debian distro, one must use apt-pinning .... which means .. you create 
etc/apt/preferences  file ...

Package: *
Pin: release a=karmic
Pin-Priority: 1001

Package: *
Pin: release a=karmic
Pin-Priority: 60

Package: *
Pin: release a=lucid
Pin-Priority: 50


[http://linuxmafia.com/faq/Debian/downgrade.html](http://linuxmafia.com/faq/Debian/downgrade.html)
gives the full story and describes subject in depth ...

in case you get pkg errors .. you use .. dpkg -i --force-all / dpkg -r --force-all

---

### Post by sports fan Matt on 2010-07-05
The nice thing as lechien describes is it does not take long.  I use a more unconventional method and to get back up and running from a fresh install is usually 30 minutes or so.

---

