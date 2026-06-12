---
title: "Monitor unknown after upgrading to 18.04"
date: 2018-05-27
forum: Installation &amp; Upgrades
---

### Post by ubuntini2 on 2018-05-27
Hi
Have been running Ubuntu Mate 17.10 and just upgraded to 18.04 LTS.
But after upgrading my monitor settings are all wrong and can't set the proper resolution.
How can I resolve this?

The results of the following command  lspci -nnk | grep -i vga -A3
43:00.0 VGA compatible controller [0300]: NVIDIA Corporation GV100 [10de:1d81] (rev a1)
    Subsystem: NVIDIA Corporation GV100 [TITAN V] [10de:1218]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_390, nvidia_390_drm





[ATTACH=CONFIG]279880[/ATTACH]

---

### Post by amvitty on 2018-05-27
> **ubuntini2 said:**
> Hi
Have been running Ubuntu Mate 17.10 and just upgraded to 18.04 LTS.
But after upgrading my monitor settings are all wrong and can't set the proper resolution.
How can I resolve this?

The results of the following command  lspci -nnk | grep -i vga -A3
43:00.0 VGA compatible controller [0300]: NVIDIA Corporation GV100 [10de:1d81] (rev a1)
    Subsystem: NVIDIA Corporation GV100 [TITAN V] [10de:1218]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_390, nvidia_390_drm





[ATTACH=CONFIG]279880[/ATTACH]
To fix unknown display problem in Ubuntu/Mint open Terminal (Press Ctrl+Alt+T) and copy the following commands in terminal:
sudo apt-get install mesa-utils
After installation reboot and enter following command in terminal to check display info:
Terminal Commands:
glxinfo | grep render
glxgears

That's it.

---

