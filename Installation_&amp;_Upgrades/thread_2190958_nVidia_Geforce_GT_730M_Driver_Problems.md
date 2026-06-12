---
title: "nVidia Geforce GT 730M Driver Problems"
date: 2013-11-30
forum: Installation &amp; Upgrades
---

### Post by iph1ps99 on 2013-11-30
Hey,
I am trying to install Ubuntu on my laptop. Since I would like to play same games I tried to install the driver for my graphics card, because it's only recognizing the onboard graphics card. When I run this command  where I can list my graphics cars, I can see my onboard + the nVidia one. Under drivers there is the nouveau driver installed. I already tried to install that .run file which you get when you download the driver from nVidia's website, but now after logging in my screen is black and I can't do anything on it :(
My Specs: Acer Aspire v3-571g
16GB RAM
1TB harddrive
nvidia Geforce gt 730m

Can somebody give me soome tips to install my driver and how I can get my screen back?
Thanks in advance,
iPh1ps99

---

### Post by iph1ps99 on 2013-12-03
push

---

### Post by oldfred on 2013-12-03
I always suggest using the repository to install video drivers. Only if you have a very new card may the current drive in the repository not be current enough.

Can you boot in Recovery mode, second entry in grub menu, perhaps sub menu?
Are you able to set which video mode you boot in in UEFI/BIOS, or is it automatic?

       Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)

---

### Post by iph1ps99 on 2013-12-04
@oldfred Thanks for helping! For everybody who got the same problem: just use this link: [http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

---

