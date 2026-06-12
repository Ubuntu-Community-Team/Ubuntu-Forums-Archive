---
title: "Want to mount usb drive w/desktop /home on lappy"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by Scunizi on 2008-11-01
My desktop motherboard died so I rescued the drive that was a dedicated /home on that Hardy install and put it in an external USB housing.  I've been trying to get it to mount as /home on my laptop hardy install.. Here's what I did and the results...

1> terminal - used blkid to get UUID of the USB drive
2> changed reference in fstab for the /home partiton by commenting out the old partition reference and entering the USB UUID reference
3> booted to the live cd of Hardy, mounted the harddrive in the laptop and changed "home" to "oldhome".
4> booted the laptop and received an error.. unfortunatly I didn't write it down.
5> booted to the live cd and moved "oldhome" back to "home"
6> booted the laptop and got much further.. I was actually able to enter my user name and pass but then receive the following error

*User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from beinig saved.  File should be owned by user and have 644 perissions.  User's $HOME directory must be owned by user and not writable by other users.*

Note:  the login name and pass on the laptop is the same as the desktop was.  However the user id # on the laptop is 1001 and the old desktop was 1000.

My whole point of doing this is to be able to get into evolution and retrieve my address book and emails.. Hopefully backing them up to a file that I can then use in my standard laptop install with normal /home references.  I've tried the suggested help on the evolution site without success.

Any ideas/help would be appreciated.

---

