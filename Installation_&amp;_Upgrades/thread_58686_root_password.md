---
title: "root password"
date: 2005-08-21
forum: Installation &amp; Upgrades
---

### Post by Lord Hammer on 2005-08-21
Just installed Ubuntu from the free CD (new to Linux).

During install I was asked for the user name and password. That works OK for "normal user".

Now I wont to install nVidia driver an to do that I have to be logged in as a root.

When I try to do that it replies that user password is incorrect. During installation I have to enter only one password.

Is there a way to find out this root password (standard root ?).

If I compare  an installation with WinXP during install I have to provide two passwords; administrator and user. Here I have provided only one.

If I have to reinstall the whole thing, where and how I have to enter the root password.

Thanks

---

### Post by adwait on 2005-08-21
In Ubuntu there is no root account. Whenver you need root access for a particular command, you can use sudo. eg, if you want to run reboot, you would use
```
sudo reboot
```

EDIT: The password is your normal user password.

---

### Post by Lord Hammer on 2005-08-21
[QUOTE=adwait]In Ubuntu there is no root account. Whenver you need root access for a particular command, you can use sudo. eg, if you want to run reboot, you would use
```
sudo reboot
```

EDIT: The password is your normal user password.[/QUOTE]
 Thanks.

This works. But now the second problem arises.

How to stop the X Server ?

P L E A S E Help

---

### Post by twelvegates on 2005-08-21
[QUOTE=Lord Hammer]
Is there a way to find out this root password (standard root ?).[/QUOTE]

I guess there is no way to find out the root password. However you may set a new one.
Reboot. At the Grub menu press 'c' and enter command mode.
```
root (hdX,Y)
kernel  /boot/vmlinuz-2.6.10-5-386 root=/dev/hdaZ ro quiet splash -s
initrd  /boot/initrd.img-2.6.10-5-386
boot
```
Adjust (hdX,Y) and /dev/hdZ to your environment.

Ubuntu should then boot into single user mode and offer the shell prompt.
There you may enter
```
passwd root
```

-Hanspeter

---

### Post by adwait on 2005-08-21
To stop the X Server, press Ctrl + Alt + Shift + F1 (or if that doesn't work, omit the shift.....I can't remember properly :) ). That will switch you to a virtual terminal. Login using your normal username and password. To stop the X Server use:
```
sudo killall gdm
```

If you want to restart the X Server now, you you
```
sudo /etc/init.d/gdm start
```

When the X Server is already running, you can directly restart by pressing Ctrl + Alt + Backspace.

---

### Post by krazikamikaze on 2005-08-22
An easier way to change the root password is probably:
```
$ sudo su
<Enter your regular passwod>
# passwd
<Enter your new root password>
```
I've never done it before, but it seems like it should work.

---

### Post by noisey_mouse on 2005-08-22
\\:D/  thank you very much  \\:D/  
i had been trying to figure that out ... read your post
tried it .... and low and behold root access

 :grin:

---

