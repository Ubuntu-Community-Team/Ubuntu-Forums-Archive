---
title: "tryed to Install Windows and can't boot now!"
date: 2005-03-21
forum: Installation &amp; Upgrades
---

### Post by emmbec on 2005-03-21
Hi I had my ubuntu system working perfectly. I had setup a fat 32 partition to install windows xp on a later time, but I was using and had only installed UBUNTU on my machine.  A few minutes ago I tryed to install Windows and when I was installing the instalation in Windows told me that the partition on which my UBUTU system was installed was active and it needed it to be inactive so windows could run ok. I told windows that it was ok to make the linux partition inactive and it was installing itself ok, but once it rebooted I think the grub thingy was damaged, since it says now that it can't find the NTLDR thing. How can I recover my UBUNTU instalation???? I am using a Live CD of knoppix right now to have internet access. Hope someone can help me, as you can see i'm somewhat new to linux. Thanks

---

### Post by TjaBBe on 2005-03-21
[QUOTE=emmbec]Hi I had my ubuntu system working perfectly. I had setup a fat 32 partition to install windows xp on a later time, but I was using and had only installed UBUNTU on my machine.  A few minutes ago I tryed to install Windows and when I was installing the instalation in Windows told me that the partition on which my UBUTU system was installed was active and it needed it to be inactive so windows could run ok. I told windows that it was ok to make the linux partition inactive and it was installing itself ok, but once it rebooted I think the grub thingy was damaged, since it says now that it can't find the NTLDR thing. How can I recover my UBUNTU instalation???? I am using a Live CD of knoppix right now to have internet access. Hope someone can help me, as you can see i'm somewhat new to linux. Thanks[/QUOTE]

I would suggest to reinstall the whole thing, and start with windows. Windows doesn't like running next to other systems (probably just out of frustration and hatred ;)). So you should start your installation with windows, and then move Ubuntu in, overwriting the nasty, non-tolerant Windows booter.

---

### Post by lao_V on 2005-03-21
You could also try to run the following command once booted up from the LIVE Ubuntu CD.

 ```
 fdisk /mbr
```

---

### Post by TjaBBe on 2005-03-22
[QUOTE=lao_V]You could also try to run the following command once booted up from the LIVE Ubuntu CD.

 ```
 fdisk /mbr
```[/QUOTE]

Hmm, maybe that is a better idea indeed  :-k. At least would save you some work  :) .

---

