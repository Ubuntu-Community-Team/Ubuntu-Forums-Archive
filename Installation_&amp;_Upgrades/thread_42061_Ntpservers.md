---
title: "Ntpservers"
date: 2005-06-15
forum: Installation &amp; Upgrades
---

### Post by belred on 2005-06-15
how do you add multiple ntp servers to ntpupdate?

i tried this

NTPSERVERS= "ntp.mycompany.net"
NTPSERVERS = "ntp.ubuntulinux.org"

and tried this:

NTPSERVERS= "ntp.mycompany.net ntp.ubuntulinux.org"

but this either of these willl not work correctly  when i'm home and when i'm at work.  i can only ever get it to work correcly in one location.  when i'm at home, i want to use ubuntulinux and when i'm at work ntp isn't allowed through our firewall and i have to use mycompany.  

any idea how to do this?

thanks,

bryan

---

### Post by desdinova on 2005-06-15
[QUOTE=belred]how do you add multiple ntp servers to ntpupdate?

i tried this

NTPSERVERS= "ntp.mycompany.net"
NTPSERVERS = "ntp.ubuntulinux.org"

and tried this:

NTPSERVERS= "ntp.mycompany.net ntp.ubuntulinux.org"

but this either of these willl not work correctly  when i'm home and when i'm at work.  i can only ever get it to work correcly in one location.  when i'm at home, i want to use ubuntulinux and when i'm at work ntp isn't allowed through our firewall and i have to use mycompany.  

any idea how to do this?

thanks,

bryan[/QUOTE]
 I installed ntp rather then ntpupdate as a server - in ntp.conf you can add multiple servers - easiest way is through the time/date applet in gnome

---

### Post by belred on 2005-06-15
i did do what you are saying.  i added the two servers to ntp.conf.  when i go to the datetime app (i'm using kde), i'm able to check "set date and time automatically" but the servers displayed are not the the ones i set.  do you know what config file date/time config uses on kde?

thanks,

bryan

---

### Post by desdinova on 2005-06-15
it would be in $HOME/.kde/share/config

---

### Post by belred on 2005-06-15
i searched all the files in /home/bryan/.kde/share/config and i don't see any files that contain any of the time servers listed in the date/time gui.   do you know the exact file name?

bryan

---

### Post by desdinova on 2005-06-15
[QUOTE=belred]i searched all the files in /home/bryan/.kde/share/config and i don't see any files that contain any of the time servers listed in the date/time gui.   do you know the exact file name?

bryan[/QUOTE]
 nope - sorry I'm a Gnome user at the mo with no trace of KDE on here

---

