---
title: "xubuntu USB cant access core applications"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by ptewee on 2008-04-02
i have been using my xubuntu on my 4GB pendrive for a few weeks.. then recently i followed a thread in the forums teaching you how to install chinese input...

after that, i restart my xubuntu, but then, when i login with my username and pword, i am greeted with a window saying that my session only lasted 10 seconds, and a 'input/output' error in the details...

i booted into the usb xubuntu, but in live mode (not persistent) to load the clean disc image, eveything functions properly, so i replaced my xorg.conf and .ICEauthority on my casper-rw, since there are some threads saying that this will work, but then i was still stuck...

a few reboots later i could login to my desktop, with my username and pword, but a few icons (casper-rw, xubuntu710-where i copied the files from the cd) were missing, and the system tray doesnt show the network icon, which should have been autostarted (rechecked in auto started applications)

by going through the Applications > System > Network, it says that i cannot access it because i dont have the privilege... so i relogin with root, but still doesnt work... (same with other core applications such as synaptic too)

anyway, the quit button at the right end of the top panel works as 'quitting the xfce panel' instead of the whole session, and the quit button located inside the Application menu does not work at all (doesnt do anything when clicked)

i have tried loads and loads of solutions but to no avail (there's a solution which recommended me to reinstall dbus, but i cant get into synaptic, not to mention the internet [without the network] so i cant do anything!!

pls help and i would say thank you 1st in advance

---

### Post by PmDematagoda on 2008-04-02
Perhaps you ran out of space on the USB drive, please post the output of:-
```
df
```

---

### Post by ptewee on 2008-04-03
ah.. im sorry i will be outstation for the next 4 days so i wont be able to check it now... will update this thread next week, and also the result of 'df'...

---

### Post by ptewee on 2008-04-08
ok i did it but i got a weird output:

```
phailure@ubuntu:~# df
df: cannot read table of mounted file systems: Input/output error
phailure@ubuntu:~# sudo df
df: cannot read table of mounted file systems: Input/output error
phailure@ubuntu:~# gksudo df
phailure@ubuntu:~# 
```

1st was my user (root privileges), then sudo, then gksudo (no output)

same thing when using root account

```
root@ubuntu:~# df
df: cannot read table of mounted file systems: Input/output error
```

---

### Post by PmDematagoda on 2008-04-08
It looks like the USB drive has failed.

Did you try plugging the USB drive to another PC with Linux on it and tried to read it?

Also, post:-
```
sudo fdisk -l
```

---

