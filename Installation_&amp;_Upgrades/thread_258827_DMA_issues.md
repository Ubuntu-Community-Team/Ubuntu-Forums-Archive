---
title: "DMA issues"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by aethernaut on 2006-09-16
When trying to use any of the Live CDs on an older system I'm trying to convert into a testing server the boot process would freeze just after checking for the CD drive.

After burrowing through these forums I eventually found an answer: by hitting F6 and then typing "ide=nodma" before running the CD everything went smoothly.  

note that I haven't a clue what DMA is I just tried what someone else had said worked for them; flying blind as it were.

now I'm trying to install phpmyadmin.  I've uncommented the extra urls in the sources.list and run apt-get update like a good little doobie but when I run apt-get install phpmyadmin the system locks up on me!

after telling me the unpacked file will be 24.3mb and asking me if I want to go ahead the error reads:
75% [working][42949573.210000] hdc: timeout waiting for DMA

I have to hit the reset button on my machine to get out of that error ](*,) 

how do I kill "dma" so I can install phpmyadmin??

and, come to that, what exactly IS DMA anyway?  I assume it's something to do with CD drives?

---

### Post by aethernaut on 2006-09-16
I'll answer my own question: 

```
sudo hdparm -d0 /dev/hdc
```

  will kill DMA which is apparently turned on by default :roll:

Add the following to the end of your hdparm.conf

```
/dev/hdc {
dma = off
}
```

  to keep it that way.
 

  If nothing else Ubuntu is greatly improving my Google-Fu :biggrin:

---

