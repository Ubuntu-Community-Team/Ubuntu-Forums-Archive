---
title: "Restored system GDM / ConsoleKit problem"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by J&#7885;hn on 2010-12-29
Hi Everyone

I backed up my Maverick install with tar and restored it to a new drive, chrooted into the new system from a live cd, reinstalled grub, modified the UUIDs for fstab and resume, and the machine boots up fine. At this point I was fairly confident that it had been a success ('cos I've restored linux machines before).

However, GDM doesn't display any user names to pick from, instead it just sits there with the ubuntu logo and the machine name. If I bypass GDM and startx manually I can't start (for example) network manager applet. The error message I get is

```
Error: (9) Connection ":1.51" is not allowed to own the service "org.freedesktop.NetworkManagerUserSettings" due to security policies in the configuration file
```

Anyone have any ideas why this would be the case? Apart from the change in UUIDs the system is identical to the one I backed up!! I've never encountered this doing previous restores so am pretty sure it's some new fangled feature I don't know anything about.

Thanks for any help. 

J&#7885;hn

---

### Post by axeldamage on 2011-01-25
Same problem in Maverik after update!

---

### Post by alcarola on 2011-06-04
I have the same problem after reverting to an old installation of lucid from natty. In my case, this installation of lucid run without problems on the same machine earlier. I've not seen this kind of problem, although I've been juggling around with backups and restores many times before.

---

