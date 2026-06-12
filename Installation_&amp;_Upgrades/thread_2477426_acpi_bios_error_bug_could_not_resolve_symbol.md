---
title: "acpi bios error bug could not resolve symbol"
date: 2022-07-24
forum: Installation &amp; Upgrades
---

### Post by wombyte on 2022-07-24
When booting Ubuntu 20.04 I get this issue since I updated today using Ubuntu's auto updater.

[https://ibb.co/MhY6pLt](https://ibb.co/MhY6pLt)

It continues booting after showing this error.

 How can I fix it?

 My system specs:
 Intel I3 10100    
16 GB DDR4 Ram (2666 MHZ)    
Nvidia GTX 1060 (3GB VRam)    
Ubuntu 20.04 (64 bit, Desktop)    
500 GB M.2 SSD Storage

---

### Post by pantazi on 2022-07-24
```
 [COLOR=#000000]sudo nano /etc/default/grub 
```

Change "quiet splash" to "quiet splash loglevel=3"

Save

Then  sudo update-grub[/COLOR]

---

### Post by pantazi on 2022-07-26
Did I help?

---

### Post by tea for one on 2022-07-27
> **pantazi said:**
> Did I help?
Your suggestion was not in vain. It helped me.

These warning messages are somewhat peculiar because it seems to depend on the kernel being used.
The messages started appearing on my PC if I use a kernel later than 5.15.0-33-generic.
```
edited@edited-22-04:~$ ls /boot | grep vmlinuz-
vmlinuz-5.15.0-33-generic  [COLOR="#0000FF"]messages not displayed[/COLOR]
vmlinuz-5.15.0-39-generic  [COLOR="#FF0000"]messages displayed[/COLOR]
vmlinuz-5.15.0-41-generic  [COLOR="#FF0000"]messages displayed[/COLOR]
edited@edited-22-04:~$
```

Anyway, I added the Grub parameter [COLOR="#0000FF"]loglevel=3[/COLOR] and the messages are suppressed.
Nothing untoward has appeared since using your suggestion approx 48 hours ago.

I also read some internet articles about log levels but my eyes glazed over. 
My vision returned after sitting in a comfy chair and sipping a glass of beer.

Thanks for the suggestion.

Couple of bug reports:-
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1981933](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1981933)
[https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-5.15/+bug/1981910](https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-5.15/+bug/1981910)

---

### Post by pantazi on 2022-07-27
Thanks T41, 

Glad it helped, it happened to me on the last update and I remembered reading about the bug. Took a little researching but I found the answer.

As you found, it only suppresses the information but it tidies up the booting up screen.

Appreciate the humour :grin:

---

