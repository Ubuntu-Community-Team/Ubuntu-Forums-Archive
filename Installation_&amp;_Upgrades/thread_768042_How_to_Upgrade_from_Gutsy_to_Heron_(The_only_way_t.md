---
title: "How to Upgrade from Gutsy to Heron (The only way that worked for me)"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by linuxd00 on 2008-04-26
There are different ways to upgrade:
[LIST]
[*]**supposedly you can run a script**(do in root mode!) called cdromupgrade which is in the root of the alternate CD...
but that didnt work for me (the script crashed).

[*]also **using synaptic** by adding all heron sources to  sources.list but for me it just froze when trying to upgrade
[*]and the** using update manager ** but it also just froze when trying to upgrade...
[*] an by **command line!** i think its the fastest and most simple(you only need to copy & paste 5 commands from this post!). this i will explain
[/LIST]
I had the alternate CD and wanted to use it in order to save bandwidth. but the upgrade script just crashed.


So i added the CDrom manually to the sources(NEVER add a cd rom manually by editing sources.list)
First i mounted the ISO using (if you have a burned CDROM disk  you can skip this)
```
sudo mount -o loop /path_to_the_ISO/ubuntu.iso /media/cdrom
```

then

```
 sudo apt-cdrom add -d /media/cdrom -m
```

then 
```
sudo apt-get update
sudo apt-get dist-upgrade

```

The problem was that the command line upgrader then wanted to upgrade but didnt seem to care about the CD... it still wanted to download 800 MB (or maybe it did i was not sure i later realized maybe it did)
so i decided to be sure it would upgrade only from the CD.

edit  sources.list
```
sudo gedit /etc/apt/sources.list
```
and comment out all sources **but** the CDrom.(put a # in front)

and re-run update and upgrade commands above

The thing with this was that the upgrader now said it was going to deinstall all of my programs for which it didnt found a new version on the CD...(like 250!)

i should say that i have Xubuntu and Ubuntu installed... so now i think that the upgrader was going to upgrade Ubuntu normally but since the alternate CD was only for Ubuntu it was going to deinstall xubuntu(since it didnt have any packages for Heron Xubuntu on it). maybe if i had only ubuntu everything would have been ok...


Maybe somebody who tries this and doesnt have Xubuntu installed aditionally can tell their experiences?

just do the command and it will tell you how many programs its going to upgrade/deinstall/update... and you can choose to proceed or abort (y/n)

UP TO THIS POINT MY SYSTEM WASNT CHANGED AT ALL!(apart from my sources.list)

ok so i decided to go to uni and do a internet update(30MB bandwidth)... aborted the upgrade .Since nothing is changed it is still safe to do so

then i decommented the online sources and redid the dist-upgrade and pressed yes...
and then one 2 hours later i had heron running! :)
you shouldnt just leave as somewhere in between it will ask you if you want to keep some settings or accept new ones... i just pressed always enter(which selects the recommended settings. i wish i could find a way to do this automatically since i all recommended options worked perfectly)

It feels faster that gutsy on my Thinkpad X31 1,6ghz. :guitar:

Only things i had to fix was to deblacklist my Graphics card so DRI and thus Compiz would work again.
Also my third mouse button is gone.. but i think its only a matter of fixing something small.

Please share your experiences

---

### Post by md5hash on 2008-04-30
cool just in time

---

### Post by IamAcoconut on 2008-04-30
Why not perform upgrade from the Heron CD (say desktop)? 
Should this work for an encrypted (on one partition - all but /boot) installation as well?

---

### Post by davidmaxwaterman on 2008-05-03
> **linuxd00 said:**
> ...supposedly you can run a script (do in root mode!) called cdromupgrade which is in the root of the alternate CD...
but that didnt work for me (the script crashed).

I had the alternate CD and wanted to use it in order to save bandwidth. but the upgrade script just crashed.



EDIT: I spoke (several hours) too soon. The installation failed with these errors :

```

Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/pool/main/o/openoffice.org/openoffice.org-calc_2.4.0-3ubuntu6_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/pool/main/o/openoffice.org/openoffice.org-common_2.4.0-3ubuntu6_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/pool/main/t/ttf-arphic-uming/ttf-arphic-uming_0.2.20080216.1-0ubuntu1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/pool/main/g/gnome-user-docs/gnome-user-guide_2.22.0+svn20080407ubuntu1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/pool/main/p/popularity-contest/popularity-contest_1.43ubuntu1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/pool/main/p/pppoeconf/pppoeconf_1.17ubuntu1_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/pool/main/p/po-debconf/po-debconf_1.0.10_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/pool/main/p/pidgin/pidgin_2.4.1-1ubuntu2_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/pool/main/p/powernowd/powernowd_0.97-2ubuntu4_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/pool/main/p/pulseaudio/pulseaudio-module-gconf_0.9.10-1ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/pool/main/p/pulseaudio/pulseaudio-module-hal_0.9.10-1ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/pool/main/p/pulseaudio/pulseaudio-module-x11_0.9.10-1ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/pool/main/t/transmission/transmission-common_1.06-0ubuntu4_all.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/pool/main/t/transmission/transmission-gtk_1.06-0ubuntu4_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/pool/main/t/ttf-arabeyes/ttf-arabeyes_2.0-1ubuntu1_all.deb Hash Sum mismatch

```

Seems like it's trying to access the CDROM, instead of the mounted ISO. I'm not sure where to go with this right now, so I'll put it off until I have a CDROM writer.

What I wrote before it failed...

Thanks for this.

While I noticed that it didn't work for you, and it hasn't actually completed for me yet, it looks like it is doing what it's supposed to, and it certainly hasn't crashed (yet).

Note that you're supposed to run it using the full pathname; for me that is 'sudo /media/cdrom/cdromupgrade', since I mounted the iso at the same point as I would have if I had burned the CD-ROM and put it in the drive.

Of course, it is downloading a load of updates, since there have been updates since the ISO was created, but it certainly seems to have avoided downloading a lot of stuff...well, I hope that's why it's faster anyway (it could be that my bandwidth has gone up, I suppose).

Thanks :)

Max.

---

### Post by zedstrange on 2008-05-24
```
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/pool/main/o/openoffice.org/openoffice.org-core_2.4.0-3ubuntu6_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/pool/main/o/openoffice.org/openoffice.org-common_2.4.0-3ubuntu6_all.deb  Hash Sum mismatch
```

I have saem problem tryingto upgrade off alternate CD.  Except i am running of the cd itself. 

I have no idea from here.   tried running with --fix-missing didnt help eith

---

