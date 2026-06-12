---
title: "Cannot log in to new Edgy install- Please help!!"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by declaration on 2006-12-03
Hi,

have done a new install but cannot login through Gnome.

I put my password and username in (making sure case sensitive) but it wont login.

Any help is much appreciated...

Thanks

---

### Post by taurus on 2006-12-03
Did you install it with the LiveCD or the alternate CD?  Try boot into recovery mode from GRUB menu and at the prompt, paste the output of this command here...

```
cat /etc/passwd
```

---

### Post by declaration on 2006-12-03
LiveCD. I will post that output later...

Thanks.

---

### Post by RoboRutt on 2006-12-05
Hi guys, 

I was getting the same message (hence I searched this thread) and did a little poking around... looks like my home partition was full, so apparently edgy will not log in if the home part is at 100%... I am a noob to unbuntu.. does this sound correct to the guru's that be?

Just an idea

Rob

---

### Post by bapoumba on 2006-12-05
Hi, RoboRutt,
yes indeed. But when you are running out of /home disk space, you get right back to the gdm login screen, which looks different from the problem here. There are a couple of bugs in malone and in GNOME actually ;)

---

### Post by taurus on 2006-12-05
> **RoboRutt said:**
> Hi guys, 

I was getting the same message (hence I searched this thread) and did a little poking around... looks like my home partition was full, so apparently edgy will not log in if the home part is at 100%... I am a noob to unbuntu.. does this sound correct to the guru's that be?

Just an idea

Rob
Do you have a separate /home partition or you only have one / partition (plus the swap, of course)?  You need to remove some files, making room so you can write to it...

---

