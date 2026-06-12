---
title: "preserving /home after upgrading/bitness"
date: 2016-12-03
forum: Installation &amp; Upgrades
---

### Post by ray field on 2016-12-03
I've been happy with 14.04, and am not inclined to update it, though I do feel the tug... on the other hand, I have never moved on from 32-bit Ubuntu and I guess it's finally time.

so, sometime in the next few weeks I'll probably buy a new SSD and install 64-bit 16.04 on that. 

my question:

1) I've kept /home on its own partition. what's the likelihood of being able to use Aptik to restore my preferences and apps, and use all those files?

2) also, if I want to be able to keep my passwordless SSH connections as-is, what do I need to copy from /etc?

---

### Post by TheFu on 2016-12-04
1) Should be mostly fine. I've moved my HOME from 32-bit to 64-bit installs multiple times.

2) ssh connections out are controlled by ~/.ssh/ files and settings.  Inbound is a different thing.

---

### Post by ray field on 2016-12-05
> **TheFu said:**
> 1) Should be mostly fine. I've moved my HOME from 32-bit to 64-bit installs multiple times.

2) ssh connections out are controlled by ~/.ssh/ files and settings.  Inbound is a different thing.

1) thanks. I hate "upgrading," I'd just as soon still be on OS/2 1.3.

2) in the past I think I've actually just copied everything from /etc/ssh -- and maybe some files in my /home directory, i.e., all of ~/.ssh? -- and done this, and it's worked for inbound SSH, just looking for confirmation.

---

### Post by kpatz on 2016-12-05
Copying /etc/ssh and ~/.ssh should be adequate for retaining your logins.

You don't even need to copy /etc/ssh, but if you don't, the server key will change and clients will get a message about the key not matching.

---

### Post by ray field on 2016-12-05
thanks.

---

