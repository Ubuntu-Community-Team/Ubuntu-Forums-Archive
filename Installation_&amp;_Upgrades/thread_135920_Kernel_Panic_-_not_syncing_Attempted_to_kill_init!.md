---
title: "Kernel Panic - not syncing: Attempted to kill init!"
date: 2006-02-24
forum: Installation &amp; Upgrades
---

### Post by MikeE99 on 2006-02-24
Hi all,

I am desperately trying to get away from Bill Gates and the whole DMCA scene, but I cannot get my Dell Inspiron 3500  to complete an installation of Ubuntu Linux.  I get the title error message at the end of a screen full of what look like DOS commands on boot off CD.  Changing to expert install does not change the result.

The machine is a standard issue P3 with a non-standard 10 Gb hard drive and 256 Mb of RAM.

Can anyone help me understand what is wrong, and how to complete the installation?

Thanks in advance, 

Mike

---

### Post by K.Mandla on 2006-02-25
Hi. I was getting similar kernel panic errors when I installed an oversize (20GB) drive in an old CTX laptop. Best I can figure, it had something to do with the size of the drive and the BIOS limit on hard drive capacity. 

For me, the problem didn't come back after a reboot. So when I saw it, I would just restart. 

Do you usually install a dynamic drive overlay when you use that drive and laptop with Windows? Do you have a normal-size (for your laptop) hard drive you can test it with?

Sorry I can't be more help than that. Good luck.

---

### Post by Trab on 2006-02-25
for me when i had that issue, everything pointed to a bad RAM...
but i later found out that my newly installed fan was pissing it off...
heres something you can try, find/make a LiveCD and boot off of it... if it works fine, then we can isolate the issue...
otherwise...
well, we can still try?

---

### Post by MikeE99 on 2006-02-26
[QUOTE=K.Mandla]Hi. I was getting similar kernel panic errors when I installed an oversize (20GB) drive in an old CTX laptop. Best I can figure, it had something to do with the size of the drive and the BIOS limit on hard drive capacity. 

For me, the problem didn't come back after a reboot. So when I saw it, I would just restart. 

Do you usually install a dynamic drive overlay when you use that drive and laptop with Windows? Do you have a normal-size (for your laptop) hard drive you can test it with?

Sorry I can't be more help than that. Good luck.[/QUOTE]

Hi K,

I do not use a dynamic drive overlay and I believe the 10Gb drive is within the machine's capabilities.  Unfortunately for me the problem always comes back and I can never complete an Ubuntu installation.  The drive did work fine under Windows for a number of years.

Do you have any idea what the error message means?

Looking forward to hearing from you,

Mike

---

### Post by MikeE99 on 2006-02-27
[QUOTE=Trab]for me when i had that issue, everything pointed to a bad RAM...
but i later found out that my newly installed fan was pissing it off...
heres something you can try, find/make a LiveCD and boot off of it... if it works fine, then we can isolate the issue...
otherwise...
well, we can still try?[/QUOTE]


Hi Trab,

I downloaded and burned both the live ISO and the boot/install ISO images, but the result remains the same; "Kernal panic - not syncing: Attempted to kill init!".

Any thoughts?

---

### Post by AGS on 2006-02-27
As far as I know a kernel panic points to defect hardware. I'm not a crack at this topic, but a few weeks ago I found defect RAM on a friends machine that was  responsible for several months of reboot after the computer worked itself warm. Everyone thought the HD was about to give it up, but after replacing the RAM the system worked just fine 'till today.

Hope this helped a little bit :-k

---

### Post by MikeE99 on 2006-02-27
[QUOTE=AGS]As far as I know a kernel panic points to defect hardware. I'm not a crack at this topic, but a few weeks ago I found defect RAM on a friends machine that was  responsible for several months of reboot after the computer worked itself warm. Everyone thought the HD was about to give it up, but after replacing the RAM the system worked just fine 'till today.

Hope this helped a little bit :-k[/QUOTE]

Thanks to Trab and AGS,

I ran hardware diagnostics and found RAM errors.  After reseating the RAM and rerunning diagnostics, all passed.  The install disk now progresses to the language screen without the Kernel Panic.

Thanks again

---

