---
title: "Help Me Understand."
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by rosendahl on 2007-10-26
I'm following this guide to install 7.10: [https://help.ubuntu.com/community/Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux")
I have no problems until 'Step 3'.

In the guide the example is
> 
title installer
        root [COLOR="Red"](hd0,0)[/COLOR]
        kernel /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw
        initrd /casper/initrd.gz

... the partition I want to install from is [COLOR="Red"]/dev/sda3[/COLOR]. My question is: What do i need to replace ***(hd0,0)*** with?

---

### Post by dabl on 2007-10-26
In "Grubspeak" your target partition is (hd0,2).

:)

---

### Post by rosendahl on 2007-10-26
And sorry for my bad English. I'm just a 14 years old boy from Denmark.

---

### Post by rosendahl on 2007-10-26
Thanks for the fast answer, I will try it.
Edit: It worked.

---

