---
title: "xdmcp in karmic"
date: 2009-08-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by radwis on 2009-08-13
hi guys,

I can't see any option to use xdmcp login in karmic. do not see an option at login, the current gdmsetup gui doesn't contain that neither.

can anybody confirm or not the same?

can it be done by cui, changin some options in /etc/gdm/gdm.conf
like putting
[xdmcp]
Enable=true

??
radek

---

### Post by JRV on 2009-10-03
I have been wondering about that too.  For now I am logging in and using 
Terminal Server Client. XDMCP is enabled in Terminal Server Client by installing xnest.

That works for an XDMCP client, but I can't figure out how to enable an XDMCP server.  It used to be in Login Window, but that is no longer included.

 Does anyone have any ideas?

---

### Post by radwis on 2009-10-08
anyone? please

---

### Post by joddy on 2009-10-21
I managed to use XDMCP on Ubuntu karmic by editing the file

/etc/gdm/custom.conf

and adding these lines:

[xdmcp]
Enable=true

Then, restart gdm or reboot the PC:

sudo /etc/init.d/gdm restart

Further configuration parameters for custom.conf are available at:
[http://library.gnome.org/admin/gdm/2.28/configuration.html.en](http://library.gnome.org/admin/gdm/2.28/configuration.html.en)


Apparently, file /etc/gdm/custom.conf is now used, instead of /etc/gdm/gdm.conf used in previous GDM and Ubuntu releases.

---

### Post by wlad0 on 2009-10-25
Hi joddy,

I have one question. In my case, file /etc/gdm/custom.conf doesn't exists. Create new one, add

[xdmcp]
Enable=true

and restart GDM but no change.

Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic
Kernel:         2.6.31-14-generic i686

$ ls -al /etc/gdm/
-rw-r--r--   1 root root   132 2009-07-07 21:49 failsafeBlacklist
-rwxr-xr-x   1 root root  8620 2009-07-07 21:49 failsafeDexconf
-rwxr-xr-x   1 root root  8528 2009-07-07 21:49 failsafeXinit
-rwxr-xr-x   1 root root  4582 2009-07-07 21:49 failsafeXServer
-rw-r--r--   1 root root  2555 2009-08-25 15:40 gdm.schemas
drwxr-xr-x   2 root root  4096 2009-10-20 18:13 Init
drwxr-xr-x   2 root root  4096 2009-10-20 18:13 PostLogin
drwxr-xr-x   2 root root  4096 2009-10-20 18:13 PostSession
drwxr-xr-x   2 root root  4096 2009-10-20 18:13 PreSession
-rwxr-xr-x   1 root root  6417 2009-08-25 15:40 Xsession

---

