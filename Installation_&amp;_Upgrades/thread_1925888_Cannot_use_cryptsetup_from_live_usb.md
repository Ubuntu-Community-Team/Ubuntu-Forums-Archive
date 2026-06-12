---
title: "Cannot use cryptsetup from live usb"
date: 2012-02-15
forum: Installation &amp; Upgrades
---

### Post by irw on 2012-02-15
I feel like I am banging my head against a brick wall here.

I have an encrypted system (11.10) installed from the alternate install cd.

I am now trying to access the encrypted partition from a live cd (running on USB stick), but I cannot get cryptsetup to work.

I booted into the live environment.
Installed cryptsetup by ```
sudo apt-get install cryptseup
```

I then tried to access my partition:
```
sudo cryptsetup luksOpen /dev/sda3 crypt_sda3
```
and this is my output:
```
Enter passphrase for /dev/sda3: 
No key available with this passphrase.
Enter passphrase for /dev/sda3: 
No key available with this passphrase.
Enter passphrase for /dev/sda3: 
No key available with this passphrase.

```

I know I am using the correct passphrase - it works fine when I boot into the system normally.

I tried also ```
sudo modprobe dm-crypt
``` but this has no effect.

What am I doing wrong?

I have searched the forums / elsewhere and see others carrying out the steps I have followed without this problem.

---

### Post by irw on 2012-02-15
OK - I'm an idiot.

Cryptsetup works fine - the problem was the keyboard layout.

I have a UK layout, the default for the live cd is US - and my passphrases use some characters that are not on the same keys!

---

