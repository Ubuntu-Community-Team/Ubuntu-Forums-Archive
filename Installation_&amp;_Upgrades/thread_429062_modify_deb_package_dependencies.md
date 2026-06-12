---
title: "modify deb package dependencies?"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by khughitt on 2007-04-30
Anyone know if there is any easy way to modify the requirements for a debian package?
I'm trying to install [http://reconstructor.aperantis.com/]("http://reconstructor.aperantis.com/") using a deb package provided on it's homepage, however it will not install because of a missing dependency (usplash-dev). I check aptitude, and found that usplash-dev has been superceded by libupslash-dev, so i downloaded that instead, but the package still won't install. When i opened up the .deb file with archive manager, i found the file that lists the package requirements, but i havn't been able to modify it.. i tried extract everything, changing the file, and re-zipping as a .tar.gz file, then renaming to .deb, but that didn't work either.

Any ideas? I'm sure i can get it to install using the tarball instead, but would still be helpful to know..
Thanks!

---

### Post by engla on 2007-05-01
I've successfully done that once. I don't remeber exactly but I did just like you did. Take note that a .deb is an archive that contains two archives, and that has to be preserved..

---

### Post by nfoti on 2007-05-01
there is a post on reconstructor forums explaining how to install in Feisty (i believe thats what you are trying to do) .

[http://reconstructor.aperantis.com/index.php?option=com_joomlaboard&Itemid=&func=view&catid=3&id=335#335]("http://reconstructor.aperantis.com/index.php?option=com_joomlaboard&Itemid=&func=view&catid=3&id=335#335")

that should get you rolling. You just need to edit /var/lib/dpkg/status, find reconstructor, and edit our usplash-dev

---

### Post by khughitt on 2007-05-04
Thanks. I was able to install it manually using the tarball. I'm just curious about how Debian files are saved and compressed, and what i would need to do to recompress one.

---

