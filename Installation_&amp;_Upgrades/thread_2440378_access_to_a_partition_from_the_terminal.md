---
title: "access to a partition from the terminal"
date: 2020-04-09
forum: Installation &amp; Upgrades
---

### Post by jeancesaravon on 2020-04-09
I recently installed *Ubuntu 18.04.4 LTS* on sda1. Then I have a sda2 partition for some data.
 I can access the files in both partitions from the file icon in the dock
 On the terminal, I can access the files in sda1, as it prompts jean@jean-G2P:~$
 On the terminal, when I try to access the contents of sda2, then I have a problem:
 
 
 **jean@jean-G2P:~$ cd /dev**
 
 
 **jean@jean-G2P:/dev$ ls  -l**
 **...**
 **brw-rw----  1 root disk      8,   0 avr  9 19:52 sda**
 **brw-rw----  1 root disk      8,   1 avr  9 19:52 sda1**
 **brw-rw----  1 root disk      8,   2 avr  9 19:52 sda2**
 …
 
 
 **jean@jean-G2P:/dev$ cd sda2**
 [COLOR=#ce181e]**bash: cd: sda2: Not a directory**[/COLOR]
 
 
 **jean@jean-G2P:/dev$ cd disk/by-uuid**
 
 
 **jean@jean-G2P:/dev/disk/by-uuid$ ls -l**

 **total 0**
 **lrwxrwxrwx 1 root root 10 avr  9 19:52 0092f46a-e796-4291-9df8-1beb7d1082cb -> ../../sda2**
 **lrwxrwxrwx 1 root root 10 avr  9 19:52 9945d714-fe96-4ab4-8d4d-dd73eff0b0b1 -> ../../sda1**
 
 
 **jean@jean-G2P:/dev/disk/by-uuid$ cd 0092f46a-e796-4291-9df8-1beb7d1082cb**
 [COLOR=#ce181e]**bash: cd: 0092f46a-e796-4291-9df8-1beb7d1082cb: Not a directory**[/COLOR]
 
 
 Can you please help me to access the contents of sda2 on the terminal?  
 I thank you in advance.
 Best regards,
 Jean Paul

---

### Post by TheFu on 2020-04-09
/dev/ has device "files".  They are not to be used directly.
You need to mount sda2 onto an empty directory.

```
sudo mkdir /Data
sudo mount /dev/sda2 /Data
```

Now try to **cd /Data**

There can be permissions considerations to be resolved.  Depends on the file system on sda2.

if you want to make the mount automatic at boot, use the /etc/fstab

BTW, based on this question, seems you are extremely new to Unix-like systems.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) has pretty much all that you might need to know that aren't Ubuntu-specific.  For those, help.ubuntu.com and the desktop or server User Guides are quick.

---

### Post by jeancesaravon on 2020-04-10
Thank you very much, TheFu, for your appreciated help!

And thank you too for the link: I just downloaded TLCL-19.01.pdf and I am learning a lot.

Have a nice day,
Jean Paul

---

