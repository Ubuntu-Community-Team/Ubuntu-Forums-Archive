---
title: "Ubuntu Edgy Eft (6.10) as Guest Domain in Xen"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by Culture20 on 2007-01-11
I've been doing some searching, but haven't been able to find anything like this yet.  I'm trying to install Edgy (or for that matter, even 6.06 LTS, and even 5.10) as a Guest HVM domain for Xen on a machine with intel's VT cpus.  I've gotten Suse, Gentoo, RHEL, & Fedora to install, but any Ubuntu CD gives me a blank black screen and no error messages, including the alternate & server install CDs.

Is there something special that the Ubuntu CDs do that the others don't?
Is there a way I could possibly boot from another medium (e.g. virtual floppy), then install from the iso/CD?
Is there a special ctrl+alt+F#+wave_a_chicken key sequence to skip past the hangup?

Heck, even Winblows is installing as an HVM (unmodified) guest.

](*,) 

Thanks a bunches

-C20

---

### Post by Culture20 on 2007-01-16
A little bump since this topic is on page 19 already...

Is there a way to rebuild the CD ISO with a new bootloader (for the sledgehammer approach)?

---

### Post by Culture20 on 2007-01-17
I just checked with Feisty Fawn Herd-2, same result.
Any clues anyone?  I'm really hoping to use Ubuntu as an HVM guest so I can help others solve cross-distro issues, but am about ready to throw in the towel on this distro.

---

### Post by mojo2317 on 2007-03-22
Hi there,
For a probable answer to this, check out:
[http://dev.osso.nl/herman/blog/2006/12/24/ubuntu-bootmenu-too-shiny-for-xen-with-hvm/](http://dev.osso.nl/herman/blog/2006/12/24/ubuntu-bootmenu-too-shiny-for-xen-with-hvm/)
He found that using the tiny net-booting mini.iso file, it doesn't hang on boot!  It works for me; installing on hvm right now.. (it is rather slow..)
Anyway, hopefully this is more useful than the [other comments]("href="http://ubuntuforums.org/showpost.php?p=2049202&postcount=2") you received. ;-)
mojo

---

### Post by Culture20 on 2007-03-22
Thanks!  That was perfect.  There was another post on the same site which was easier too:

Simple solution posted on this site from Colin Watson:
[http://dev.osso.nl/herman/blog/2006/12/24/ubuntu-bootmenu-too-shiny-for-xen-with-hvm/](http://dev.osso.nl/herman/blog/2006/12/24/ubuntu-bootmenu-too-shiny-for-xen-with-hvm/)

"Try holding down the Shift key while booting the CD; this should let you skip gfxboot."



And it worked!  Currently installing Ubuntu in HVMs.  Now I can support Ubuntu easier.  Thanks Colin!  Thanks Mojo2317!

---

### Post by mojo2317 on 2007-03-23
lol!  I've gotten in the habit of not reading comments; glad someone else still does! :-)
Thanks!

---

