---
title: "Network Manager not saving in Keyring (or seahorse)"
date: 2008-09-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by gaussian on 2008-09-15
Has anyone encountered the following? And maybe has a workaround? I did some Googleing, but could not find an answer to the problem:

I have up-to-date 32-bit Intrepid installation. Not a clean install, but updated with update manager from Feisty (with all the intermediate steps). My main installation is 64-bit Gutsy.

I noticed that Network manager does not save passwords to wireless access points to keyring (or anywhere). I also tried saving with checking "System settings", but this did not help (it did not connect automatically after reboot, only reconnected after removing the "System settings"). This is true for a new user too.

I am happy to file a bug, but wanted first feedback if this was just a PEBKAC. I have now installed wicd for awhile because this was driving me nuts.

---

### Post by Jove on 2008-09-16
Yeah, I'm encountering this behavior as well.

---

### Post by bpl07 on 2008-09-16
Me too.  Bug report?

---

### Post by gaussian on 2008-09-16
Added a comment to similar Hardy bug that it affects Intrepid.

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/206568](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/206568)

---

### Post by analystscouch on 2008-09-16
I hadn't seen that Hardy report. I reported this for Intrepid a while back.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/265127](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/265127)

---

### Post by gaussian on 2008-09-16
> **analystscouch said:**
> I hadn't seen that Hardy report. I reported this for Intrepid a while back.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/265127](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/265127)

These are definitely related. Especially the system settings part.  But in my case, I can connect (at least to WEP access point), but I have to retype the password (since it is not been saved).

---

### Post by Tatty on 2008-09-17
I have just installed Intrepid (amd64) and appear to be getting this too.  Will comment on launchpad once it comes back up from maintenance.

---

### Post by rwabel on 2008-09-24
same for me here. It just doesn't store the WPA key :-(

---

