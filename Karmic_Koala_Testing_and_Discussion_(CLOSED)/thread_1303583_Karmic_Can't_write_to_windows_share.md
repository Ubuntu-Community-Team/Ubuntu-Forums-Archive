---
title: "Karmic: Can't write to windows share"
date: 2009-10-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bryceowen on 2009-10-28
I have a laptop running Jaunty and a workstation running the Karmic build from Monday and I'm having a small problem trying to connect to a share on an XP machine.

I run the same command on both the laptop and the workstation:
```

sudo mount -t cifs -o username=*****,password=***** //192.168.xxx.xxx/share /mnt/win

```
On the laptop (jaunty), it connects, I'm able to read, write, and delete files with no problem. On the workstation (karmic), I can read, but nothing else. Can anyone tell me what I'm doing wrong?

EDIT:
Turns out, I needed to add file_mode=0777,dir_mode=0777 to the option argument.

EDIT:
O.K., so from the command line, I can run:
```

sudo mount -t cifs -o rw,username=*****,password=*****,file_mode=0777,dir_mode=0777 //192.168.xxx.xxx/share /mnt/win

```
And I'm able to edit, delete, write, etc as any user (not just root or sudo). HOWEVER, if I add the line:
```

//192.168.xxx.xxx/share /mnt/win cifs rw,username=*****,password=*****,file_mode=0777,dir_mode=0777 0 0

```
to my fstab, the share fails to mount the same way and I can't make changes to files as a regular user.

---

