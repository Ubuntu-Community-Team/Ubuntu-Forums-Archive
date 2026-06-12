---
title: "libgksu bungled! can't update nautilus/gnome related packages!"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by ridetheteapot on 2008-02-28
heres what dpkg tells me when i try to update nautilus-data

> 
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/10_libgksu'
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/10_libgksu'
dpkg: error processing /var/cache/apt/archives/nautilus-data_1%3a2.20.0-0ubuntu7_all.deb (--install):
 subprocess new post-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/sbin/update-gconf-defaults", line 118, in <module>
    read_entries(realname)
  File "/usr/sbin/update-gconf-defaults", line 100, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/10_libgksu'
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/nautilus-data_1%3a2.20.0-0ubuntu7_all.deb


I have a feeling something happened at the same time i lost all my man pages [my man page thread]("http://ubuntuforums.org/showthread.php?t=708958")

i have triedd reinstalling libgksu (tried all version cause i don't know which it was angry about) --- but when trying to reinstall i get the same error. Is there an order that i should try to reinstall some packages to get this sorted out? I havent got a clue what happened.... I ran fsck on startup yesterday to see if something happened to the drive, but i didnt get any foul report.
This is a laptop and i think that the battery ran out a few days ago, and it didnt automatically shutdown prior, but still fsck didnt get mad... and i havent noticed any other missing data as far as documents go.

---EDIT

Well with my trackrecord on replies to my thread, this is pretty rhetorical, but never mind, the whole harddrive in swisscheese now. all kinds of crazy weird things are going on(but all said i can still manage to use the system), its time for a format, and reinstall (maybe check out gentoo).
the thing thats oddest of all is that fsck never picked anything up, im just losing random files each reboot... and putting /fsck is not running it on reboot anymore...

---

