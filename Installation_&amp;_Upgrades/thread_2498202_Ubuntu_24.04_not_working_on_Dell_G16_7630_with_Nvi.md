---
title: "Ubuntu 24.04 not working on Dell G16 7630 with Nvidia drivers"
date: 2024-06-04
forum: Installation &amp; Upgrades
---

### Post by Sainoq on 2024-06-04
My Dell G16 came with Windows and I immediately switched to Ubuntu.

I tried 24.04 (I got it beginning of May) but I had issues with proprietary drivers (535) for the Nvidia 4060 Mobile on board.
On Wayland I get a grey screen, on Xorg it stopped working after a few seconds and rebooting didn't help, it was completely frozen, not even reaching the login.

I installed 23.10 and it worked fine on Wayland with recommended proprietary driver 535.

I waited a month and then did the upgrade from 23.10 to 24.04, it started, but nvidia-smi was not responding, the "additional drivers" page was stuck on "custom driver installation" and I couldn't change anything.
I tried forcing the drivers back to 535 but got the system frozen again.

Now I'm back to 23.10 (Proprietary drivers 535.171.04) which will end support soon.
Official Dell version for the G16 is 22.04, but they don't provide support for Linux

Hardware is the following

Dell G16 7630
[LIST]
[*]I7 13650HX
[*]32GB RAM
[*]Intel Raptor Lake-S UHD Graphics (rev 04)
[*]Nvidia AD107M (GeForce RTX 4060 Mobile) (rev a1)
[/LIST]

Any suggestion? Rollback to recommended 22.04? Wait another month till end of 23.10 support?

I'm not a Linux expert.

Thanks

---

### Post by ubfan1 on 2024-06-04
A tough choice for such new equipment.  Do join the bug at [https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/2037004](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/2037004) so the 545 and 550 (and 555) drivers may be installed successfully.  I'm only able to run the 535 on Ubuntu 24.04 Desktop, the 545 produces an install error from the Software&Updates/additionaldrivers tab. Those three driver packages are present in the graphics-drivers repos, so maybe it's just some install scripts that have trouble. Backup and wait a bit, or maybe try the nouveau driver on your 24.04 install.

---

### Post by Sainoq on 2024-06-04
Thanks for the suggestion. I tried briefly the Nouveau driver and it seems to work fine for the display, but I'm not sure I can use it for AI related stuff like Ollama and Stable diffusion. Does anybody have experience with that?

---

### Post by ubfan1 on 2024-06-04
Take a look at :
[https://forums.developer.nvidia.com/t/solved-run-cuda-on-dedicated-nvidia-gpu-while-connecting-monitors-to-intel-hd-graphics-is-this-possible/47690/2](https://forums.developer.nvidia.com/t/solved-run-cuda-on-dedicated-nvidia-gpu-while-connecting-monitors-to-intel-hd-graphics-is-this-possible/47690/2)

Sometimes you can Use the Intel GPU for display and the Nvidia for CUDA.

---

