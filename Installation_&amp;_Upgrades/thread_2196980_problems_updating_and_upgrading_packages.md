---
title: "problems updating and upgrading packages"
date: 2014-01-01
forum: Installation &amp; Upgrades
---

### Post by andrew725 on 2014-01-01
Hi,

I tried updating the packages on my 12.04 LTS server over the weekend and it just got stuck on a certain section.  Of course the windows machine that I had my SSH session open on crashed overnight, thus not allowing me to copy/paste the exact part it stalled on.  I believe the section it got hung up on was trying to install something like postdrm or something along those lines, though I'm not 100% sure.

Last night I tried to updated the packages again.  Upon running sudo apt-get update, it errored out on this part, so I ran what it said to run:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

upon running that, it hung up on this part:
andrew@backup-server:~$ sudo dpkg --configure -a
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up libreoffice-common (1:3.5.7-0ubuntu5) ...
Setting up libdevmapper-event1.02.1 (2:1.02.48-4ubuntu7.3) ...
Setting up grub-pc (1.99-21ubuntu3.14) ...


I let it sit there for a good 5-6 hours before killing it. 

also to note, when I first ran sudo apt-get update and then sudo apt-get upgrade on Saturday night, it definitely started updating the packages because it asked me if I'd like to keep my local samba config file and it ended up screwing up grub.  my samba shares are also not working correctly.  furthermore, grub doesn't seem to automatically boot after 10 seconds, like what's set in the config file..

Can anyone help me out with this so I can get my packages updated?

Thanks,

Andrew

---

