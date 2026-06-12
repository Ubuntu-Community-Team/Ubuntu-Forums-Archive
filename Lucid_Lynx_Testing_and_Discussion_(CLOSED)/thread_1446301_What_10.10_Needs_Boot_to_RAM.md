---
title: "What 10.10 Needs: Boot to RAM"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Cobmojo on 2010-04-03
10.10 needs a 'boot to ram' option for it's install. Imagine Ubuntu (or maybe just Lubuntu) running on RAM like Puppy Linux and open apps in a blink of an eye. 
Most computers can handle it these days. I just bought my desktop with 8gb of RAM on it just aching for some action.
It would take some effort to get it all streamlined making it friendly to newer users.

I know it's already possible on the current Ubuntu with some work. But, I'm talking about making it a user-friendly option from the get-go.

Now we've got the LTS out of the way it's time to have a little fun. What do you guys think? Stupid? 


fyi: [https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)

---

### Post by Arand on 2010-04-03
Already possible with the Lucid liveCD by adding TORAM=yes to the kernel boot line.
As for easily running an installed system that way, interesting idea.
But I don't see it as really coinciding with the design direction of ubuntu, because of it's rather specialised nature.
Also, we'd throw away the boot speed advantage just gained with 10.04.
- Arand

---

### Post by Sef on 2010-04-03
Moved to Lucid.

---

### Post by Stason on 2010-04-04
> **Arand said:**
> Already possible with the Lucid liveCD by adding TORAM=yes to the kernel boot line.
As for easily running an installed system that way, interesting idea.
But I don't see it as really coinciding with the design direction of ubuntu, because of it's rather specialised nature.
Also, we'd throw away the boot speed advantage just gained with 10.04.
- Arand

Loading kernel to RAM would help for sure, but also loading /usr/share /usr/lib and may be something more into RAM does speed things up considerably at the expense of additional 30 sec boot time, which can be cut by skipping the boot up splash/plymouth routines.

---

