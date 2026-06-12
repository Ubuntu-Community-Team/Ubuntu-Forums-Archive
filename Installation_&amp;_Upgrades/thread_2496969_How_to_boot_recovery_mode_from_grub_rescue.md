---
title: "How to boot recovery mode from grub rescue?"
date: 2024-04-18
forum: Installation &amp; Upgrades
---

### Post by djeyewater on 2024-04-18
I've installed Ubuntu on an old tablet, but it doesn't currently boot automatically and instead I end up at Grub Rescue.
I can run the following:
```
set root=(hd0,gpt2)
linux /boot/vmlinuz root=/dev/disk/by-id/mmc-BGND3R_0x2f804915-part2
initrd /boot/initrd.img
boot
```
And it will boot, but I just get a plain blue screen with a couple of icons top right. I can't open terminal via keyboard shortcut. I did manage to connect to the wifi but it seems ssh is disabled so I can't get in that way.
From reading other threads it seems the advice is to boot into recovery mode. But I have no idea how to do this?

---

### Post by Rubi1200 on 2024-04-20
Sounds like there might be a few problems here.

Which version of Ubuntu, what are the specs. for the tablet especially graphic card and memory?

If you run the system info script in my signature and post the pastebin link back here it might give us a better chance at analyzing the situation.

---

### Post by yancek on 2024-04-20
Running the boot repair script and posting the output link here would go a long way to get help.  Since you can boot with the entry you posted, have you tried putting that exact entry in the /boot/grub/grub.cfg file?  If you try that, do not update-grub.  If it boots, it will be a temporary solution.  You need to be more specific about what old is, year of manufacture would be good.

---

### Post by djeyewater on 2024-05-07
To answer the question, to boot in recovery mode you need to add 'single' to the end of the linux command. This will then boot in single user / recovery mode. So in my case, I had to use:
```
set root=(hd0,gpt2)
linux /boot/vmlinuz root=/dev/disk/by-id/mmc-BGND3R_0x2f804915-part2 single
initrd /boot/initrd.img
boot
```

Also, to correct myself, it was not grub rescue but standard grub.

I'll post a new thread about the issue with there being no boot entries in grub.

---

