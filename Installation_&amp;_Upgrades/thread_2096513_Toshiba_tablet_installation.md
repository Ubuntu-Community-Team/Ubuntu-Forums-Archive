---
title: "Toshiba tablet installation"
date: 2012-12-20
forum: Installation &amp; Upgrades
---

### Post by aames13 on 2012-12-20
I have a Toshiba Excite 10 tablet that I'm trying to put Ubuntu 12.10 on as a project... which wouldn't be an issue if I knew which version to download. It has an NVIDA Tegra processor, and I don't know if either of the versions will work for it. I would simply create a bootable USB and see which works, but the Excite doesn't have a standard USB port, so before I go about using an SD card or trying to find something to plug into the microUSB port, I figured I'd ask here... words of wisdom from anyone?

---

### Post by Mark Phelps on 2012-12-20
Looked at the specs for your tablet -- that's really NICE!

So, if it was MY tablet, I would do the following BEFORE messing around with installing Ubuntu:
1) Go to the Android forums and the Phandroid forums
2) See if they have any sections dealing with your tablet
3) See if you can get help from them regarding how to image off your tablet in such a way that you can completely restore it to its current working state.

Since you can't (at present) boot from a Linux distro to see how well it works, forcing an install on the Tablet runs a high risk of turning it into a 10-inch glass placemat.

You should at least find out how to save and restore it so that, in worst case, you can get your working Tablet back.

---

### Post by aames13 on 2012-12-21
It's certainly not bad, although I have the version with less internal storage. I really dislike the Android OS though which is why I wanted to try Ubuntu on it.... I just didn't realize it had an NVIDA processor until I read up more. I'll try the pages you recommended.

---

### Post by cwsnyder on 2012-12-21
It looks like from [http://www.nvidia.com/object/tegra-superchip.html](http://www.nvidia.com/object/tegra-superchip.html) that the Tegra chips are integrated on an ARM Cortex-A9 processor, so you will need Ubuntu on Android or Ubuntu on ARM to even _attempt_ to replace Android with Ubuntu.

---

### Post by grahammechanical on 2012-12-21
There an official **experiment** going on to get Ubuntu running on a Nexus 7. Which has a Nvidia Tegra 3 t30l system chip and Quad core, 1200 MHz, ARM Cortex-A9 processor.

[https://wiki.ubuntu.com/Nexus7/Installation]("https://wiki.ubuntu.com/Nexus7/Installation")

[https://wiki.ubuntu.com/Nexus7]("https://wiki.ubuntu.com/Nexus7")

Note this comment from the FAQ

> Will this image work on the Nexus 10?

No, this image will not work. The Nexus 10 has a completely different SoC (Samsung exynos vs. nVidia tegra3).


This sort of thing is fine when there is official Ubuntu leadership and development. It becomes very risky when you are testing this alone. It would be nice if things were simple. But they are not.

Regards.

---

