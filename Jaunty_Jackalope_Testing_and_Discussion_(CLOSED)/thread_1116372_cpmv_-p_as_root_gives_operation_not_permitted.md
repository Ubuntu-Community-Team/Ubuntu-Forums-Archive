---
title: "cp/mv -p as root gives operation not permitted?"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ajmcello on 2009-04-04
root@sumwhere# cp -p test.txt /tmp
cp: preserving permissions for `/test.txt': Operation not supported

Why does this happen? It does copy but causes scripts to bomb out because it returns an error status.

---

### Post by ajmcello on 2009-04-06
It looks like it might have something to do with NFS and jaunty only, but it only occurs on the client side of an NFS mount with jaunty. gutsy or feisty don't have this issue with the same NFS server.

When I look at the files and directories on the NFS share on jaunty they all end with a "+" after the modes (drwxr-xr-x+ for example). Any of these files or directories will fail when trying to cp or mv with --preserve=mode.

I do have root_squash turned off on the NFS server and all the UIDs are mapped properly, but I am working as UID root.

Anybody have any ideas?

---

