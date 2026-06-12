---
title: "Login Screen Settings Will Not Unlock in Lucid 32bit"
date: 2010-02-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2010-02-13
In trying to get my machine to boot correctly not using Recovery Mode I found that my "Login Screen Settings" on Lucid 32 bit will not unlock. On my Lucid 64 bit it works fine but do not have to use recovery mode. I have my system set to auto login and was thinking that is giving me trouble. The problem is I cannot change it like I can on Lucid 64 or Karmic.

Bill

---

### Post by sparker256 on 2010-02-13
> **sparker256 said:**
> In trying to get my machine to boot correctly not using Recovery Mode I found that my "Login Screen Settings" on Lucid 32 bit will not unlock. On my Lucid 64 bit it works fine but do not have to use recovery mode. I have my system set to auto login and was thinking that is giving me trouble. The problem is I cannot change it like I can on Lucid 64 or Karmic.

Bill

Had a problem with my /etc/gdm/custom.conf
When I got it to look like this all if fine again.
I was missing the last line.

```



[daemon]
AutomaticLoginEnable=true
AutomaticLogin=bill
TimedLoginEnable=false
TimedLogin=bill
TimedLoginDelay=10
DefaultSession=gnome

```

---

