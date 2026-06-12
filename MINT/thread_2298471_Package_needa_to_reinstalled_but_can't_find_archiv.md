---
title: "Package needa to reinstalled but can't find archive"
date: 2015-10-11
forum: MINT
---

### Post by Devon_suz on 2015-10-11
I was trying to install synology cloud on Linux Mint version of ubuntu There nly was an rpm on their website. I used alien and it had a problem with scripts so I tried to use alien install again and now I can't actually update anything

This is what the result was : I then trie sudo apt-get install -f

Any suggestion how to remove this programme?
I've actually found a deb package for it soHelp please


```
sudo alien -i synology-cloud-station-3.2-3487.x86_64.rpm
warning: synology-cloud-station-3.2-3487.x86_64.rpm: Header V4 RSA/SHA1 Signature, key ID 86a998db: NOKEY
warning: synology-cloud-station-3.2-3487.x86_64.rpm: Header V4 RSA/SHA1 Signature, key ID 86a998db: NOKEY
warning: synology-cloud-station-3.2-3487.x86_64.rpm: Header V4 RSA/SHA1 Signature, key ID 86a998db: NOKEY
warning: synology-cloud-station-3.2-3487.x86_64.rpm: Header V4 RSA/SHA1 Signature, key ID 86a998db: NOKEY
warning: synology-cloud-station-3.2-3487.x86_64.rpm: Header V4 RSA/SHA1 Signature, key ID 86a998db: NOKEY
warning: synology-cloud-station-3.2-3487.x86_64.rpm: Header V4 RSA/SHA1 Signature, key ID 86a998db: NOKEY
warning: synology-cloud-station-3.2-3487.x86_64.rpm: Header V4 RSA/SHA1 Signature, key ID 86a998db: NOKEY
warning: synology-cloud-station-3.2-3487.x86_64.rpm: Header V4 RSA/SHA1 Signature, key ID 86a998db: NOKEY
warning: synology-cloud-station-3.2-3487.x86_64.rpm: Header V4 RSA/SHA1 Signature, key ID 86a998db: NOKEY
warning: synology-cloud-station-3.2-3487.x86_64.rpm: Header V4 RSA/SHA1 Signature, key ID 86a998db: NOKEY
warning: synology-cloud-station-3.2-3487.x86_64.rpm: Header V4 RSA/SHA1 Signature, key ID 86a998db: NOKEY
warning: synology-cloud-station-3.2-3487.x86_64.rpm: Header V4 RSA/SHA1 Signature, key ID 86a998db: NOKEY
warning: synology-cloud-station-3.2-3487.x86_64.rpm: Header V4 RSA/SHA1 Signature, key ID 86a998db: NOKEY
warning: synology-cloud-station-3.2-3487.x86_64.rpm: Header V4 RSA/SHA1 Signature, key ID 86a998db: NOKEY
warning: synology-cloud-station-3.2-3487.x86_64.rpm: Header V4 RSA/SHA1 Signature, key ID 86a998db: NOKEY
warning: synology-cloud-station-3.2-3487.x86_64.rpm: Header V4 RSA/SHA1 Signature, key ID 86a998db: NOKEY
Warning: Skipping conversion of scripts in package synology-cloud-station: postinst postrm prerm
Warning: Use the --scripts parameter to include the scripts.
warning: synology-cloud-station-3.2-3487.x86_64.rpm: Header V4 RSA/SHA1 Signature, key ID 86a998db: NOKEY
    dpkg --no-force-overwrite -i synology-cloud-station_3.2-3488_amd64.deb
(Reading database ... 163690 files and directories currently installed.)
Preparing to unpack synology-cloud-station_3.2-3488_amd64.deb ...
prerun called with unknown arguemnts 'upgrade'
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: error processing archive synology-cloud-station_3.2-3488_amd64.deb (--install):
there is no script in the new version of the package - giving up
post called with unknown arguemnts 'abort-upgrade'
dpkg: error while cleaning up:
subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
synology-cloud-station_3.2-3488_amd64.deb
Unable to install at /usr/share/perl5/Alien/Package/Deb.pm line 92, <GETPERMS> line 42.
    find synology-cloud-station-3.2 -type d -exec chmod 755 {} ;
    rm -rf synology-cloud-station-3.2

sudo apt-get -f remove synology-cloud-station_3.2-3488_amd64.deb 
[sudo] password for chelle: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package synology-cloud-station needs to be reinstalled, but I can't find an archive for it.





sudo apt-get -f installReading package lists... Done
Building dependency tree 
Reading state information... Done
E: The package synology-cloud-station needs to be reinstalled, but I can't find an archive for it.
```

---

### Post by bapoumba on 2015-10-11
Have you tried with dpkg ?
```
sudo dpkg -P synology-cloud-station
```

There are harsher options with dpkg (see man dpkg for the remove-reinstreq option).

---

### Post by Devon_suz on 2015-10-12
I tried it and the result is below, unfortunately I got the same result 

 sudo dpkg -P synology-cloud-station
[sudo] password for : 
dpkg: error processing package synology-cloud-station (--purge):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
Errors were encountered while processing:


sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package synology-cloud-station needs to be reinstalled, but I can't find an archive for it.

---

### Post by slickymaster on 2015-10-12
*Moved to the ***MINT*** sub-forum*

---

### Post by Devon_suz on 2015-10-12
[COLOR=#111111][FONT=Ubuntu]This is what seemed to have worked, I found this in a 2011 post.

from 
[http://askubuntu.com/questions/602276/the-package-jre1-8-0-40-needs-to-be-reinstalled-but-i-cant-find-an-archive-forThe](http://askubuntu.com/questions/602276/the-package-jre1-8-0-40-needs-to-be-reinstalled-but-i-cant-find-an-archive-forThe) following worked for me (I had the same problem), I hope it works for you, I got the instructions for other packages with the same error:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Make a backup of /var/lib/dpkg/status with:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.bkup[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Then open /var/lib/dpkg/status with:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]sudo nano /var/lib/dpkg/status[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]and search through the file for any reference to that package name (i.e. jdk1.8.0-40) and CAREFULLY delete that entry. Don't delete anything else. Save the file and quite.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Then run sudo apt-get update.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]This should solve your the problem.[/FONT][/COLOR]

---

### Post by bapoumba on 2015-10-12
Hmm, not the same symptoms and error messages from your link, thus may be not the best way to fix this. The status file lists the files that are installed. Removing one entry as you did may fool the package managers having them think things are ok but you still have the bits installed here and there. I would have tried dpkg with the remove-reinstreq option first.

If anything happens to your install in the future, please remember this thread and what you did.

Now, please do not get me wrong, glad to see you are back up and running :)

---

