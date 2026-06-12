---
title: "Fiesty Boot Starts with no bootsplash and weird messages"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by Recked on 2007-03-29
Hello,

I just installed Feisty on a dual Athlon MP 1900 computers with dual hard drives and for some reason while the machine boots up ok I get no bootsplash and a number of what appears to be error/issue messages while it comes up. Not sure if the messages are a problem hard drive or if they are referring to an issue with a processor.

Is there any way to get a screenprint or other output from the boot sequence?


thank you

---

### Post by adam.tropics on 2007-03-30
In a terminal
```
  dmesg | more
```

---

### Post by Recked on 2007-03-30
Thanks Adam I will try this when I get home. I sure hope I am not having issues with one of the processors or something now as I just bought a replacement motherboard for the two cpu's etc. I assume if I post the output from the command somebody here might be able to suggest something?

thanks again

---

### Post by adam.tropics on 2007-03-30
I would think so, though you could see if anything stands out in dmesg, and search the forum first, could save you some time.

---

### Post by Recked on 2007-03-31
Hello,

Just below is the area of the boot process where there appears to be an issue or two. The first time I brought the machine up tonight there were no issues and I had a bootsplash. The system got hung up when I was doing what amounted to a partial upgrade and I had to reboot. This second boot did not give a bootsplash and I got this partial listing:

   19.896000] "amd76xrom" amd76xrom_init_one(): Unable to register resource 0x00000000ffff0000-0x00000000ffffffff - kernel bug?
[   19.920000] CFI: Found no "amd76xrom" @ffff0000 device at location zero
[   19.932000] JEDEC: Found no "amd76xrom" @ffff0000 device at location zero
[   19.932000] CFI: Found no "amd76xrom" @ffff0000 device at location zero
[   19.932000] JEDEC: Found no "amd76xrom" @ffff0000 device at location zero
[   19.932000] CFI: Found no "amd76xrom" @ffff0000 device at location zero
[   19.932000] JEDEC: Found no "amd76xrom" @ffff0000 device at location zero

Does anybody have any clue what the issue might be here?

thank you

---

