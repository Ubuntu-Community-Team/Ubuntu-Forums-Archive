---
title: "Live CD SU Password"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by SomeoneKnows on 2008-04-09
I have

---

### Post by SomeoneKnows on 2008-04-09
sorry about that...

I'm having trouble getting my dual boot pc to boot into Windows XP but can boot into Fedora. The problem with Fedora Core 4 is it doesn't recognize my Windows partition (NTFS).

I heard that Ubuntu does recognize the NTFS drives. I downloaded the Ubuntu Live CD and everything started great. When I started a terminal and tried to get SU privileges I don't have a password to get the proper permissions. Do I have to go through the install process first, I'm not seeing a way to change the password booted from the Live CD.

Is there a standard password for the Live CD?

---

### Post by Pumalite on 2008-04-09
You don't need a password for the Live CD. su is equivalent to sudo in Ubuntu.

---

### Post by gsmanners on 2008-04-09
I think the su is disabled by default in Ubuntu, so you would type this instead:

sudo -i

The live CD should not require a password as stated above.

---

### Post by Pumalite on 2008-04-09
You can also type:
sudo su
(If you want to be root for more than 10 min)

---

### Post by Pumalite on 2008-04-09
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

