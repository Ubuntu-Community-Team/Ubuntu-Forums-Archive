---
title: "[SOLVED] Boot Partition and Unable to CD to /home error on new install"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by VastOne on 2008-11-22
Greets...

I have a stable 8.10 running from an upgrade from 8.04.

I have a /home partition setup

I installed a fresh 8.10 to a new drive, manually selecting my file (/), my home (/home to the correct partition) and a swap area.  All installed well but when I try to login in I get:

command prompt for login that says TTY1: Unable to CD to /home/username

Note:  I used the exact login/PW name on the new install. 

I also told the install to import my settings from the original 8.10

I seemed to have followed everything the way your supposed to but it appears I have no rights to my /home on the home partition.

Anyone able to shed light on where I went wrong?  

VastOne

---

### Post by taurus on 2008-11-22
Boot into recovery mode from GRUB menu and see whether your login name is the same as the one in /home.

Post the outputs of these commands if you are not sure what to look for.

```
tail /etc/passwd
ls -la /home
df -h
```

---

### Post by VastOne on 2008-11-22
taurus,

Thanks for quick reply...Here are the results

last line of tail code

vastone : x1000:1000 VastOne,,, :/home/vastone:/bin/bash

last line of ls -la code

drwxr -xr -x 78 vastone vastone 

last line of df -h code

/dev/sdb6 /home

all of which looks like it should be to me....

Let me know what you think...

Thanks 

VastOne  


> **taurus said:**
> Boot into recovery mode from GRUB menu and see whether your login name is the same as the one in /home.

Post the outputs of these commands if you are not sure what to look for.

```
tail /etc/passwd
ls -la /home
df -h
```

---

### Post by VastOne on 2008-11-22
Further info,

I ran these same queries in the 1st installation of 8.10 (logged in as vastone) and received the exact same results. Based on that, I should be able to access /home from either install, but I am still getting the Unable to CD to /home error trying to boot from the new install of 8.10

Can anyone shed light on this?  Needing traction.....

Thanks...

VastOne

> **VastOne said:**
> taurus,

Thanks for quick reply...Here are the results

last line of tail code

vastone : x1000:1000 VastOne,,, :/home/vastone:/bin/bash

last line of ls -la code

drwxr -xr -x 78 vastone vastone 

last line of df -h code

/dev/sdb6 /home

all of which looks like it should be to me....

Let me know what you think...

Thanks 

VastOne

---

### Post by VastOne on 2008-11-22
Anyone?

Seemed to have lost traction....

> **VastOne said:**
> Further info,

I ran these same queries in the 1st installation of 8.10 (logged in as vastone) and received the exact same results. Based on that, I should be able to access /home from either install, but I am still getting the Unable to CD to /home error trying to boot from the new install of 8.10

Can anyone shed light on this?  Needing traction.....

Thanks...

VastOne

---

### Post by VastOne on 2008-11-23
Where art all thy experts?

V1

> **VastOne said:**
> Anyone?

Seemed to have lost traction....

---

### Post by VastOne on 2008-11-23
I solved this by re-installing Ibex the same exact way with the only exception being that I formatted the / (file system) partition this time around.

In the first install I had already had that partition setup as an ext3 with nothing on the disk.  I had the install just use it (/ file system) and after the install I had no rights even though the user was exactly the same. 

I am sure I could have done a chmod 755 and gotten the same results.

Any way, solved....

> **VastOne said:**
> Greets...

I have a stable 8.10 running from an upgrade from 8.04.

I have a /home partition setup

I installed a fresh 8.10 to a new drive, manually selecting my file (/), my home (/home to the correct partition) and a swap area.  All installed well but when I try to login in I get:

command prompt for login that says TTY1: Unable to CD to /home/username

Note:  I used the exact login/PW name on the new install. 

I also told the install to import my settings from the original 8.10

I seemed to have followed everything the way your supposed to but it appears I have no rights to my /home on the home partition.

Anyone able to shed light on where I went wrong?  

VastOne

---

