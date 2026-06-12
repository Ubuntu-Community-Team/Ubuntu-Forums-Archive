---
title: "azerty luks and cloud-config (user-data)"
date: 2022-05-03
forum: Installation &amp; Upgrades
---

### Post by totoroavi on 2022-05-03
Hi,

I try to make a master with a 22.04, so I install with cloud-config way.
I set up lvm crypt partition, it's working fine, I pass password in user-data.

The problem is, at reboot and during the luke authentication, keyboard is in qwerty...
So I make try with simple password to fins a way to solve it:

    ```
echo "KEYMAP=y" >> /etc/initramfs-tools/initramfs.conf && /usr/sbin/update-initramfs -u`
```

It's working, but no way to put it in user-data file.
I try to put this in user-data

```
    - curtin in-target --target=/target -- echo "KEYMAP=y" >> /etc/initramfs-tools/initramfs.conf
    - curtin in-target --target=/target -- update-initramfs -u -k all
```

I try too to make a small bash script, who is downloaded at the end of user-data file and run it. Not working

It's look "update-initramfs -u" is not making change on the correct kenel.

Any idea ?

Have a nice day.

---

### Post by totoroavi on 2022-07-18
Hi

I foud a solution.
At installation end I run this command :

```

echo '
XKBMODEL="pc105"
XKBLAYOUT="fr"
XKBVARIANT=""
XKBOPTIONS=""
    
BACKSPACE="guess"
' > /etc/default/keyboard

```
And then : dpkg-reconfigure --frontend noninteractive keyboard-configuration

---

