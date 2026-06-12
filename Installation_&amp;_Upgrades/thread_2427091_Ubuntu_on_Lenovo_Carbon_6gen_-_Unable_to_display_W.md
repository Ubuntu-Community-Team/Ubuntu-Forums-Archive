---
title: "Ubuntu on Lenovo Carbon 6gen - Unable to display Windows login option"
date: 2019-09-17
forum: Installation &amp; Upgrades
---

### Post by ro7ca on 2019-09-17
[SIZE=2]Hi,

I am new to ubuntu, after installing it (along to Windows 10) on a new laptop. When I didn't see the option at start, I received the link after my failed attempt to fixing it:[/SIZE]
[SIZE=3] 
[/SIZE][SIZE=3]http://paste.ubuntu.com/p/7R4yNMZP8B/[/SIZE]

   
At the current startup, in addition to Ubuntu, I also have the following:
- Windows UEFI recovery booth 
- Windows Boot UEFI recovery
- Windows Boot UEFI fbx64.efi
- Windows Boot Manager (on dev/neonpit1)


Is there anything I can do to get windows back?

---

### Post by ro7ca on 2019-09-20
Any help here? I trying to find a way to login to windows...

---

### Post by oldfred on 2019-09-21
Can you directly boot Windows from Lenovo UEFI boot menu.
Depending on model, one of these keys:             Lenovo - F8, F10, F12 

Check that fast start up is off, as that sets hibernation flag and then Linux NTFS driver cannot see the NTFS partition(s).
      
 Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions) &

---

