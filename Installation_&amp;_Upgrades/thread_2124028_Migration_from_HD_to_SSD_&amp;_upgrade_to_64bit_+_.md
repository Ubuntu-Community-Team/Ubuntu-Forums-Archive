---
title: "Migration from HD to SSD &amp; upgrade to 64bit + encryption.."
date: 2013-03-09
forum: Installation &amp; Upgrades
---

### Post by flosspike on 2013-03-09
Hi Forum users,
I'm stuck!. I have a 250Gb hard disk with ubuntu 12.10 i386 loaded upon it. I've discovered that my computer actually has a dual core processor so wanted to upgrade to 64bit, but then I had a fit of enthusiasm and bought a 120Gb SSD. 

I started by backing up my home directory to a NAS drive using the backup utility & then closed the system down. I removed the HD and lobbed it into a USB enclosure and fitted the new SSD. I booted the 64bit Ubuntu from the CD drive & installed that onto the SSD. Again, I like the security of encrypting my home directory.

Now all I want to do is access my old HD, which is encrypted, copy the contents of the Home folder across to the new SSD and then follow the advice from "How do I upgrade from x86 to x64 without osing settings" which uses "dpkg --get-selection > ~/installed-software"

The problem I have is the encrypted home folders are difficult to access. I can live boot and mount both drives but I can't get past the "access private data", I can access either the home folder on the x86 or x64 by simply booting on that drive, which is closer, I just can't access both at the same time stumbling at the private data access.

I have even re-installed the x64 onto the SSD using different passwords, as was originally using the same passwords and as I tried mounting both, the second drive would report an error, something about key already mounted. 

Has anyone before tried migrating to a smaller SSD from a larger HD, got around the encryption and successfully retained all they're data??

Any help would be most welcome.

---

### Post by Paddy Landau on 2013-03-16
I have got around the encryption before, but that was quite some time ago and complicated. The problem is that the process is so poorly documented.

I suggest something radically easier:

[LIST=1]
[*]Boot into your old system on the HDD. 
[*]Copy your files into a shared area on the HDD. 
[*]Boot into your new system on the SSD. 
[*]Copy the data from the shared area on the HDD into your encrypted home on the SSD. 
[*]Delete the shared area on the HDD. 
[/LIST]
You will save yourself a huge amount of hassle.

Alternatively, restore from your backups — it is a good test for whether or not your regular backups work correctly. This is how I would have done it.

---

