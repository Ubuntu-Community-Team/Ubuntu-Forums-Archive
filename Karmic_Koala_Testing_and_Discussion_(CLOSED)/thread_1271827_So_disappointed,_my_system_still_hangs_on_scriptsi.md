---
title: "So disappointed, my system still hangs on scripts/init-bottom after update"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by carfield on 2009-09-21
I think it is like caused by following bugs

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432901](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432901)
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/432275](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/432275)

Just run update again, however, after restart, not only the computer cannot start (again) . The worse part is I cannot start my system by update grub attribute to "rw /bin/bash" to just start the computer for recovery....

It really so disappointed....

---

### Post by VMC on 2009-09-21
> **carfield said:**
> I think it is like caused by following bugs

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432901](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/432901)
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/432275](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/432275)

Just run update again, however, after restart, not only the computer cannot start (again) . The worse part is I cannot start my system by update grub attribute to "rw /bin/bash" to just start the computer for recovery....

It really so disappointed....

Did you try to just add "single" at the end of the kernel line(no quotes), then Ctrl+x to boot.

---

### Post by carfield on 2009-09-21
> **VMC said:**
> Did you try to just add "single" at the end of the kernel line(no quotes), then Ctrl+x to boot.

It doesn't help... however, I can login after change to "rw init=/bin/bash" ... sorry, I make mistake...

---

### Post by verb3k on 2009-09-21
I got the same error after the update and now can't boot the system.

It says something about /scripts/init-bottom and udev errors

 Can anyone help?

---

### Post by shakaran on 2009-09-22
I filled a bug, for me it don't solved.
[https://bugs.launchpad.net/bugs/433943](https://bugs.launchpad.net/bugs/433943)

---

### Post by JCoster on 2009-09-22
This happened to me after the update cock-up last wednesday/thursday and the only fix i found was a reinstallation..
I understand that this isn't what you wanted to hear, but the general concensus then was that it was something which happened in the update process which couldn't be fixed in another update (the fix of the upstart package).

---

### Post by shakaran on 2009-09-22
I find a solution:

1. - Download/grab a live cd.

2. - Start live cd and when it loads the desktop open a gnome-terminal.

3. - Create this dirs:

```
sudo mkdir /media/karmic
sudo mkdir /media/karmic/proc /media/karmic/dev /media/karmic/etc
```

4. - Mount your linux partition (for me sda6):
```
sudo mount /dev/sda6 /media/karmic
```

5. - Bind the dirs:
```
sudo mount -o bind /proc /media/karmic/proc
sudo mount -o bind /dev /media/karmic/dev/
sudo mount -o bind /dev/pts /media/karmic/dev/pts
```

6. - Copy this file
```
sudo cp /etc/resolv.conf /media/karmic/etc/resolv.conf
```

7. - Update your real linux partition with chroot:
```
sudo chroot /media/karmic apt-get update
```

8. - Upgrade your real linux partition with chroot:
```
sudo chroot /media/karmic apt-get dist-upgrade
```

9. - If you have some broken package:
```
sudo chroot /media/karmic apt-get -f install
```

10. - Reboot and voilá! Fixed for me.

---

