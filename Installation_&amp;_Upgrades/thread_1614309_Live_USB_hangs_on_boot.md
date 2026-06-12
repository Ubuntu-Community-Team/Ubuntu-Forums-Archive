---
title: "Live USB hangs on boot"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by subpar on 2010-11-05
I've been away from ubuntu for awhile, so I thought I would pop on back in and see how everything was going along. After putting 10.10 netbook remix on my netbook, I wanted to see how my main box would handle on ubuntu.

Well, I have had no such luck. I have made several boot pendrives, checked the md5sum of the isos and nothing has seemed to work. I've unplugged every peripheral connected to my computer except my keyboard and mouse, and nothing will get it going. I've searched a little bit before posting. One forum post said to try the following code:
```

i915.modeset=0 xforcevesa

```
which did nothing. Even attempting to run it as a liveCD gave me the same errors.

After it hangs for awhile on the ubuntu screen, it'll finally say ```
stdin: I/O error 
```

Any clues?

---

### Post by dino99 on 2010-11-05
if its a clean install, you might miss a driver for your hardware: google around with your "model+maverick"

try to boot by adding either: nomodeset, noacpi, nolapic, noapic, irqpoll (and remove quiet splash to see the comments)

---

### Post by subpar on 2010-11-05
It's a homebuilt computer, so I'll have to google each part and see what's up with it. When I removed quiet splash, this is the error it gave me (repeatedly):

```

end_request: I/O error, dev fd0, logical block 0
Buffer I/O error, dev fd0, sector 0

```

It keeps repeating that on the screen, ad nauseum.

---

### Post by dino99 on 2010-11-05
fd0 is the floppy drive :( Is there one on your system ?

Look at bios to deactivate it and into /etc/fstab too

at last you can blacklist it if nothing else work

---

### Post by subpar on 2010-11-05
> **dino99 said:**
> fd0 is the floppy drive :( Is there one on your system ?

Look at bios to deactivate it and into /etc/fstab too

at last you can blacklist it if nothing else work

Yeah, I just googled that and found out the same. How would I add it to blacklist in the boot mode? I'm going to try and disable it in bios right now.

Why does it even look for a floppy? Didn't we as a species stop making those anyways? :)

---

### Post by subpar on 2010-11-05
Alright, disabling it in my bios took care of the problem. Learned something about properly configuring my bios as well as boot options for ubuntu :) Thank you for your help.

---

### Post by dino99 on 2010-11-05
fine :) happy to see you here with us, good luck and have fun :guitar:

---

