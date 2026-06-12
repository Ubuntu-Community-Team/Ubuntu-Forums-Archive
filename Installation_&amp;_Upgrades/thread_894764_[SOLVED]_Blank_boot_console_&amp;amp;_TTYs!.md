---
title: "[SOLVED] Blank boot console &amp;amp; TTYs?!"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by Mintsoft on 2008-08-19
Hi all,

I've just installed the realtime kernel package and noticed when it reboots I don't see anything on the terminal and I can't see anything if I do ctrl+alt+ F1-F6. The machine still boots but I just don't see it, the odd thing is, if I boot with the generic kernel it works fine and I can see everything! I've just checked over my menu.lst configuration and they're the same options et cetera :|
```

title		Ubuntu 8.04, kernel 2.6.24-19-rt
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=2299c57c-da7d-4a49-9292-5e0803ffefe7 ro vga=795
initrd		/boot/initrd.img-2.6.24-19-rt

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2299c57c-da7d-4a49-9292-5e0803ffefe7 ro vga=795
initrd		/boot/initrd.img-2.6.24-19-generic

```

Does anyone have any ideas on a solution to this?

Thanks

---

### Post by Mintsoft on 2008-08-20
Incase anyone ever searches the forums I've actually just solved this myself! I noticed that my laptop didn't have the same problems with the RT kernel and I remembered having to enable the vesafb module to get a 1440x900 console so I enabled the vesafb as per [https://help.ubuntu.com/community/ConsoleFramebuffer]("https://help.ubuntu.com/community/ConsoleFramebuffer") and voila I can see consoles again!

---

