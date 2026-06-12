---
title: "PXE Installation searches for cdrom?"
date: 2011-07-24
forum: Installation &amp; Upgrades
---

### Post by SeaKing on 2011-07-24
I followed the ubuntu help instructions for creating [PXEInstallMultiDistro.]("https://help.ubuntu.com/community/PXEInstallMultiDistro?action=fullsearch&context=180&value=linkto%3A%22PXEInstallMultiDistro%22") But when I want to boot I get the error megssage (see attachment). The installation searches for /cdrom?
The whole cd/image content is in /.../.../i386, the path you can see before /cdrom. Where's the mistake?

---

### Post by SeaKing on 2011-07-24
Problem solved, it was just a wrong path defined, it had nothing to do with /cdrom.

The cdrom error came later the boot ;) 

massage: 
Please provide a name for this Disc, such as 'Debian 5.0.2...'

solution:
While copinging the cd content the folder .disk hadn't be copied with so just use

cp -R /media/cdrom/* /var/lib/tftpboot/<foldername>/ # for copying everthing or
cp -R /media/cdrom/.disk /var/lib/tftpboot/<foldername>/.disk # for copying just the folder

---

### Post by sdpagent on 2012-12-19
> **SeaKing said:**
> Problem solved, it was just a wrong path defined, it had nothing to do with /cdrom.

The cdrom error came later the boot ;) 

massage: 
Please provide a name for this Disc, such as 'Debian 5.0.2...'

solution:
While copinging the cd content the folder .disk hadn't be copied with so just use

cp -R /media/cdrom/* /var/lib/tftpboot/<foldername>/ # for copying everthing or
cp -R /media/cdrom/.disk /var/lib/tftpboot/<foldername>/.disk # for copying just the folder

Thank you so much, I had just made the same mistake, so your not alone.

---

