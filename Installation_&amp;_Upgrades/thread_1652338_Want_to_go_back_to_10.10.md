---
title: "Want to go back to 10.10"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by ubkid on 2010-12-24
I recently installed 10.10, and just yesterday Ubuntu updated my software, and for some reason loaded 11.04 alpha on my machine.  Even if I select the oldest release in GRUB, Ubuntu still boots up as 11.04, as reported in the SYSTEM/ABOUT UBUNTU menu.  I am relatively new to Ubuntu and want to stick to a stable release.  Can I go back to 10.10 without completely reloading Ubuntu?  FWIW, I have a dual-boot machine with Windows 7, 64-bit on one drive and Ubuntu 64-bit on its own drive.  Even though I am a relatively new user, I really love Ubuntu--it's feel and organization is so much nicer than Windows, and I don't feel the usual Windows irritation factor when using it.  Thanks for any help you can offer!!!

---

### Post by howefield on 2010-12-24
It is most likely this bug...

[https://bugs.launchpad.net/ubuntu/+s...cs/+bug/690248](https://bugs.launchpad.net/ubuntu/+s...cs/+bug/690248)

What is the output of the following terminal command ?

```
lsb_release -a
```

---

### Post by ubkid on 2010-12-24
> **howefield said:**
> It is most likely this bug...

[https://bugs.launchpad.net/ubuntu/+s...cs/+bug/690248](https://bugs.launchpad.net/ubuntu/+s...cs/+bug/690248)

What is the output of the following terminal command ?

```
lsb_release -a
```

Here is the output:

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick

---

### Post by Runckle on 2010-12-24
You have 10.10 on your system.

---

### Post by kansasnoob on 2010-12-24
Yes, you're really running Maverick! I filed this bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248)

many dups

---

### Post by kansasnoob on 2010-12-24
> **howefield said:**
> It is most likely this bug...

[https://bugs.launchpad.net/ubuntu/+s...cs/+bug/690248](https://bugs.launchpad.net/ubuntu/+s...cs/+bug/690248)

What is the output of the following terminal command ?

```
lsb_release -a
```

Your link was hosed ;)

```
https://bugs.launchpad.net/ubuntu/+s...cs/+bug/690248
https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248
```

---

### Post by ubkid on 2010-12-25
> **kansasnoob said:**
> Yes, you're really running Maverick! I filed this bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248)

many dups

Thanks very much.

---

