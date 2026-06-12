---
title: "Power Mgr error: &quot;This program cannot start until you start the dbus session service&quot;"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by Getwild2 on 2006-06-05
Upon every boot after upgrading from Breezy to Dapper, I receive the following error message: 

[IMG]http://www.lbcflint.org/cjs/images/powermanagererror.jpg[/IMG]

How would I go about fixing this?  Thanks in advance...

---

### Post by bcarp on 2006-06-05
I did as well until I rebooted my machine after 
apt-get'ing nvidia drivers  (nvidia-glx) 

I mean a hard reboot not just a ctrl-backspace either..

---

### Post by Getwild2 on 2006-06-05
[QUOTE=bcarp]I did as well until I rebooted my machine after 
apt-get'ing nvidia drivers  (nvidia-glx) 

I mean a hard reboot not just a ctrl-backspace either..[/QUOTE]
That worked!  That's for your help!  8)

---

### Post by Getwild2 on 2006-06-06
Well it appeared as though the Nvidia driver update fixed the problem.  That is until I got back to work today and logged in at home through FreeNX.  It's funny, at home when I boot/login I do not receive the error but I do with FreeNX.  Wierd.  :-k 

Oh well, no biggie really.  If I come across a fix I will do so but I'm not going to waste my time with this one anymore if its not hurting anything.

---

