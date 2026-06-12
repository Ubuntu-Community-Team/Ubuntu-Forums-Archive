---
title: "installation from windows - no cdrom, no floppy"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by blackpaw on 2006-06-11
hi!

I have a opder subnotebook without a real floppy drive and also no cdrom built in. I would like to install xubuntu on it.
I tried several methods involving older installations, server install, conversions of "normal" ubuntu to xubuntu and vice versa, dist-upgrade
but now I want a fresh installation of xubuntu dapper because my system is pretty low-end.

I followed the nice explanations on this page:
[https://wiki.ubuntu.com/Installation/FromWindows]("https://wiki.ubuntu.com/Installation/FromWindows") (second part)
copied vmlinuz and initrd.gz from the extracted CD and used grub4dos, pointing the menu.lst to the files on the FAT partition.

When I start the system I get a boot promt "install ubuntu" - good.
If I do as told on the website, I get a network install with no possibility to install from the ubuntu-files that I copied from the CD :(
As my WLAN card is pretty strange (some 3com chipset that requires me to copy firmware manually) and not having a built-in network-jack I was stuck again. (yes, I know, weird notebook.. but it's very nice if it works ;) )

Then I followed the comment of Rob saying > Just a note: I think that /boot/initrd.gz above should read /ubuntu/install/initrd.gz Rob Pomeroy
and pointed the menu.lst to /ubuntu/casper/initrd.gz
the system then booted and stopped saying
> /bin/sh: can't access tty; job control turned off

Any clue what this means?

The website
[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/") gave me the idea that it might be a problem with the new installer, so I am downloading the "alternate" iso of Xubuntu Dapper now, maybe I'll have more luck like this. will post my experience...

thanks in advance


andreas

Edit:
Can anyone enlighten me about what the grub parameters used in the wiki mean and which one to use best for my enterprise? the parts about the ramdisk-size, the vmlinuz and the initrd.gz I understood ;)

like:
 root=/dev/rd/0 rw -- (in the netboot approach)
or:
 root=/dev/ram0 devfs=mount,dall (in the CD approach)

---

### Post by kaamos on 2006-06-11
I have a lifebook where I used the Windows NT/2000/XP (using Grub) -approach to install breezy. I had working eth0 from the boot, so it was actually pretty easy.. But the point of this post is: with no floppy, no cd and no network you have a pretty though installation scenario.. So please post your experiences in the wiki, especially if you succeed in the installation. ;-)

---

### Post by blackpaw on 2006-06-11
okay, using the "alternate" cd now, I am a small step further. 
The installer now comes as far as "no cdrom driver found"
and wants me to provide one.

I mounted the windows partition successfully with
mount -t vfat /dev/hda1 /media/xubuntu
but the installer wouldn't accept it as a cdrom drive :(

[https://wiki.ubuntu.com/Installation/FromHardDriveWithFloppies](https://wiki.ubuntu.com/Installation/FromHardDriveWithFloppies)
he apparently did the trick but he dd'd the iso on a linux partition.. I don't have one yet.. only unpartitoned space somewhere.

any idea how I could make him believe it is one?
Or maybe if I went for the network install, could I make ubuntu believe that a directory on my windows partition is a nfs server?

any idea how I will get xubuntu on this thing?


thanks


andreas

---

### Post by blackpaw on 2006-06-13
well...

I gave up :)

got myself a different kind of wlan card (proxim orinoco) and the netinstall went like a charm. :P
stupid atmel-crap from 3com. :(


andreas

---

