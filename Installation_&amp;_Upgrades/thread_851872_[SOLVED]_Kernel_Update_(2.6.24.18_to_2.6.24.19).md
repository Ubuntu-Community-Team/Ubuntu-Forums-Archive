---
title: "[SOLVED] Kernel Update (2.6.24.18 to 2.6.24.19)"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by Kydwn on 2008-07-07
Recently, I updated from kernel 2.6.24.18 to 2.6.24.19 .
During restart, I choose the new kernel, I enter userid and password and... all I get is the userid screen again... The system just doesn't start with the new kernel.

I've been using 2.6.24.18 kernel with no problems at all. (compiz, 3d cube, emerald theme manager etc).

I've noticed that if I disable from System-Administrator-Hardware drivers the ati graphic driver, I can use the new kernel but then again I notice that I have no sound (Intel 82801DB-ICH4).

Of course, none of the above happen if I start with 2.6.24.18. So I stay with 2.6.24.18 kernel waiting for a future update...

---

### Post by Kydwn on 2008-07-08
I've searched for so long in all sorts of forums, but nothing at all...

There 're other similar reports but no suggestions...

I guess I ll have to wait for the end of the summer...

:)

---

### Post by Archmage on 2008-07-08
Is it possibile that your keyboard got switched to US and you password has keys that are not there on the US-keyboard?

E.g. your password is puzzel an you need to enter puyyel to enter?

---

### Post by Kydwn on 2008-07-09
I guess you haven't read my first message...

:confused:

---

### Post by Archmage on 2008-07-09
> **Kydwn said:**
> I guess you haven't read my first message...

:confused:


Well, if you type in a wrong password, than you can't log in and will always go back to the login-promt. And if you have a keyboard that is using the wrong keys, wenn you press them, this could result in entering the wrong password.

---

### Post by Kydwn on 2008-07-09
What you say is that password works fine for kernel 2.6.24.18 but not for 2.6.24.19?
:confused:

---

### Post by Kydwn on 2008-07-10
Problem solved!!! 
I thought that restricted driver for ATI, doesn't operate normaly under kernel 2.6.24.19.
So, through Synaptic I installed the resticted module-generic- for kernel 2.6.24.19. After a restart, I managed to enter using kernel 2.6.24.19. But... There was no sound at all. Here is what I did:
$ sudo aptitude reinstall linux-restricted-modules-2.6.24-19-generic (this was already installed but the instructions I found said to install it again)
$ sudo aptitude reinstall linux-restricted-modules-common
$ sudo aptitude reinstall linux-restricted-modules-generic

So, I have - again - sound in my system, and everything is working fine!!!

( A t   L a s t . . . )

---

