---
title: "Upgrading to a bigger hard drive"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by Rippy on 2007-01-28
I installed ubuntu on a puny 10gig hard drive. Now, I'd like to shift my music collection from windows to ubuntu (I have physically seperate drives for each, that i interchange with a Startech hard drive bay). Sadly, that would take up my remaining 5.7 gigs of space.

So now I have a 40gig drive, and I'd like to switch to that one. I've done some googling for a solution, but every result gave a completely different solution (different commands, apps, etc), so I wasn't sure which to trust. Can anyone help me out?

Simply put, I need to know how to shift my Ubuntu to a larger hard drive, while still retaining linux's funky partitions. How shall I proceed?

---

### Post by housam on 2007-01-29
Simply , prepare your new HDD for a fresh install of ubuntu . Do the partitioning manually and go for the installation.

---

### Post by Rippy on 2007-01-30
agh, I learn this right after I spent a good couple hours getting everything configured just right.. :'(

---

### Post by RandomJoe on 2007-01-30
No, there are ways to transfer the existing system.  (Else why do "bare metal" backups?)  They may not be _simple_ but they do work.  (Note, this isn't a comprehensive 'howto', you should definitely read the manpage for 'rsync' so you know how it works!  And be _sure_ everything is working well before blitzing the old drive!)

A method pretty close to what I do on my systems:
Install the old drive in a USB/firewire enclosure, or in another machine you can reach over the LAN.

Set up the new drive, and do a fresh install of the _same version_ OS as before.  (This takes care of the fiddly wierd-permission files.)

Plug in the USB drive, or make sure the network is up.  Use 'rsync' to transfer over all directories _except_ /dev and /proc.  This will overwrite any changed files with the version on the old drive, and add in any new files.  I use something like 'rsync -av --progress remote@machine:/path/to/files .' to drag the directory 'file' to the directory I'm currently in.  (Be careful - adding a / at the end of files means 'everything in files', not 'the directory files'!)

Reboot, and you should have your original system back.

Disclaimer:  I've not had to do this with Ubuntu yet, but I _have_ done it several times in the past with Slackware.  I back my computers up to a server with rsync, then if I screw something up royally or just decide to go back to what I had before after experimenting with a new OS I do this procedure to get right back to where I was at the time of the backup.  (With a handy script, of course, so I don't have to manually type anything.)

Either way, your original drive will still not be touched (unless you make a mistake in a command somewhere!) so you can always go back to it if needed... ;)

Alternatively, look for one of the full-system-backup programs available and use that to backup then restore...

---

