---
title: "After karmic update, login prompt goes into recovery m ode"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ittiam on 2009-10-23
As suggested in the title, after karmic update the login prompt goes straight into character interface.

This is what happened after karmic update
1) Asked me to reboot
2) Then it said UUID wrong in fstab, could not mount drive or something. Told me to hit ESC to continue. I hit ESCAPE it went into recovery mode which is the character interface
3) There I login, then start gdm/kdm manually, then it works and takes me to the GUI.

While trying to start gdm manually,

```
sudo service gdm start 
```

does not work.

But 

```
sudo gdm
```

works and  gets me into gnome login screen.

But why does during start up does it go straight to recovery console?

---

### Post by ittiam on 2009-10-24
The same happens using kdm as well. I see there is a bug in launchpad regarding this:

```
WARNING: Unable to find users: no seat-id found  
```

[https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/433928](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/433928)

But I guess that was fixed before the release of karmic. I see this warning whenever I run

```
sudo gdm
```

but gdm starts fine with this command. 

There is some problem during boot up. I am not even able to get logs regarding this. I enabled bootlogd but /var/log/boot is empty.

Any other ideas?

---

### Post by ittiam on 2009-10-24
This is the error I get during boot

```

(ESC for recovery shell)
/: waiting for /dev/disk/by-uuid/6b1dd640-04f1-4f3c-ab91-a537f60841d1
/tmp: waiting for (null)
```

I tried the solution posted [here]("http://newyork.ubuntuforums.org/showthread.php?t=1297318") but it does not work for me.

---

### Post by nerdy_kid on 2009-10-24
I have had the same issues; to fix the boot, boot from an old kernel and run sudo update grub.  As for login, try dpkg-reconfigure gdm.

---

