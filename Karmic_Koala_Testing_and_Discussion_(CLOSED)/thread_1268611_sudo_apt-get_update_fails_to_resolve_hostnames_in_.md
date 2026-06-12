---
title: "sudo apt-get update fails to resolve hostnames in chroot"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by JCoster on 2009-09-17
Yet another problem...  Since I can't boot at the moment for another reason, I'm stuck with getting into my Karmic install via chroot from the live CD.

However, attempting to run "sudo apt-get update" gives me errors about not being able to resolve hostnames, so this implies that there is a problem with internet connectivity.  However, I can browse the web on Firefox on the live CD and ping successfully from the chroot. 

Also, running "sudo apt-get upgrade" connects fine and informs me that there are no packages which require upgrade.

Aptitude also fails to resolve hostnames.

Why is this?

And as a quick side-question, what's the difference between "apt-get update" and "apt-get upgrade"?

Cheers

---

### Post by Wise Ferret on 2009-09-17
1. I also experienced connectivity problems trying to use apt-get in chroot. It was solved using the instructions in comment #3 here: [http://ubuntuforums.org/showthread.php?t=1268160](http://ubuntuforums.org/showthread.php?t=1268160)

2. apt-get update downloads the information about latest package versions and dependencies. apt-get upgrade downloads the necessary packages and installs them. Generally it is better to use apt-get dist-upgrade, as it works more responsibly with partial upgrades and is less likely to break your system.

---

### Post by JCoster on 2009-09-17
> **Wise Ferret said:**
> I also experienced connectivity problems trying to use apt-get in chroot. It was solved using the instructions in comment #3 here: [http://ubuntuforums.org/showthread.php?t=1268160](http://ubuntuforums.org/showthread.php?t=1268160)

I take it you mean by running:? ```
sudo aptitude update && sudo aptitude full-upgrade
```

Cheers, I'll give it a go when i get home..

> **Wise Ferret said:**
> apt-get update downloads the information about latest package versions and dependencies. apt-get upgrade downloads the necessary packages and installs them.

Does this mean that an "apt-get upgrade" won't be up-to-date without a successful "apt-get update" preceeding it? 

Thanks for your help.

---

### Post by sisco311 on 2009-09-17
how did you chroot?

```

mount /dev/sda2 /mnt/karmic
mount -t sysfs none /mnt/karmic/sys
mount -t proc none /mnt/karmic/proc
mount --bind /dev/ /mnt/karmic/dev
mount --bind /dev/pts /mnt/karmic/dev/pts
mount -o bind /etc/resolv.conf /mnt/karmic/etc/resolv.conf
chroot /mnt/karmic

```

EDIT: never mind.

---

### Post by JCoster on 2009-09-17
Yeah I've been following the same instructions I've used previously back when the hostnames could be resolved...

---

### Post by sisco311 on 2009-09-17
> **JCoster said:**
> Yeah I've been following the same instructions I've used previously back when the hostnames could be resolved...

after chrooting into karmic try to change the hostname:
```
hostname $(cat /etc/hostname)
```

---

### Post by philinux on 2009-09-17
> **sisco311 said:**
> how did you chroot?

```

mount /dev/sda2 /mnt/karmic
mount -t sysfs none /mnt/karmic/sys
mount -t proc none /mnt/karmic/proc
mount --bind /dev/ /mnt/karmic/dev
mount --bind /dev/pts /mnt/karmic/dev/pts
mount -o bind /etc/resolv.conf /mnt/karmic/etc/resolv.conf
chroot /mnt/karmic

```

EDIT: never mind.

I've not had trouble with chroot but I used this, not sure if it would make any difference.
```
cp /etc/resolv.conf /mnt/etc/resolv.conf
```

---

### Post by sisco311 on 2009-09-17
> **philinux said:**
> I've not had trouble with chroot but I used this, not sure if it would make any difference.
```
cp /etc/resolv.conf /mnt/etc/resolv.conf
```

In Ubuntu, NetworkManager takes care of the resolv.conf file.
Every time you (re)start NetworkManager the file is overwritten with the list of name servers provided by NetworkManager.

In case one uses a manually configured resolv.conf file (without NetworkManager), it's safer to just *bind* the file during the chroot session instead of overwriting it.

---

### Post by JCoster on 2009-09-17
> **philinux said:**
> I've not had trouble with chroot but I used this, not sure if it would make any difference.
```
cp /etc/resolv.conf /mnt/etc/resolv.conf
```

Brilliant. This solved it, cheers philinux.

Before I was running:
```
cp /etc/resolv.conf /mnt/etc/resolv**e**.conf
```

Thanks.

---

