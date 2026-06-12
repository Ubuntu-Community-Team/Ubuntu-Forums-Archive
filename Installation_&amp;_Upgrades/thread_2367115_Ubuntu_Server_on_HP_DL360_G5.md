---
title: "Ubuntu Server on HP DL360 G5"
date: 2017-07-26
forum: Installation &amp; Upgrades
---

### Post by tyoi on 2017-07-26
Dear fellow erm, people.

I've recently saved a HP Proliant DL360 G5 from imminent doom in the trashcan. It has been replaced by some newer hardware. The server is in excelent and working condition (it was running Windows storage server 2012) so I thought to use it as a replacement for my current setup; an old converted desktop machine running a minecraft server for my little brother and a few of his friends, lacking the CPU an RAM capacity needed. 

I've created a bootable usb stick with 16.04 distro and loaded it into the machine. However, when I select "Install Ubuntu server" the screen goes black and nothing happens. The blacklight on the monitor does stay on, and the server doesn't restart or fault giving me the impression it waits for input or something. I've tried the 14.04 and 17.04 distro and the latest debian but with all I experience the same problem. 

No amount of google-ing has helped my effort in solving this issue so I am here, asking suggestions/help.

---

### Post by BenginM on 2017-07-26
Salutations! and welcome to the forums .. What GPU\s is on the machine .. is it dual graphics or only with an on board one!

if you going for a server edition , try using the mini/netboot iso , make sure to verify check the hashes of the iso before burning to the usb.. a wired ethernet is required though . but the installation is fairly simple .. you might need to temporary set the nomodeset kernel boot option #see:

[ATTACH=CONFIG]276148[/ATTACH]
[ATTACH=CONFIG]276149[/ATTACH]

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[https://www.youtube.com/watch?v=U42Ln3k7VK0](https://www.youtube.com/watch?v=U42Ln3k7VK0)

---

### Post by QIII on 2017-07-26
Hello!

Are you installing Ubuntu Server or an Ubuntu desktop flavor?

---

### Post by mastablasta on 2017-07-27
make sure the image you are installing from is a good one.: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

you can also try nethserver (centos/redhat based). i think HPs are usualy certified for Redhat, but some of them have Ubuntu certification as well. nortmally this is not the issue though. also check the BIOS for any strange setting and maybe set it to default (reset the settings)

---

### Post by tyoi on 2017-07-27
Guys (I presume), 

Thank you for the repsones! I managed to figure it out: the USB bootloader thingy I was using didn't create a correct image on the USB stick resulting in the fault. When I used rufus the installation went trough without any hickups (server edition). It's purring nicely now. Only thing that's left on the to do list is making the hibernation work, on which is seems to hang, but I'll do some homework on that before troubling you guys. 

Thanks again

---

### Post by BenginM on 2017-07-27
Glad to know , as for suspend hibernation on RAM 

[https://wiki.ubuntu.com/Kernel/Debugging](https://wiki.ubuntu.com/Kernel/Debugging)

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

