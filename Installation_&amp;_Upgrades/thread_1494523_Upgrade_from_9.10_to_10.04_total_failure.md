---
title: "Upgrade from 9.10 to 10.04 total failure"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by SomethingFishy on 2010-05-27
Hi

I ran the upgrade from ubuntu 9.10 yesterday and it's now a mess.  Is there something I can do to refloat this ship?

The file download stage seemed to be working OK: I was watching it when it only had three minutes left to go.  I went away and came back a few minutes later and the screen had gone black.  OK I thought, this must be all part of the plan, so I went away and came back over an hour later: still nothing.  I decided, perhaps foolishly, to press the power button and boot it up.

Eek! Now I get the following errors:

mounting none on \dev failed: no such device

chroot:cannot execute /etc/apparmor/initramfs: no such file or directory

Then the message Ubuntu 10.04 LTS cruncher tty1 and a login prompt.  I can log in OK but don't know what to do next to recover the situation.

Rather alarmingly there is some activity on the system: lots of messages beginning with a number like [22.71309...

Please help :)

---

### Post by kansasnoob on 2010-05-27
Since you do get a TTY you could try:

```
sudo dpkg-reconfigure -phigh -a
```

If it does work expect it to take a long time, like an hour or two.

---

### Post by SomethingFishy on 2010-05-27
Thanks kansasnoob. I followed your guidance and quickly end up with multiple messages of the form 'unknown media type in type 'fonts/package' and the line 'This is not dpkg install-info anymore, but GNU install-info'...

---

### Post by SomethingFishy on 2010-05-28
Any more ideas anybody, please?

---

### Post by SomethingFishy on 2010-05-28
I think all the upgrade files have downloaded (is it possible to check?) and perhaps all I need is the right command to continue the installation?

---

### Post by kleiaustin on 2010-05-28
Same problem, my power went out during the installation. And now it says 
 
mounting none on \dev failed: no such device
 
No other errors. Just that, and I want my linux to work :(

---

### Post by SomethingFishy on 2010-05-28
I feel your pain kleiaustin. Let me know if you get any help and I'll do the same.

---

### Post by SomethingFishy on 2010-05-28
Hey Kleiaustin, I may be getting somewhere. I'm following Wilee Nilee's two instructions in this post: [http://ohioloco.ubuntuforums.org/showthread.php?t=1492719](http://ohioloco.ubuntuforums.org/showthread.php?t=1492719)

---

### Post by kansasnoob on 2010-05-28
I have used a chroot to fix things before but I never know what's needed until I begin:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Generally safe and possibly helpful commands:

apt-get update
apt-get dist-upgrade
apt-get -f install
apt-get clean
apt-get autoclean
apt-get autoremove
dpkg --configure -a


It quite often depends on what the terminal spits back at you :(

---

### Post by SomethingFishy on 2010-05-28
Thanks again kansasnoob.  I'm fixed now: the command 

sudo dpkg --configure -a

from wilee nilee's post (linked above) was what got me back on track.  I suspect there might still be a few loose ends so I'll research your suggestions and see what I can do to make everything tickety-boo.

Cheers again.

---

### Post by kleiaustin on 2010-05-31
Thanks guys, I think I figured it out.
This is the easiest way, though I lost some data
 
Heres what to do: First, download [http://sourceforge.net/projects/dban/files/dban/dban-2.2.6/dban-2.2.6_i586.iso/download](http://sourceforge.net/projects/dban/files/dban/dban-2.2.6/dban-2.2.6_i586.iso/download)
 
Its called Dban, It deletes the whole drive, and "nukes it" aka wipes it clean. Then reinstall the whole system. I couldn't figure out anything else. 
 
PS. Just call me Austin, since thats my name.

---

