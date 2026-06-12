---
title: "acer-wmi: unable to detect available WMID devices on boot"
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 416inversed on 2010-04-11
I just upgraded to beta2, now on boot I get an "acer-wmi: unable to detect available WMID devices" error on boot.

After grub, the screen flickers black for several seconds, the error message appears, a split second of xsplash screen, then right into GDM login. From there everything is normal (for a beta).

A previous forum post [http://ubuntuforums.org/showthread.php?t=1233149](http://ubuntuforums.org/showthread.php?t=1233149) lead me to believe it wasn't just a Lucid problem, but the solution presented in that thread didn't work.

But in attempting that solution, I noticed it also happens while booting from my Lucid liveUSB, but not from a Karmic stick... so maybe it is something in Lucid afterall.

Any thoughts on a fix? I already filed a bug report with xsplash, so should I just live with it  to see if it disappears with the RC?

---

### Post by wilee-nilee on 2010-04-11
> **416inversed said:**
> I just upgraded to beta2, now on boot I get an "acer-wmi: unable to detect available WMID devices" error on boot.

After grub, the screen flickers black for several seconds, the error message appears, a split second of xsplash screen, then right into GDM login. From there everything is normal (for a beta).

A previous forum post [http://ubuntuforums.org/showthread.php?t=1233149](http://ubuntuforums.org/showthread.php?t=1233149) lead me to believe it wasn't just a Lucid problem, but the solution presented in that thread didn't work.

[http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)
Will give your information about this command, I am not sure but your not supposed to run it on a running OS but at the command line at boot. I could be wrong but be careful with running a powerful command like this.



But in attempting that solution, I noticed it also happens while booting from my Lucid liveUSB, but not from a Karmic stick... so maybe it is something in Lucid afterall.

Any thoughts on a fix? I already filed a bug report with xsplash, so should I just live with it  to see if it disappears with the RC?

I think this is a development thing it happens on mine as well but I am running a acer aspire netbook.

It sounds like it boots up and runs right?

[http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)
Here is more information on this command. I believe it is not supposed to be run on a running system but from a command at boot. I could be wrong, but be careful with this sort of command it is one that can as I understand create problems as well.

---

### Post by 416inversed on 2010-04-11
Oh yeah, my Acer AOD250 finishes booting and runs just fine.

---

### Post by wilee-nilee on 2010-04-11
Glad it's booting, here is the paragraph from the wikipedia that I think is important.

A system administrator can also run fsck  manually if there is believed to be a problem with the file system. Because running fsck to repair a file system which is mounted for read/write operations can potentially cause severe data corruption/loss, the file system is normally checked while unmounted, mounted read-only, or with the system in a special maintenance mode that limits the risk of such damage.

---

