---
title: "Upgrade problem"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by localhost44112 on 2007-06-11
I have upgrade my Ubuntu and the last kernel wont boot; it seems it cant find my hard disk :( I tried also to use the Ubuntu Install CD and I have the same problem.

Any suggestions?

Thk a lot ;)

---

### Post by taurus on 2007-06-11
Boot from the LiveCD and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by localhost44112 on 2007-06-11
It gives me empty output cuz it doesn't find any hds ;)

---

### Post by taurus on 2007-06-11
Can you post the whole message when you ran that command from a terminal?

---

### Post by localhost44112 on 2007-06-11
I typed what you told me:

> sudo fdisk -l

Then I see:

> ubuntu@ubuntu:~: sudo fdisk -l
ubuntu@ubuntu:~:

Thats what I see; nothing :((

Thk

---

### Post by merlinus on 2007-06-11
Perhaps you got this right, but the l is a lowercase L.

-merlin

---

### Post by taurus on 2007-06-11
Also, get into your BIOS and see if the system even detects your harddrive(s) at all.

---

### Post by localhost44112 on 2007-06-11
Its not related to BIOS; the old edgy's kernel works well and I can boot the system :)

---

### Post by taurus on 2007-06-11
I bet you have a PATA harddrive and the original kernel converts it from /dev/hda to /dev/sda.  Then, the latest kernel goes back to /dev/hda and that is why the new kernel can't boot because it can't find your / partition in /etc/fstab.

---

### Post by localhost44112 on 2007-06-11
Its a SATA and there is no device available from /dev (like hda or sda) :(

---

