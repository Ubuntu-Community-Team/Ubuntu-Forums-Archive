---
title: "Presario C700s really don't like installing Ubuntu..."
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by Kouy on 2008-02-27
So I just got a new laptop today and I've been spending all day researching these problems but it seems another problem always pops up. Initially when I put in the 7.04 live cd and tried to boot it up I got an error that said, "/bin/sh: can't access tty; job control turned off" I managed to get past this by hitting f6 on the main screen and adding "break=top" then "modprobe piix" and "exit" at the command line and all was well and good for a while until another error came up that said, "failed to start xserver" So I thought I fixed this by entering, "sudo dpkg-reconfigure xserver-xorg" and again this worked for a while until I got to the step where it says, "Desired default color depth in bits" and I select 24 and a console opens up at the bottom and says, "xserver-xorg postinst warning: overwriting possibly-customised configureation file; backup in /etc/X11/xorg.conf.20080226232901 dexconf: error: cannot generate configureatio file; xserver-xorg.config/display/modes not set. Aborting. Reconfigure the X server with "dpkg-reconfigure xserver-xorg" to correct this problem. xserver-xorg postinst warning: error while preparing new Xorg X server configuration file in /etc/X11/xorg.conf.dpkg-new; not attempting to update existing configuration" So why not? I try the same thing again and the same error in the same place. At this point I was frustrated and went and got the 6.06 live cd. I got the same initial error but I was able to get onto the desktop by using the "break=top..." solution safe graphics mode but then when I got to the desktop the cursor wasn't configured right at all and if I just touched the touch pad the cursor would zip all around the screen and I had no control. Anyways I got to the install on the desktop using my keyboard and got as far as the partitioning which after I click next it just stops and doesn't go forward and won't allow me to to go back, I don't have any blank discs so I have the 7.10 live cd shipit'd but that will take weeks and I still have no guarantee that will work. Somebody please bail me out here, I can't figure this out. [-o<

---

### Post by wandalalakers on 2008-02-27
I haven't done it but I've read you can create a bootable usb drive with ubuntu.  If you don't have a jump drive. Find a co-worker or family member and ask them for three blank cds.  This way you can try 7.10 sooner than later and you have two blank cds for other stuff.

---

### Post by Kouy on 2008-02-27
I have a flash drive and I've looked into booting up linux on it many times before, before I ordered my first Ubuntu live cd and it says there are ways but none of them seem very simple or practical and although I'm not a complete linux noob I don't like to go too far down a path that I don't know enough about because I have risked thinking I know what I was doing before and changed one wrong thing and nearly lost everything. So just to be on the safe side I would rather not dabble in flash driving OS booting if I don't have to.

edit: Plus I have a deathly slow wireless connection and it disconnects a lot so it would take a lot of luck for me to download the iso file, which when I did try before was going to take about 2.5-3 hours. I could always use a torrent but those seem to take days longer even so I would be just as likely to take my chances and hope I can actually hold a connection for 3 hours.

---

