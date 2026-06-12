---
title: "I am not able to Create anew user"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jayeshm on 2010-03-31
Hi,

I upgraded from Ubuntu 9.10 to 10.4 now i am not able to create new users. My current user is in administrative group still i am not able to create new users

---

### Post by meborc on 2010-03-31
what steps do you take to create a new user and what error messages (if any) you get?

have you tried adding users from CLI?

---

### Post by jayeshm on 2010-03-31
I created it from system >administration > users and groups

---

### Post by meborc on 2010-03-31
> **jayeshm said:**
> I created it from system >administration > users and groups

yes, but at what point do you get an error? i'm away from my lucid box, but will try it later

---

### Post by jayeshm on 2010-03-31
Actually it is not giving any error, after creation it is going to invalid stage. If we try to enable it, it will again become disabled

---

### Post by monraaf on 2010-04-01
Perhaps you're affected by this bug:

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/545864](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/545864)

> 
Workaround:
1. Run sudo dpkg-reconfigure -plow libpam-runtime
2. Deselect "Winbind NT/Active Directory authentication"
3. Select OK


---

### Post by jayeshm on 2010-04-02
Thanks,

Now i am able to create new users

---

