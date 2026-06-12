---
title: "Won't dual boot windows 10 and ubuntu 15.10"
date: 2016-01-03
forum: Installation &amp; Upgrades
---

### Post by robcleghorn on 2016-01-03
Having issues getting the UEFI boot loader to recognise my ubuntu installation, it seems to just load Windows 10 without any boot menu with options.

Followed all the forums on this including running boot-repair but no joy.

Here is the boot repair output.
[http://paste.ubuntu.com/14393777/](http://paste.ubuntu.com/14393777/)

---

### Post by oldfred on 2016-01-03
Only the one model seemed to need a downgrade on the UEFI version. But all Acer have required a supervisory password and then setting trust on the Ubuntu/grub efi boot files. 

 Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)

---

### Post by robcleghorn on 2016-01-03
Thanks for the reply, actually it was the boot order, windows was still above ubuntu so the grub loader wasn't getting triggered...

---

