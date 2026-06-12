---
title: "Will Windows Recovery Partition Still Work?"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by Skaa on 2010-02-13
A quick introduction:
I have a small amount of experience with ubuntu and after some recent problems with windows on both my computers I want to give ubuntu a try on my laptop. However, I also want the option to revert to windows if I eventually decide that ubuntu is not for me.

Windows (vista) came pre installed on my laptop with a recovery partition that allows me to reinstall windows if necessary. It is accessed on startup by pressing one of the function keys (i forget which one). Does anybody know if I install ubuntu on the main partition of my laptop will I still be able to run the windows reinstallation program?

[I have already tried the live CD and wubi, which have persuaded me to give ubuntu a chance at full install]

Thanks in advance

---

### Post by lenoirrichelieu on 2010-02-13
You should have any problems if you don't touch that partition by any means.
But if you are still undecided stay a bit more on wubi instalation.

---

### Post by darkod on 2010-02-13
Yes, it should still work in most cases. It would depend how it's set up and it's difficult to say like this not even seeing the computer.
If you have a manual, check whether you can create restore DVDs from that partition and then you don't have to keep it any more. The DVDs would be able to boot your computer and restore vista, the same job as the partition.
In most cases you should be able to create DVDs from the partition.

I would also consider making an image of your vista, and then you can restore from this image without any loss to any of the other partitions. MS is doing a very unfair thing by not providing install media any more, and manufacturers can only offer restore partition. But this partition is usually wiping the whole hdd and creating the factory layout.

For example, you have C: system partition and D: data windows partition. With windows install media you can reinstall vista on C: but keep your D: intact. With the restore partition you lose D: and all data on it too. Is that a restore you would like to do? Also with an image of C: you can restore only C:, not touching D:.

Wiping the whole drive by the restore partition is becoming even a bigger problem when dual booting because it will destroy your other OS too which might be working perfectly.
Consider your options and make a decision what works for you best, but I wouldn't keep that partition much longer.

---

### Post by ask4Prasath on 2010-02-13
Hi 
Am using ubuntu for a year 
Now am getting some prob 
am unable to boot it is showing 
init rcefault(2111) main process terminated

thanks in advance

---

### Post by darkod on 2010-02-13
> **ask4Prasath said:**
> Hi 
Am using ubuntu for a year 
Now am getting some prob 
am unable to boot it is showing 
init rcefault(2111) main process terminated

thanks in advance

And how is that related to this thread? Please open your own thread.

---

