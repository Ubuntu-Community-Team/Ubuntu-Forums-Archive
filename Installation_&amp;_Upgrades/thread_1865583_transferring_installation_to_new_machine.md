---
title: "transferring installation to new machine"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by Jethro_uk on 2011-10-20
Hi all, I've a machine running an installation of 9:10 which I have got to be *exactly* what I need .. it's a media/download server.

I have recently acquired a new machine which is 10x better, and want to transfer the installation from one machine to the other. Obviously there will be driver issues for various bits and pieces, but beyond that I don't want to be messing for ages.

Can anyone suggest a possible strategy ? Would Clonezilla help ?

---

### Post by smurphy_it on 2011-10-20
Ubuntu 9.10 isn't support any longer.  They are at 11.10 right now.

---

### Post by oldfred on 2011-10-20
Since it is a server you may want Lucid 10.04 LTS. That is a one step upgrade so not huge changes.

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)

I just have a home desktop, but my backup recovery is a new install and restore my /home and other important data from the backup.
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

You can do a clean install to houseclean all the cruft. Plug in old drive in new system and copy over /home and anything else you want.

---

### Post by Jethro_uk on 2011-10-20
> **smurphy_it said:**
> Ubuntu 9.10 isn't support any longer.  They are at 11.10 right now.

I don't really care atm. IME, Ubuntu doesn't really do upgrades. I started at 7.10 and every upgrade from them on my desktop install broke something and took ages fixing. I stopped at 10.10, when a bug which crept in somewhere after 8.04 made my system unusable, and wasn't fixed.

However my 9.10 server is rock solid. I don't use the console on it, I neatX in, or use browser apps. So I'm not too fussed about snazzy whizzy stuff.

---

### Post by Jethro_uk on 2011-10-20
UPDATE

I am overjoyed to find the new machine has 4GB memory, as opposed to the old machines 2GB. Which gives me an idea ...

Is there a way to run a virtualisation engine (VMBox ?) and load the old 9.10 boot into that, from a disk image ? I could then install 10.04, run the old server in a VM, and transfer the settings and software in a side-by-side session ?

---

