---
title: "AppArmor Testing Needed"
date: 2009-07-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ghindo on 2009-07-15
Jamie Strandboge has made [a blog post]("http://penguindroppings.wordpress.com/2009/07/15/apparmor-now-available-in-karmic-testing-needed/") about the AppArmor situation in Karmic:> After a lot of hard work by John Johansen and the Ubuntu kernel team, [bug #375422]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/375422") is well on its way to be fixed. More than just forward ported for Ubuntu, AppArmor has been reworked to use the updated kernel infrastructure for LSMsHowever, the new AppArmor still needs testing.  Head on over to [Strandboge's post]("http://penguindroppings.wordpress.com/2009/07/15/apparmor-now-available-in-karmic-testing-needed/") for instructions on how to test it out.

Happy huntin' :popcorn:

---

### Post by wayne_cat on 2009-07-15
Thank you for the hint .. time to rewrite my firefox and syslog profiles.

---

### Post by dino99 on 2009-07-15
seems to be fine now:

oem@oem-desktop:~$ sudo aa-status
[sudo] password for oem: 
apparmor module is loaded.
21 profiles are loaded.
9 profiles are in enforce mode.
   /usr/share/gdm/guest-session/Xsession
   /usr/sbin/cupsd
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/sbin/avahi-daemon
   /usr/lib/connman/scripts/dhclient-script
   /usr/sbin/tcpdump
   /usr/lib/cups/backend/cups-pdf
   /sbin/dhclient3
   /sbin/dhclient-script
12 profiles are in complain mode.
   /usr/sbin/traceroute
   /bin/ping
   /usr/sbin/mdnsd
   /usr/sbin/ntpd
   /usr/sbin/identd
   /usr/sbin/nmbd
   /usr/sbin/dnsmasq
   /sbin/klogd
   /usr/sbin/smbd
   /sbin/syslogd
   /sbin/syslog-ng
   /usr/sbin/nscd
6 processes have profiles defined.
4 processes are in enforce mode :
   /usr/sbin/cupsd (2914) 
   /usr/sbin/avahi-daemon (2887) 
   /sbin/dhclient3 (3212) 
   /usr/sbin/avahi-daemon (2886) 
2 processes are in complain mode.
   /sbin/syslogd (2447) 
   /sbin/klogd (2470) 
0 processes are unconfined but have a profile defined.

):P

---

### Post by andyrogers2008 on 2009-07-15
Works like a charm on my laptop.

---

### Post by zika on 2009-07-15
I get:```
$ sudo aa-status
apparmor module is loaded.
apparmor filesystem is not mounted.
```

---

### Post by andyrogers2008 on 2009-07-15
You need to read the blog first, you need to append a line to your kernel in grub.

---

### Post by zika on 2009-07-15
> **andyrogers2008 said:**
> You need to read the blog first, you need to append a line to your kernel in grub.Sorry, I've read first post once again ...

---

### Post by taavikko on 2009-07-15
> **zika said:**
> Sorry, which blog? What line? ...

There's a link in the post #1

But adding "security=apparmor" to kernel boot line will enable it for the session.

---

### Post by zika on 2009-07-15
> **taavikko said:**
> There's a link in the post #1

But adding "security=apparmor" to kernel boot line will enable it for the session.Yes I've seen that and I've corrected my post accordingly ... :)
Now I get:```
$ sudo aa-status
apparmor module is loaded.
8 profiles are loaded.
8 profiles are in enforce mode.
   /usr/lib/connman/scripts/dhclient-script
   /usr/share/gdm/guest-session/Xsession
   /usr/sbin/tcpdump
   /usr/lib/cups/backend/cups-pdf
   /sbin/dhclient3
   /usr/sbin/cupsd
   /sbin/dhclient-script
   /usr/lib/NetworkManager/nm-dhcp-client.action
0 profiles are in complain mode.
0 processes have profiles defined.
0 processes are in enforce mode :
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.
```Thank You for quick answer.

---

### Post by MacUntu on 2009-07-15
Works! :)

---

### Post by plun on 2009-07-24
Well....   apparmor-utils is maybe needed...):P


Works anyway.

---

### Post by dino99 on 2009-07-25
Work fine for me with apparmor-utils installed:

oem@oem-desktop:~$ sudo aa-status
[sudo] password for oem: 
apparmor module is loaded.
20 profiles are loaded.
6 profiles are in enforce mode.
   /usr/share/gdm/guest-session/Xsession
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/sbin/avahi-daemon
   /usr/lib/connman/scripts/dhclient-script
   /usr/sbin/tcpdump
   /sbin/dhclient3
14 profiles are in complain mode.
   /usr/sbin/traceroute
   /usr/sbin/mdnsd
   /bin/ping
   /usr/sbin/cupsd
   /usr/sbin/ntpd
   /usr/sbin/identd
   /sbin/klogd
   /usr/sbin/dnsmasq
   /usr/sbin/nmbd
   /usr/lib/cups/backend/cups-pdf
   /sbin/syslogd
   /usr/sbin/smbd
   /sbin/syslog-ng
   /usr/sbin/nscd
6 processes have profiles defined.
3 processes are in enforce mode :
   /sbin/dhclient3 (3385) 
   /usr/sbin/avahi-daemon (3056) 
   /usr/sbin/avahi-daemon (3055) 
3 processes are in complain mode.
   /usr/sbin/cupsd (3082) 
   /sbin/syslogd (2581) 
   /sbin/klogd (2604) 
0 processes are unconfined but have a profile defined.

---

