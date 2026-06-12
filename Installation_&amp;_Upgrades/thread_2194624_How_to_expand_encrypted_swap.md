---
title: "How to expand encrypted swap?"
date: 2013-12-19
forum: Installation &amp; Upgrades
---

### Post by ipb on 2013-12-19
Folks,

When I installed Ubuntu 12.04 LTS on this laptop I agreed to the suggestion that the swap should be encrypted.  The CPU is fast enough for this not to be a performance issue etc etc.

However, shortly afterwards (!) I upgraded the RAM, which had a noticeable improvement in performance, as expected, but now the machine has well below the optimum swap space available.  I prefer the UNIX guide of swap=2.5*RAM but would be happy with 2*RAM.  I now have 1*RAM and I am not happy with that.

I cannot find out how to increase the size of the encrypted swap file.

Help please.

Best Regards

Ian

---

### Post by philinux on 2013-12-19
How much ram have you?

See this too. 


[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by grahammechanical on 2013-12-19
You could use System Monitor and see if you are actually using swap and how much. The more memory we have the less the need to swap data to hard disk.

I do not know but I should think that to resize an encrypted swap file we must first remove the encryption. Are you sure that it is the swap partition that is encrypted and not the home folder/partition?

Regards.

---

### Post by ipb on 2013-12-20
> **philinux said:**
> How much ram have you?

See this too. 


[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Thanks - 2GB - machine maxed out.  Swap is being used but, I believe, mainly because there are a lot of browser windows open and idle.

Ian

---

### Post by ipb on 2013-12-20
Yes, System Monitor shows swap being used - nowhere near full but in my old SysV days if you hit the swap limit you got a kernel panic.

You may be right - it might be an encrypted home folder or partition - I followed the install questions and did not add anything that was not a basic option.  However, this must have changed because my two other machines running 12.04 LTS did NOT offer that option so I obviously became confused.

Swap usage is sitting at 283Mb at the moment but has gone up to 600Mb - there are 2Gb of RAM.  100Gb hard disk of which about 20Gb are used so plenty of room.  Swap was running at 90% with 1Gb of RAM for obvious reasons.  BIOS will not support more RAM in any event.  Machine is not routinely swapping and so I suspect that the swap is storing idle process data.

Ian

---

### Post by philinux on 2013-12-20
2gig swap is enough

My laptop and desktop both have 2 gig ram and 2 gig swap.

---

### Post by ipb on 2013-12-20
Yes, and my machine only has 1Gb swap and 2Gb RAM - so I need to increase it but owing to the encryption the usual methods do not seem to apply.

Ian

---

