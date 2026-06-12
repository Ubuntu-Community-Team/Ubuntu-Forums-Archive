---
title: "tar root dir on Gutsy and restore on Hardy -  will there be problems?"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by beaker15 on 2008-11-21
Hi

I'm upgrading my server onto a physically new box with better spec. My current installation is a Gutsy server and my plan was to tar the root of this server, excluding /dev /sys and fstab and untar it onto my new server installation. My question is whether this will work if i install 8.04 on the new server and untar onto this different version, will i encounter problems?

(On another note, my original plan was to just install Gutsy onto the new server so i know there won't be any conflicts but i haven't got the original disk and all the ones i have downloaded don't seem to work. The disk check is always successful and the install seems to go fine but when booting up from the hard drive, it gets as far as
***Running local boot scripts (/etc/rc.local)        [ok]***

and then doesn't get any further. I'm stumped on this one)

little help please?

---

### Post by lemming465 on 2008-11-22
> if i install 8.04 on the new server and untar onto this different version, will i encounter problems?
I think you'd encounter a lot of problems, so I'd suggest not doing that.
> it gets as far as
Running local boot scripts (/etc/rc.local)
This is the last thing that happens before X starts; if you aren't getting video it usually means that there is a configuration problem with the driver for your video chip.  Either try a server-install without X (text console would probably work), or try booting in VESA safe mode, or use [Ctrl]-[Alt]-[F1] to switch to a text console.

If you can't get the Gutsy install to work, my next ploy would be to install Hardy on the new server, and then just copy the data and local applications from the old one (/home, /usr/local, /opt, ...)  It's going to be a lot less work to set up the services and applications again than it would be to untangle a Gutsy overlay on a Hardy base.

---

### Post by terazen on 2008-11-22
Yeah I tried doing what you are asking before and Lemming is right.  It was much less work to just install from scratch and copy specific files over than untangle stuff.

Mine was from dapper to hardy.  Basically just zipped up all my key directories and config files keeping the file permissions(most time consuming), ran `dpkg --get-selections` on both boxes, and installed a slew of packages on the hardy box until they were the same.  

I'm keeping the dapper box on a different ip address for a while until I'm sure I did it right.

---

