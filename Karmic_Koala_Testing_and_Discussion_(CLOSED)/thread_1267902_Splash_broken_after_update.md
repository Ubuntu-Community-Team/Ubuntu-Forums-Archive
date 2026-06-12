---
title: "Splash broken after update"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jonick on 2009-09-16
Hi Guys,

My splash is broken on boot up & shutdown after todays (16/09/2009)

anyone else seeing this issue?

Regards,

jonick.

---

### Post by simmeson on 2009-09-16
Yup, same here.

---

### Post by Funnnny on 2009-09-16
Or they removed it ?

---

### Post by simmeson on 2009-09-16
> **Funnnny said:**
> Or they removed it ?

Hopefully youre right so that we in the next update will get the new one based on xsplash ;)

---

### Post by portis on 2009-09-16
Could it be related to this change?

usplash (0.5.37) karmic; urgency=low

  FFE LP: #427356.

  * Make usplash optional in the initramfs, you need to set USPLASH=y

---

### Post by forumache on 2009-09-16
I read somewhere that the idea is to get rid of usplash and start xsplash as early as possible.

---

### Post by siegi on 2009-09-16
I have the same issue, I don't see usplash. 
But I have some udev error messages.
[http://ubuntuforums.org/showpost.php?p=7956755&postcount=4](http://ubuntuforums.org/showpost.php?p=7956755&postcount=4) 
The system boots normally. 

Do you guys get this errors to?

---

### Post by moviemaniac on 2009-09-16
> **siegi said:**
> Do you guys get this errors to?

everybody who updated does :D

[https://bugs.launchpad.net/ubuntu/karmic/+source/dbus/+bug/430611](https://bugs.launchpad.net/ubuntu/karmic/+source/dbus/+bug/430611)

---

### Post by Eestlane on 2009-09-16
> **forumache said:**
> I read somewhere that the idea is to get rid of usplash and start xsplash as early as possible.

Yeah.
[http://www.netsplit.com/2009/09/02/making-a-splash/](http://www.netsplit.com/2009/09/02/making-a-splash/)

---

