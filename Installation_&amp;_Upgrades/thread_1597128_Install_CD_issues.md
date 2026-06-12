---
title: "Install CD issues"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by dhavalbbhatt on 2010-10-15
Hi all -
Completely frustrated with the new 10.10 64bit release - and I haven't even used the OS! I have downloaded almost every version of 10.10 64bit (alternate, desktop, using bittorrent, regular download from the website) and burned CDs using slowest speeds, maximum speeds, other Linux distros, Windows - but I can't seem to get the OS loaded onto my machine! The alternate version goes all the way to loading the kernal and then bombs out. The desktop version stalls at the partitioner. I am not sure what is going on - but this is completely frustrating. I am not sure what else I should be trying. 


Anyone have any clue? Any help will be greatly appreciated.

Thanks,
Dhaval

---

### Post by eltonw on 2010-10-15
> **dhavalbbhatt said:**
> Hi all -
Completely frustrated with the new 10.10 64bit release - and I haven't even used the OS! I have downloaded almost every version of 10.10 64bit (alternate, desktop, using bittorrent, regular download from the website) and burned CDs using slowest speeds, maximum speeds, other Linux distros, Windows - but I can't seem to get the OS loaded onto my machine! The alternate version goes all the way to loading the kernal and then bombs out. The desktop version stalls at the partitioner. I am not sure what is going on - but this is completely frustrating. I am not sure what else I should be trying. 


Anyone have any clue? Any help will be greatly appreciated.

Thanks,
Dhaval

Does your computer have an AMD processor? The 64-bit release is meant for AMD machines only.
If your processor is INTEL, then you have downloaded the wrong iso images.

HTH...

---

### Post by varangian on 2010-10-15
> **eltonw said:**
> Does your computer have an AMD processor? The 64-bit release is meant for AMD machines only.
If your processor is INTEL, then you have downloaded the wrong iso images.

HTH...

This is nonsense, the amd64 tag for the iso is just historical as AMD were the original developers of the 64 bit extensions. Intel later licensed the technology and there's been further development and cross-licensing but the upshot is both AMD's and Intel's consumer 64 bit processors are compatible with the Ubuntu 64bit releases. As can be seen [[COLOR="Blue"]here[/COLOR]]("https://help.ubuntu.com/community/32bit_and_64bit") or just by going to the Ubuntu download page where, if you select the 64 bit version, you get the amd64 iso without any need to specify a CPU manufacturer.

As to the OP's question I've had similar issues with the 64 bit (I've yet to try a live CD for the 32 bit so maybe that's better) and as far as I can see at the moment nobody does have a clue.

---

### Post by dhavalbbhatt on 2010-10-15
> **eltonw said:**
> Does your computer have an AMD processor? The 64-bit release is meant for AMD machines only.
If your processor is INTEL, then you have downloaded the wrong iso images.

HTH...

The AMD64 is not for AMD machines only - it for 64bit architecture, regardless of whether the chip manufacturer is AMD or Intel. 

Dhaval

---

### Post by dhavalbbhatt on 2010-10-15
> **varangian said:**
> 

As to the OP's question I've had similar issues with the 64 bit (I've yet to try a live CD for the 32 bit so maybe that's better) and as far as I can see at the moment nobody does have a clue.

As a last resort, I downloaded the DVD version of 10.10 64bit and I will try that out tonight. If that does not work out, then I will have to go back to LTS version and wait for one of the variants to move up to 10.10 and install the variant at that point.

Sad to see I am not alone here....

Thanks for the replies.

Dhaval

---

### Post by VMC on 2010-10-15
> **dhavalbbhatt said:**
> Hi all -
Completely frustrated with the new 10.10 64bit release - and I haven't even used the OS! I have downloaded almost every version of 10.10 64bit (alternate, desktop, using bittorrent, regular download from the website) and burned CDs using slowest speeds, maximum speeds, other Linux distros, Windows - but I can't seem to get the OS loaded onto my machine! The alternate version goes all the way to loading the kernal and then bombs out. The desktop version stalls at the partitioner. I am not sure what is going on - but this is completely frustrating. I am not sure what else I should be trying. 


Anyone have any clue? Any help will be greatly appreciated.

Thanks,
Dhaval

The "clue" might be inside "/var/log/installer". Read the files there.

Also list some of your hardware - ram, video. From a Terminal running "dmidecode" might reveal some hidden stuff.

---

### Post by dhavalbbhatt on 2010-10-16
> **dhavalbbhatt said:**
> As a last resort, I downloaded the DVD version of 10.10 64bit and I will try that out tonight. If that does not work out, then I will have to go back to LTS version and wait for one of the variants to move up to 10.10 and install the variant at that point.

Sad to see I am not alone here....

Thanks for the replies.

Dhaval


I finally managed to get the DVD version going. It wasn't smooth by any means, but it has worked!!

Thanks,
Dhaval

---

