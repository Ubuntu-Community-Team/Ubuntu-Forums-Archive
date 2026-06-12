---
title: "Trying to recover 10.04 from 10.10 upgrade crash"
date: 2012-01-06
forum: Installation &amp; Upgrades
---

### Post by grey1beard on 2012-01-06
During an upgrade from 10.04LTS to 10.10, my toshiba satellite laptop suffered a power supply loss(running on mains adaptor ) at some time during the installation of the downloaded files.
Restoring power showed the 10.04 splash screen, then got as far as showing an old desktop folder in place, then a pop-up that repeatedly flashed into view for about 0.1 second at a time that says
 > The panel encountered a problem while loading "OAFID:GNOME_FastUserSwitchApplet"
_D_elete  D_o_n't delete
The tracker mouse icon is non-operative so I tried the keyboard strokes but that doesn't work during the brief appearance of the pop-up.

I've rebooted and tried grub menu -

"10.04.3 LTS, 2.6.32-12-rtai recovery mode" gets to a line

> [   1.850837]EXTS-fs: mounted filesystem with ordered data mode.
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: running /scripts/init-bottom ...
Done.
[    5.267064] Adding 1253028k swap on /dev/sda5.  Priority:-1 extends:1 across:12538028k
_
with a flashing cursor at the bottom, then no change over >10 minutes.

"10.04.3 LTS, 2.6.32-37-rtai recovery mode" gets to a line

> [   1.862216]EXTS-fs: mounted filesystem with ordered data mode.
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: running /scripts/init-bottom ...
Done.

_

 All other recovery kernels offered get to the same end line, with the exception of 10.04 LTS 2.6.24-16 rtai which quotes a variety of problems, finishing with 
> BusyBox v1.13.3(Ubuntu 1:1.13.3-1ubuntu11) built in shell (ash)
Enter  'help' for a list of built in commands.

(initramfs) _

This time with an active flashing cursor, and this led me via 'help' to the list.
I tried a sudo apt-get clean command as suggested on a forum thread, but it didn't find the sudo command.

Is there anything else I can try before I go for a completely new clean installation ?
Only a few recent folders will be lost, nothing disastrous.

John

---

### Post by 2F4U on 2012-01-06
If the system doesn't find the sudo command, it seems to be badly damaged. It may be better - to prevent future problems - to do a fresh install, in particular if you can backup the things you need easily.

---

### Post by grey1beard on 2012-01-07
Is it possible I might be able to use a 10.04 live cd to get access, with a view to returning to 10.04 , checking out any folders I've overlooked, before trying a new install of 10.10 (now that I have a new power supply unit :) )

John

---

### Post by dino99 on 2012-01-07
following this example, you should go ahead with the installation: boot on a livecd first.

[http://ubuntuforums.org/showpost.php?p=7929196&postcount=11](http://ubuntuforums.org/showpost.php?p=7929196&postcount=11)

---

### Post by grey1beard on 2012-01-07
Trying to boot from the live cd I have, and it takes a bit of encouragement, but in the end got to the choice screen.
Went for try live cd, just to see if this exposed the pre-installed folders, but after showing the ubuntu splash screen with the white to red dots thingy, it switched to a cli reading
> BusyBox v1,13.3 etc.....
Enter 'help'.....
(initramfs) _

Dino99, thanks for that link. I've had a quick read through the whole thread as well, and can see the drift, but faced with the above problem.
If I went for a new install, do I get the possibility of a new partition, alongside the old(busted?) one, with possible access to it?

Clutching a straws here, but I'm good at that.

John

---

### Post by grey1beard on 2012-01-07
Having problems with my old installion cds for 10.04, I've found a 10.10 (alternate) cd which has "Repair" choice on the first screen. 
Unfortunately, that seems to have got stuck till I hit the Enter key a couple of times and it is now onwards and upwards.
I'll edit this post as things develop (or not).

Stopped at 
> Loading additional components 89%
Configuring partman-crypto-dm

Started a second time with acpi=off, and quiet splash deleted (I think), and it got passed the previous stop, and got to a choice of where to put various things.
I chose to accept each choice as offered, but have now got stuck again.
I'll restart, and take note of the choices, and ask for guidance.

John

---

### Post by grey1beard on 2012-01-07
Should I have my wireless card switched off while I'm trying this ?

The Rescue mode fails at Autoconfiguration of Network

---

### Post by grey1beard on 2012-01-07
Choices - 
> /dev/sda1
/dev/sda2
/dev/sda5
Do not use a root file system

Which to go for ?
I assume I should select the 1st.
Then it offers
> Execute a shell in /dev/sda1
Execute a shell in the installer environment
Reinstall grub boot loader 
Choose a different root file system
Reboot the system

so I choose the 1st again.
What then happens is the screen goes blue, with a bottom white stripe and a #symbol at the extreme left.
All is now stopped - no signs of life, except I've just discovered that I can type onto the bottom white line.
Now what ???

---

### Post by grey1beard on 2012-01-07
It's a terminal type window, and accepts entries, but I've no idea what to do :(

---

### Post by grey1beard on 2012-01-07
Found my way in to the file system, and confirmed that there is no important data to be rescued.
I can therefore abandon the attempt at recovery and will mark this as Solved.
Pity there are no alternatives.

---

