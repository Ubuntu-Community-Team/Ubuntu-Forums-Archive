---
title: "login problem after install"
date: 2017-03-04
forum: Installation &amp; Upgrades
---

### Post by gearheadgeek2 on 2017-03-04
I don't know if this is the right forum, but the problem is loosely related to install.

[FONT=Ubuntu, Arial, libra sans, sans-serif][COLOR=#111111]I'm trying to use Xubuntu 14.04 and now the login dialog box shows Guest instead of my login name. I've been all over the net and read what lightdm documentation I could find but have not found a solution. I had to install Xubuntu to a separate drive since the install hung up at grub install every time I tried to install.  After perhaps a dozen tries, I tried a separate disk and succeeded.  After everything was configured and rebooting several times to make sure all was ok (this was the second try - the first broke badly after the recommended dist-upgrade, which I did not try the second time), I moved the install (using clonezilla) to it's final resting place on a partition on another drive.  I fixed grub and fstab, and changed my uid:gid to match the servers I deal with. Now it wants me to log in as guest when I boot.  Naturally, I can choose other and log in with my login and password so the system seems OK otherwise.  It seems like the information the greeter uses is tied to uid or uuid or some such. Where does greeter get the information it uses to build that login dialog box?  Is there a way to let me choose uid:gid during install?[/COLOR][/FONT]

---

### Post by opsusec on 2017-03-06
what's your partition scheme looking like? LVM without RAID will do this sometimes. Encrypted Home folders are separate file-systems from root this way.

when partitioning a drive with GPARTED, it gives you the option to assign a new UUID to a drive.

---

### Post by gearheadgeek2 on 2017-03-06
My partition scheme is normal - no LVM or Raid.  Somehow the move changed how the greeter decides what/who to offer login.

---

