---
title: "Help! - Deleted /tmp files - Can't login"
date: 2006-09-17
forum: Installation &amp; Upgrades
---

### Post by freebirdwil on 2006-09-17
#-o 
I am running Ubuntu 6.06 in a dual boot environment with Windows XP Home SP2. Each OS has it's own HD. Grub starts it up. Everything has been working fine...until...

I noticed a new version of Firefox available for Linux. I unzipped tarball to /tmp. Then realized I should have exported it to /usr/lib/firefox (I think). So I deleted everything in /tmp and now I can only boot up Ubuntu using select session terminal option. I am not very good at command line and everything I try to adjust/edit gets either permission denied or can't find orbit-username. Before I delete Linux partition and start a brand new installation I thought I would ask for help. Have tried adduser, edit /etc/sudoers, /etc/password, /etc/groups, using recovery boot-up mode. Don't really understand what to do. Any merciful pros willing to help?

Thanks...
Edit/Delete Message

---

### Post by ape on 2006-09-18
what are the permissions on your /tmp directory?

they should be the following:

   drwxrwxrwt

and the directory should be owned by user root and group root.

---

### Post by BLTicklemonster on 2006-09-18
I reckon its not as simple as restoring stuff from the waste basket is it?

---

