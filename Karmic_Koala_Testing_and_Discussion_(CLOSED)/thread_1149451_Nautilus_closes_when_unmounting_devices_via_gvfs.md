---
title: "Nautilus closes when unmounting devices via gvfs"
date: 2009-05-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by taavikko on 2009-05-05
G'day mates, anyone else?
Logs show no entry for this behaviour, neither doesn't nautilus crash just filebrowser window closes.

This also happens when using BT (obex)
So seems to be related to gvfs.

Window doesn't close when inserting USB-stick and umounting it.

Main comp act's as a server(9.04 + KDE)

Using nautilus -> connect to server -> ssh (sftp)
```
taavikko@hp-dv5:~$ ls -l .gvfs/
total 4
drwx------ 1 taavikko taavikko 4096 2009-03-31 19:38 sftp for devil on 192.168.0.100
taavikko@hp-dv5:~$ gvfs-mount -u .gvfs/sftp\ for\ devil\ on\ 192.168.0.100/
taavikko@hp-dv5:~$ ls -l .gvfs/
total 0
taavikko@hp-dv5:~$ 
```

Doesn't work either when umounting via nautilus-> sidepanel-> umount icon

Definitely unwanted behaviour, could someone confirm that this happens on 9.04 also?

---

### Post by taavikko on 2009-05-09
Funny, few restarts seems to solved this behaviour.

Other thing, while using nautilus menu to "connect to server"
it spawns another windows. Searched around gconf for setting to change this, but there's not one. (this is been this way as long as I can remember)
But seems rather pointless it to open a new one, when one is already open.

Comments, opinions?

---

### Post by Locke_99GS on 2009-05-09
I haven't experienced that one, but gphoto2 crashes my nautilus as desktop every time when retreiving thumbnmails form my camera.

---

