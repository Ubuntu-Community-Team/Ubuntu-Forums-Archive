---
title: "New user &amp; group manager killed my lucid :]"
date: 2010-01-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by xens on 2010-01-24
Hi there, I think I found an annoying bug

1. Start user & group
2. Add group whatyouwant to your main user
3. Apply
4. Cry

It removed half of the entries in my /etc/group file, I had to boot to another partition, the edit the group file and re-add the deleted lines (I took the example of my group file in karmic).

Can someone with a VM please try this ? I'm quite sure it's not related to my setup.

Thanks :KS

Romain

---

### Post by phenest on 2010-01-24
Tried in a VM, but not getting this.

---

### Post by moviemaniac on 2010-01-24
I've had some other issues with the new use & group manager. I can tick all the groups I want for my user and save. When I log out and log in again, all the ticks are gone but the settings have been applied. However when I then log out and log in for a second time, the settings themselves are gone, too. It's very annoying, because I lose being a member of the virtualbox group on every login when I don't set the group memberships every time before logging out... Luckily I only reboot my machine when an update requests it :D

---

### Post by cariboo on 2010-01-24
If you manually add yourself to the vboxuser group, does it stick?

```
sudo gpasswd -a <user> vboxuser
```

---

### Post by moviemaniac on 2010-01-25
Yeah, that works when looking at /etc/group after a reboot. The user & group manager is still buggy, though, it doesn't show any of my group memberships...

---

### Post by xarte on 2010-01-30
I wanted to add a note to this as I'm having the same trouble with users/groups not working in my (dual boot) installation.

This is mentioned in another thread. Have you found any solutions for yours?

I also tried simply changing the user type to 'administrator' or 'desktop user' but that didn't apply at all.

I tried re-installing gnome-utils and a couple of other packages that seemed related to users and groups, no change.

---

