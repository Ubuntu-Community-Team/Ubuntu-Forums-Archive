---
title: "Ubuntu doesn't load due to $HOME access error"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by studiesrule on 2006-11-05
I have just completed a otherwise successful install of Edgy. I have a special /home partition, as I shuffle through distros. I also have made a /boot partition (residue from FC6). The startup screen successfully loads but displays the following error:
Unable to load $HOME/.dpms

It also mentions the $HOME should be set to id 684 (I think), and that the permissions are not properly set. "Owner should own $HOME and no other user should be able to write". After this window, another one pops ups saying error at: "Setting id 700". Perhaps there is a conflict here.

What should I do now?

---

### Post by hearnden on 2006-11-05
So what are the permissions of $HOME for that particular user?  Are they not compatible with those messages?

755 (i.e. rwxr-xr-x) is quite common, as is 700 (rwx------).

---

### Post by studiesrule on 2006-11-05
I'm not sure, help on how to check and change would be in order.

---

### Post by hearnden on 2006-11-05
If you can get a Live CD or any kind of Linux or Ubuntu environment running, then you can check the file permissions on $HOME by

1.  Mount the partition with your home directories on it

e.g.

```

$ sudo mkdir /mnt/hd
$ sudo mount /dev/sda3 /mnt/hd

```

Where /dev/sda3 is the partition with your HOME on it.

2.  Type 'ls -ld /mnt/hd/xxx' where xxx is the home directory.  If your user is 'bob', then this might be /mnt/hd/home/bob, or it might be /mnt/hd/bob if that partition is a dedicated home partition (i.e. usually mounted at /home).

3.  If the permissions are something weird, then set them to something sensible with:

```

$ chmod 700 /mnt/hd/home/bob

```

Sensible permissions would be at least rwx------.

However, that might be the long way.  Does booting in recovery mode help?  If you can get a login prompt (non-graphical), then you can always log in as root and fix things, if you know the root password.

---

### Post by studiesrule on 2006-11-05
ok. shall try

---

### Post by studiesrule on 2006-11-05
That didn't work, so i reinstalled, this time without a seperate home partition. Things are working smoothly.

---

