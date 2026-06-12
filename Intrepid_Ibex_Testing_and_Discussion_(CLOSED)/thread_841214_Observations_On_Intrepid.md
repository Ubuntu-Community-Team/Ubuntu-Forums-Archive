---
title: "Observations On Intrepid"
date: 2008-06-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-06-26
Thanks to Raptor45's excellent sticky, my Intrepid pre alpha upgrade was totally painless.

Some observations:

The Logitech G15 keyboard packages have been upgraded and it works out of the box. Top stuff.

Problem a: I dont like how the keyboard is being init'ed too early in the boot process. It gets setup before the logging is on and I dont get to see the g15deamon log details on init.

EDIT: Now think this was my fault with messing around on hardy compiling my own binaries and doing init. Ooops.

Problem b: The volume control on the G15 doesnt seem to work with pulse audio

Problem c: During init the kernel reports that the hardware clock cannot be set by any known method and fails

Problem d: I too had the pc speaker pulse bug and used the known workaround with blacklisting the module

Problem e: AppArmor isnt happy on boot

Problem f: Pulse audio isnt happy and has various errors in the logs

Problem g: This is an annoyance on Hardy too. HDDs dont seem to spin down by default and theres no GUI to prompt it. Im trying out  sudo hdparm -S24 /dev/sdd as well as my other HDDs to see if that works. Cant understand why spin down of HDDs is not enabled by default - even if it was set to say 30mins or something.

The new flash version is working nicely in firefox and its good to have the new GCC version too. I wonder if Open Office 3 will be ready in time.

Some packaging points:

Tripwire remains outdated
No recent svn builds of mplayer are available (Im compiling my own)
Yasm is outdated
x264 and lib x264 are outdated

Overall Im excited to see whats happening with Intrepid and to contribute to testing so that this release of Ubuntu can be the very best release ever :guitar:

---

### Post by soccerboy on 2008-06-26
> **Nullack said:**
> Thanks to Raptor45's excellent sticky, my Intrepid pre alpha upgrade was totally painless.

Some observations:

The Logitech G15 keyboard packages have been upgraded and it works out of the box. Top stuff.

Problem a: I dont like how the keyboard is being init'ed too early in the boot process. It gets setup before the logging is on and I dont get to see the g15deamon log details on init.

Problem b: The volume control on the G15 doesnt seem to work with pulse audio

Problem c: During init the kernel reports that the hardware clock cannot be set by any known method and fails

Problem d: I too had the pc speaker pulse bug and used the known workaround with blacklisting the module

Problem e: AppArmor isnt happy on boot

Problem f: Pulse audio isnt happy and has various errors in the logs

Problem g: This is an annoyance on Hardy too. HDDs dont seem to spin down by default and theres no GUI to prompt it. Im trying out  sudo hdparm -S24 /dev/sdd as well as my other HDDs to see if that works. Cant understand why spin down of HDDs is not enabled by default - even if it was set to say 30mins or something.

The new flash version is working nicely in firefox and its good to have the new GCC version too. I wonder if Open Office 3 will be ready in time.

Some packaging points:

Tripwire remains outdated
No recent svn builds of mplayer are available (Im compiling my own)
Yasm is outdated
x264 and lib x264 are outdated

Overall Im excited to see whats happening with Intrepid and to contribute to testing so that this release of Ubuntu can be the very best release ever :guitar:

I broke parts of my fstab file trying out the ecrypt-utils package as detailed in 8.10 blueprints.  When it creates the ~/Private directory, it is owned by root instead of the user and if you don't use sudo then fstab can't be edited.  I guess I might try to take a stab at manually editing fstab but most likely go for a clean install as it has been 2 weeks since I installed.  I am getting itchy to configure ubuntu again.

---

### Post by Gina on 2008-06-26
I'm seeing a lot of those bugs too particularly on my AMD64.  Intrepid behaves much better on my 6 yr old laptop.

---

### Post by soccerboy on 2008-06-26
I am still waiting for the integration of empathy into gnome.  It is slated for 2.24 but I still haven't seen anything with empathy install.

---

### Post by PmDematagoda on 2008-06-27
About the AppArmor problem, perhaps that may be because a version of AppArmor for Linux kernel 2.6.26 has not yet been made, so unfortunately you would have to wait for Novell to release such a version.

---

