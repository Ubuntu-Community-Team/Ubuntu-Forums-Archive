---
title: "[SOLVED] white screen after kernel update"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by excogitation on 2008-06-15
I updated to the latest kernel 2.6.24-19 (from 2.6.24-17) - but now after I enter
my username and password the login screen turns white after a few seconds.

[URL="http://pastebin.com/m36a1e841"]output of tail dmesg, syslog, Xorg.0.log
[/URL]

I suspect it is related to the fglrx driver but I don't really know.

I also installed the linux-restricted-modules-2.6.24-19-generic - but
it didn't help. (why weren't those installed with the update?)

Also - why do I have to manually install the virtualbox-ose-guest-modules
and virtualbox-ose-modules after each kernel update...
couldn't the update manager take care of that?

---

### Post by PmDematagoda on 2008-06-15
Try this:-

1) Move to a tty by pressing Ctrl+Alt+F1.

2) Login and execute:-
```
killall compiz.real
```

3) Move back by pressing Ctrl+Alt+F7.

See if that clears it up for you.

---

### Post by excogitation on 2008-06-19
Thanks for your help, PmDematagoda.

Unfortunately I ran dpkg-reconfigure xserver-xorg before reading your post and
ended up with a black screen instead of the login window.

So I uninstalled the drivers and installed the latest one following [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide").

Now everything is as it was before - just some hours lost...

---

