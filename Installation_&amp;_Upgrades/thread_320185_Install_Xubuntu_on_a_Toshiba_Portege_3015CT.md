---
title: "Install Xubuntu on a Toshiba Portege 3015CT"
date: 2006-12-16
forum: Installation &amp; Upgrades
---

### Post by KeatonB on 2006-12-16
Hey everybody
[INDENT]I'm fairly new to linux, although I have been playing around with Suse and various other distro's for awhile. I have run into a problem and after a day of searching I have found no solution that doesn't involve buying new hardware. My problem is getting Xubuntu installed on my 8 year old Toshiba Portege 3015ct laptop, which is a tiny 2.9lbs. The laptop can only boot from a Hard drive or a floppy, the cdrom drive and network card are connected via PCMCIA card slots, and there is a usb 1.1 port. I have found various ways of booting Xubuntu without being able to directly boot from cdrom, the problem is none of these methods will work with PCMCIA cdroms or USB pendrives. I also found network installs, but my network card requires NDISWRAPPER to work with linux. Is there is a way to create a bootable floppy disk that will 'see' a PCMCIA Cdrom, A USB Pendrive, or a NDISWRAPPER Network card? I don't want to take the hard drive out of the computer or re-install Windows. I can run Damn Small Linux in live-pendrive mode if it is needed[/INDENT]
[RIGHT]Thanks,
Keaton[/RIGHT]

---

### Post by gn2 on 2006-12-17
I have a Portege 3440CT which is similar, in that it only has an external PCMCIA cd-rom.

5.10 installed from the install cd-rom no problem, have you tried that?

---

### Post by phuturism on 2007-01-22
Same problem for me - I have a usb cdrom drive.

I ended up doing a netboot install from a win xp machine on the LAN - worked great!  Thread here...

[http://www.ubuntuforums.org/showthread.php?t=327597&highlight=windows+install+netboot](http://www.ubuntuforums.org/showthread.php?t=327597&highlight=windows+install+netboot)

---

### Post by fishymark27 on 2007-03-10
I used to xubuntu alternative cd and it worked like a charm directly from the pcmcia cdrom. except that now it doesn't recognise the pcmcia slot at all!

---

