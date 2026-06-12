---
title: "uname release errror"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by bstanley on 2011-04-17
I have just upgraded my system from version 9.04 to 9.10.

I then upgraded it from 9.10 to 10.04 LTS.

When i run the   uname -a command it shows:

Linux ubuntu-9-04 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 i

It still thinks it is running unbuntu 9.04.

The /etc  lsb-release and issue files both show the version
as 10.04.

How do i fix the uname command?

---

### Post by plucky on 2011-04-18
> **bstanley said:**
> I have just upgraded my system from version 9.04 to 9.10.

I then upgraded it from 9.10 to 10.04 LTS.

When i run the   uname -a command it shows:

Linux ubuntu-9-04 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 i

It still thinks it is running unbuntu 9.04.

The /etc  lsb-release and issue files both show the version
as 10.04.

How do i fix the uname command?

What does ```
cat /etc/hostname
``` show you?

Looks like your hostname is "ubuntu-9-04"

Good Luck

---

### Post by bstanley on 2011-04-18
> **plucky said:**
> What does ```
cat /etc/hostname
``` show you?

Looks like your hostname is "ubuntu-9-04"

Good Luck
I checked the hostname file and it was set to  unbuntu-10-04.

But, the /etc/hosts file had the node name as  ubuntu-9-04 .

Changed it to ubuntu-10-04 and all is well in uname world.

Thanks for pointing me in the right direction !!  :-)

---

