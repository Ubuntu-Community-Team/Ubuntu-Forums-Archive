---
title: "Fresh Install, can't enable samba shares"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by wkulecz on 2008-05-02
Things have gone pretty smoothly so far with 8.04 until I tried to share my /data folder with samba for use by windows PCs.

Did the right click share folder menu selection and was told samba was not installed, dialog offered to install it, asked for password and samba seems to now be running when I look at system->administration->services.

Problem is when I try to create the share, I get a "you need to be administrator to do this error" but I see no way to get root privilege with this dialog.

I've been around the Linux block more than a few times and can do it manually, but this is IMHO a big bug compared to 6.06 samba setup which was the easiest one I've ever set up.

--wally.

---

### Post by Pumalite on 2008-05-02
This might help:
[http://doc.ubuntu.com/ubuntu/serverguide/C/configuring-samba.html](http://doc.ubuntu.com/ubuntu/serverguide/C/configuring-samba.html)
[http://linux.about.com/od/ubusrv_doc/a/ubusg33t01.htm](http://linux.about.com/od/ubusrv_doc/a/ubusg33t01.htm)

---

### Post by wkulecz on 2008-05-02
Seems my username did not get added to the sambashare group.  I added it, logged out, logged back in and could then create the shares as expected.

Still had to manually change the smb.conf WORKGROUP setting from the default to what I use.

--wally.

---

