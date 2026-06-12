---
title: "Pre-installed Windows 8.1, Xubuntu 15.04 No grub"
date: 2015-06-22
forum: Installation &amp; Upgrades
---

### Post by Matt0001 on 2015-06-22
Hello, I've installed Xubuntu 15.04 on my Acer Aspire laptop. Install seemed to go fine. I have disabled fast boot and secure boot. I have run boot-repair. Computer boots straight into Windows, F12 boot options does not show any option other than windows.

[http://paste.ubuntu.com/11754708/]("http://paste.ubuntu.com/11754708/")

Any ideas? Thank you so much for your help. I've been using Ubuntu since 5.10, but this is the first time I've tried to install it on anything other than a Windows XP or Vista system.

---

### Post by oldfred on 2015-06-22
Acer seems to be one that requires you to set a UEFI password (never ever lose that) and that opens up more settings that then let you "trust" other systems, so you can boot them.

       Screenshots of secure boot settings Asrock, Asus, HP, Acer
[https://neosmart.net/wiki/disabling-secure-boot/](https://neosmart.net/wiki/disabling-secure-boot/)

 Video on getting into UEFI - 1 Min Acer but similar to all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)
      
 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

---

### Post by Matt0001 on 2015-06-22
Thank you! The third link was exactly what I needed.

---

