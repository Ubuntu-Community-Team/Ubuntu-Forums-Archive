---
title: "modprobe problems on fresh install"
date: 2006-12-24
forum: Installation &amp; Upgrades
---

### Post by shandiddy on 2006-12-24
Please dont flame me, I hope I'm posting in the right forum. 

I have sucessfully installed and used edgy(6.10) and dapper(6.06LTS) and I have been using dapper for a year or so now, and it works flawlessly.

I recently installed linux mint 2.1(Bea) based on edgy ubuntu. Everything went perfectly well and installed perfect because it's essentially just ubuntu edgy with some preinstalled packages.

when I try to boot it loads the usual then it hangs with this message 

**"modprobe: WARNING: Not loading blacklisted module ipv6"**

I am using a HP DV6000t laptop, I have not changed or modified anything since I got it.  dapper and edgy work perfectly fine.

Any help or how to change the boot would help.
thanks

---

### Post by taurus on 2006-12-24
Maybe you want to have a look in /etc/modprobe.d/blacklist...

---

### Post by shandiddy on 2006-12-24
I would edit that but I can't even get into the OS or the command. How do I edit that out ? Recovery mode?

---

### Post by taurus on 2006-12-24
Can you boot into recovery mode from GRUB menu?

```
nano -w /etc/modprobe.d/blacklist
```
Otherwise, boot with the LiveCD, mount your / partition, and edit it...

---

