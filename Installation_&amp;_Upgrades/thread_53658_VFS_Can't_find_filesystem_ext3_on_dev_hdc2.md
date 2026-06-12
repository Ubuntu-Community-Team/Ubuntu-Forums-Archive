---
title: "VFS: Can't find filesystem ext3 on dev hdc2"
date: 2005-08-01
forum: Installation &amp; Upgrades
---

### Post by ariffin on 2005-08-01
Hello, I'm a newbie and I hope I don't offend. I love linux and will bleed until it works the way I want it to.

So, here is the problem. On bootup, even before the default terminal font is loaded, I get this error:

**VFS: Can't find filesystem ext3 on dev hdc2**

I use ReiserFS and am dual-booting with XP. Is that message even an error? Everything works just great after the bootup. I hope someone knows what it is, just to cure the nagging feeling.

---

### Post by ariffin on 2005-08-01
Okay, I've found the solution. The message isn't even a serious problem. It results from autoprobing for filesystems built into the kernel. It can be ignored!

[https://bugzilla.ubuntu.com/show_bug.cgi?id=2100](https://bugzilla.ubuntu.com/show_bug.cgi?id=2100)

Hopefully, somebody will find this and not get uptight over it the way I did.

---

### Post by eeried on 2005-08-02
Thanks for your reassuring message ariffin, and the link.

I get that on my desktop with only ubuntu installed, while the laptop on dual-boot shows no VFS message.

---

