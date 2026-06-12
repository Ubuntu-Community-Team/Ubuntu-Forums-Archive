---
title: "[SOLVED] Want to run CD require Windows Game on Linux"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by Ralph L on 2008-01-25
I have a game for that must be run with the CD in the drive.  I would like to run it under Linux.  To allow the game to run under windows without have the CD in the drive I installed Virtual CD.  Is there any similar capability in Linux that would allow me to run the game without having the CD in the drive.

---

### Post by yabbadabbadont on 2008-01-25
cdemu claims to provide this support, but I never managed to make it work.  Others have had some success with it though.  It at least gives you a place to start looking.  ;)

---

### Post by mcduck on 2008-01-25
Copying the disk into image and then mountintg that image through loop-back should work in most cases.

```
sudo mount -o loop -t iso9660 foo.iso /media/cdrom
```

There's also a  GUI tool for mounting images so you don't need to do it from command line: [http://onlyubuntu.blogspot.com/2007/12/gmount-iso-is-small-tool-written-using.html]("http://onlyubuntu.blogspot.com/2007/12/gmount-iso-is-small-tool-written-using.html")

---

