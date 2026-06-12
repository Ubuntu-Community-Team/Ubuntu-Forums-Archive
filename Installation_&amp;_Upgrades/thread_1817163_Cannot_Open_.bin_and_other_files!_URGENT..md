---
title: "Cannot Open .bin and other files! URGENT."
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by Joseph889 on 2011-08-03
Hello,

I am new to this forum, I signed up because of this problem I've been having.

Ok, so I have a Dell R310 server, and on my old server (Dell PE SC1420) I had the steam server installed to host for counter strike and other games, so when I got my new server, I downloaded the installer for steam, which was originally in a .bin, so I did these commands to install it:

```
chmod +x hldsupdatetool.bin
./hldsupdatetool.bin
-bash: ./hldsupdatetool.bin: No such file or directory

```The thing is, I know it exists, it comes up on ls -l and FTP. I've tried also hosting for Ventrilo, same thing. 

```
-bash: ./ventrilo_srv: No such file or directory
```Please help me, this is very important and I need to get these servers running soon!

Thanks!

---

### Post by Joseph889 on 2011-08-03
Bump. (It's really important to get this fixed)

Anyone have an idea of what this is?

---

### Post by oldos2er on 2011-08-03
What does ```
file hldsupdatetool.bin
``` say? Is the machine running a 32- or 64-bit OS?

---

### Post by Joseph889 on 2011-08-03
> **oldos2er said:**
> What does ```
file hldsupdatetool.bin
``` say? Is the machine running a 32- or 64-bit OS?

Results of file hldsupdatetool.bin are ```
hldsupdatetool.bin: ELF 32-Bit  LSB Executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), stripped
```

My system is 64 bit,and so was the old one.

---

### Post by nerdy_kid on 2011-08-03
is the filesystem ok?

```

sudo touch /forcefsck
sudo reboot

```

---

### Post by Joseph889 on 2011-08-03
Fixed. Installed 32 bit libraries, that was stupid of me.

---

