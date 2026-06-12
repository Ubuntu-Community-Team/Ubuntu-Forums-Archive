---
title: "Grub error 18 after fresh 7.04 install"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by Jim Darrough on 2007-05-31
I have been happily running Ubuntu 6.06lts on my Compaq Evo N620c for some time. I managed to get hold of another laptop hd and attempted to install 7.04 but am running into problems and could use some help.

First one was that I had to wait while 7.04 times out attempting to find the non-existent floppy drive. Once the Live CD boots up, it seems to detect the wireless card (I tried a Buslink 54g PCMCIA and the installed Orinoco wireless device) but won't let me activate it. 

After running the install program, the system does the normal stuff but seems to think my HD is a SCSI one. It LOOKS like it writes the new system to the HD but when I reboot, I get Grub Error 18. 

Any suggestions? I tried Kubuntu and Ubuntu with the same result. 

Thanks, Jim Darrough

---

### Post by confused57 on 2007-05-31
> **Jim Darrough said:**
> I have been happily running Ubuntu 6.06lts on my Compaq Evo N620c for some time. I managed to get hold of another laptop hd and attempted to install 7.04 but am running into problems and could use some help.

First one was that I had to wait while 7.04 times out attempting to find the non-existent floppy drive. Once the Live CD boots up, it seems to detect the wireless card (I tried a Buslink 54g PCMCIA and the installed Orinoco wireless device) but won't let me activate it. 

After running the install program, the system does the normal stuff but seems to think my HD is a SCSI one. It LOOKS like it writes the new system to the HD but when I reboot, I get Grub Error 18. 

Any suggestions? I tried Kubuntu and Ubuntu with the same result. 

Thanks, Jim Darrough
Here are some possible solutions for grub error 18:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

If it's an older bios, you might need to set up a small boot partition(approx 100 Mb) at the beginning of the hard drive.

---

### Post by Jim Darrough on 2007-06-07
I wanted to thank the reference to Super Grub disk. It allowed me to edit the MBR and boot into the new installation however, for some reason my system thinks it's 6.06lts. Not sure where I went wrong.

But it does boot! 

Thanks, Jim

---

