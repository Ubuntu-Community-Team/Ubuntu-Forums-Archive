---
title: "shutting down in the middle of updates"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by mocatz187 on 2010-01-06
Hi.
I was in the middle of updates when a console message appeared stating it needed permission to exit while others were logged on to my computer.
so I clicked cancel because the terminal was still clearly configuring the kernel update.
upon clickingh cancel the system crashed and would not boot.
what should I do if the system wants to log off befotre its done .
was this an early message that would have worked itself out?
I have never used gparted before but I know that I will never get a second installation to take without all of the settings being screwed up.
this means that I won't get updates or anything.

---

### Post by kansasnoob on 2010-01-06
So can you not boot at all now? Do you have a Live CD?

If you can boot a live CD post the output of:

```
sudo fdisk -l
```

BTW that's a lower case L.

We might be able to fix it.

---

### Post by mocatz187 on 2010-01-06
cannot reboot.
I have started all over but how can I prevent this from happening again.
I have started the updates again.
I suppose next time when the machine asks for a password to logout right in the middle of kernel configuration I'm going to give it what it asks for regardless of whether the timing seems right or not.
it was probably just going to store the permission until it needed it right?

---

### Post by SecretCode on 2010-01-06
And can you boot from a live CD?

It's definitely odd that this should happen. But it should be recoverable.

---

### Post by mocatz187 on 2010-01-06
As much fun as it sounds to go in and fix the OS I think I'll pass, at least for this computer. 
I have reinstalled and everything seems fine.
Thanks

---

### Post by kansasnoob on 2010-01-06
Was that by any chance a Partial Upgrade? I saw someone else got nailed by a partial today.

I didn't have it but I may be on a different server.

---

### Post by mocatz187 on 2010-01-07
Nope, it was a full upgrade.

---

