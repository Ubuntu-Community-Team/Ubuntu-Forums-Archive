---
title: "NTFS drive: Permissions / Restrict user access"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by sunside on 2008-02-23
Hi there.

I am quite new to Linux and Ubuntu. I used it several times now in my university and at home, but usually for not more than some hours, then switching back to Windows, and now I have decided to give it a serious try.

I am basically running a somewhat fresh installation Ubuntu 7.10. (Of course I played around a bit, so it's not really out-of-the-box anymore)

Since I come from Windows XP, I have plenty of NTFS partitions here. Most of them are on external USB HDDs. I already installed ntfs-3g and thus have read and write access to them. They get properly mounted on start-up.

I want to set up an multiuser environment but have, of course, sensitive data on the NTFS partitions which I do not want to be seen by every user. In fact, I do not want most of the drive to be seen by anyone but me (or root-likes). Then again, there are some folders I want to be readable by everyone - mp3s, photos, etc. -, and they should also act as a Samba share later, if possible. (That's of no priority now)

(edit: this part of the problem is solved)
Now the NTFS drives are mounted and owned by root, so I cannot change the access permissions. All the boxes are greyed out (using Nautilus, extended permissions enabled). 

(edit: this part is **not**)
I tried chmod, chown, chgrp from a root console and nothing happens (no error whatsoever, but no effect either).

I have read that there is some user right management in  /etc/fstab, but I did not fully understand it, so I didn't touch anything there.

Any help is appreciated!
Best wishes from Berlin,
Markus

---

### Post by Pumalite on 2008-02-23
Try:
sudo nautilus

---

### Post by sunside on 2008-02-23
sudo nautilus unlocked the boxes, but the effect remains the same: As soon as I make a selection in the boxes, the value switches back to what it was before. (This is somewhat like the effect I saw in the terminal: No error, but also no change)

---

### Post by Pumalite on 2008-02-23
You might want to try:
sudo chmod 777 /media/???
Where ??? has to be changed by you to what is appropriate.

---

### Post by lswest on 2008-02-23
what you can do, if you have a complete drive that you don't want to be seen or accessed by other users you can change the permissions of the mount-point (e.g. /media/sda1) and otherwise...not sure on the problem with the permissions on the actual drive, i'll play around with my external HDD later (kinda late now ~8pm in Germany, so i'll take a crack at it tomorrow if it's not been solved by then)

---

### Post by sunside on 2008-02-23
Tried that, but without success. First I chmodded/chowned the mountpoint while the drive was mounted (no error, no success). When I unmounted the drive the mountpoint had different permissions (the defaults: read and execute for everyone, but no write); I changed them, but when I remounted the drive, everything was like before: All root, full access for everyone.

Another problem is that I cannot change the mountpoints of the USB drives, since they - let's say, /media/drivename - don't exist until I (auto)mount the drive. I haven't created the directory since I fear the result would be the same.

Markus

---

### Post by Pumalite on 2008-02-23
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[http://ubuntuforums.org/showthread.php?t=589909](http://ubuntuforums.org/showthread.php?t=589909)

---

### Post by sunside on 2008-02-23
Thanks for the links, Pumalite, but I'm not sure if they help me. I just learned the "gksudo" command thanks to them, but that didn't help me out.

Here are some more information from my current setup. This is the /media folder as it looks right now.

```

lrwxrwxrwx 1 root    root     6 2008-02-20 04:32 cdrom -> cdrom0
drwxr-xr-x 2 root    root  4096 2008-02-20 04:32 cdrom0
drwxrwxrwx 1 root    root  8192 2008-02-23 08:41 hda1
drwxrwxrwx 1 root    root  8192 2008-02-22 01:05 hdb1
drwxrwxrwx 1 root    root 28672 2008-02-17 04:25 hdb5
drwxrwxrwx 1 root    root 16384 2008-02-23 11:45 hdb6
drwx------ 6 sunside root 16384 1970-01-01 01:00 HSC
drwxrwxrwx 1 root    root 16384 2008-02-17 04:25 Vista
drwxrwxrwx 1 root    root  8192 2008-02-17 04:25 X200
drwxrwxrwx 1 root    root  8192 2008-02-22 04:10 X3
```

Everything there, except for cdrom and HSC is NTFS. I addition, everything that has a "real" name is an external USB drive.

My **/etc/fstab** looks like this, in case this is of any help.

```

# Entry for /dev/hda2 :
UUID=c75e37d6-6c8d-4c14-9dd5-e142fbca82ea / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda1 :
UUID=0274470F7447053F /media/hda1 ntfs-3g defaults,locale=de_DE.UTF-8 0 1
# Entry for /dev/hdb1 :
UUID=78B0A386B0A34A08 /media/hdb1 ntfs-3g defaults,locale=de_DE.UTF-8 0 1
# Entry for /dev/hdb5 :
UUID=B2EC1F50EC1F0DEB /media/hdb5 ntfs-3g defaults,locale=de_DE.UTF-8 0 1
# Entry for /dev/hdb6 :
UUID=36C0DBC6C0DB8B0F /media/hdb6 ntfs-3g defaults,locale=de_DE.UTF-8 0 1
# Entry for /dev/hda5 :
UUID=7a5fafff-865e-4b9e-b84c-c744c5237785 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
```

Here's an example to make the scenario a bit clearer:

[LIST]
[*] **/hdb1** should be only accessable for me.
[*] **/hdb1/photos/** should be accessable by anyone.
[/LIST]

So much for the idea behind it - but as I said, I am not able to change the permissions without sudo (okay, I understand that), but *when* I am able to change them - using **gksudo nautilus**, for example, or using **sudo mc** in the shell - the settings are *reverted automatically* or ultimately when I confirm the dialog. (Forgot to mention: I tried to change the permissions of /media/hdb1 and of folders and files down there.)

(Is this maybe because NTFS drives cannot handle unix permissions or stuff? I have read something like that somewhere, but this was related to a Ubuntu 5 topic.)

Markus

---

### Post by cherry316316 on 2008-02-24
check my post here

[http://ubuntuforums.org/showthread.php?p=3855335#post3855335](http://ubuntuforums.org/showthread.php?p=3855335#post3855335)

one update, i don't use any more "exec" option, so in all u can also remove the "exec" option.

good luck

---

### Post by sunside on 2008-02-24
Thanks for the hint, cherry316316.

According to that I changed a line (to test it, first) in fstab from:

```
UUID=36C0DBC6C0DB8B0F /media/hdb6 ntfs-3g defaults,locale=de_DE.UTF-8 0 1
```

to 

```
UUID=36C0DBC6C0DB8B0F /media/hdb6 ntfs-3g auto,rw,locale=de_DE.UTF-8,uid=1000,umask=000,sync 0 1

```

Now if I get that right, this means that the owner is user #1000 (whis is me) and that everyone is rwx (well, if I got that right that umask is the opposite of these chmod flags). When I unmount and then remount the drive (using sudo mount -a), everything is indeed so (the owner being me, everything switched on) - but I still cannot change the values. 
They pop back as soon as I touch them. (I tried on the drive's root directory as well as on files and folders down there, but nada). Altering the permissions of the mount point itself doesn't have any effect either. :(

So I am able to lock everyone out (which is a good starting point), but I am still not able to allow users to access certain directories on the drive.

Thanks so far!
Markus

---

