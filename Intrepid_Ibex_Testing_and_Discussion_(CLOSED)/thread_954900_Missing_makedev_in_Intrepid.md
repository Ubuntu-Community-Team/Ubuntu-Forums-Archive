---
title: "Missing makedev in Intrepid"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by trusty on 2008-10-21
I have been having problems installing my webcam.
> 
[FONT="Courier New"][SIZE="1"][B]Creating video4linux (/dev/video*) special files...
udev active, devices will be created in /dev/.static/dev/
rm: cannot remove `video0-': Read-only file system
mknod: `video0-': Read-only file system
makedev video0 c 81 0 root video 0660: failed
rm: cannot remove `video0-': Read-only file system
rm: cannot remove `radio0-': Read-only file system
mknod: `radio0-': Read-only file system
makedev radio0 c 81 64 root video 0660: failed
rm: cannot remove `radio0-': Read-only file system
rm: cannot remove `video1-': Read-only file system
mknod: `video1-': Read-only file system
makedev video1 c 81 1 root video 0660: failed
rm: cannot remove `video1-': Read-only file system
rm: cannot remove `radio1-': Read-only file system
mknod: `radio1-': Read-only file system
makedev radio1 c 81 65 root video 0660: failed
rm: cannot remove `radio1-': Read-only file system
rm: cannot remove `video2-': Read-only file system
mknod: `video2-': Read-only file system
makedev video2 c 81 2 root video 0660: failed
rm: cannot remove `video2-': Read-only file system
rm: cannot remove `radio2-': Read-only file system
mknod: `radio2-': Read-only file system
makedev radio2 c 81 66 root video 0660: failed
rm: cannot remove `radio2-': Read-only file system
rm: cannot remove `video3-': Read-only file system
mknod: `video3-': Read-only file system
makedev video3 c 81 3 root video 0660: failed
rm: cannot remove `video3-': Read-only file system
rm: cannot remove `radio3-': Read-only file system
mknod: `radio3-': Read-only file system
makedev radio3 c 81 67 root video 0660: failed
rm: cannot remove `radio3-': Read-only file system
rm: cannot remove `video4-': Read-only file system
mknod: `video4-': Read-only file system
makedev video4 c 81 4 root video 0660: failed
rm: cannot remove `video4-': Read-only file system
rm: cannot remove `radio4-': Read-only file system
mknod: `radio4-': Read-only file system
makedev radio4 c 81 68 root video 0660: failed
rm: cannot remove `radio4-': Read-only file system
rm: cannot remove `video5-': Read-only file system
mknod: `video5-': Read-only file system
makedev video5 c 81 5 root video 0660: failed
rm: cannot remove `video5-': Read-only file system
rm: cannot remove `radio5-': Read-only file system
mknod: `radio5-': Read-only file system
makedev radio5 c 81 69 root video 0660: failed
rm: cannot remove `radio5-': Read-only file system[/B][/SIZE][/FONT]

The package manager appears to be unable to make the video* devices.

It seems that makedev is missing.

Should makedev still be a part of the Intrepid package?  

(the answer should be yes) 

If yes, any idea where mine went to? On holidays perhaps?

Recommendations?
> 
[FONT="Courier New"][SIZE="1"][B]root@tightun:~# find / -name makedev -print
/usr/share/doc/makedev
/usr/share/lintian/overrides/makedev[/B][/SIZE][/FONT]
> 
[FONT="Courier New"][SIZE="1"][B]root@tightun:~# which makedev
root@tightun:~#[/B][/SIZE][/FONT]


---

