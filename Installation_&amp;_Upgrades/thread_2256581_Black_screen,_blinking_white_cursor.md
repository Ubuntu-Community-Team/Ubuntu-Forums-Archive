---
title: "Black screen, blinking white cursor"
date: 2014-12-13
forum: Installation &amp; Upgrades
---

### Post by cindylo on 2014-12-13
So I have an older Dell E521 with BIOS version 1.1.4 and i've been trying to boot into ubuntu and elementary OS to try/install one and neither work. They both have the blinking white bar in the top left hand corner forever. Any ideas?

---

### Post by sudodus on 2014-12-13
I think there are two problems (if the following specs are correct)

[http://www.pcworld.com/product/29437/dell-dimension-e521.html](http://www.pcworld.com/product/29437/dell-dimension-e521.html)

1 - The CPU and RAM do not manage to run standard Ubuntu with Unity. You will have better luck with two lighter flavours of Ubuntu

***Xubuntu*** - medium light desktop environment (actually needs 1 GB RAM to work well)
***Lubuntu*** - ultra light desktop environment (needs 512 MB RAM to work well)

2 - the nvidia chip/card - there might be problems with the built-in graphics driver. You might get the computer run with basic graphics, if you boot with the boot option **nomodeset**, or some other boot option according to this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Then you should be able to install a proprietary nvidia graphics driver, and with some luck, you will find one driver that works reasonably well.

Start trying with the version ***14.04.1 LTS***, and if no luck, try ***12.04.5 LTS***.

Lubuntu 12.04 had no LTS (long time support) and has passed end of life. You might try ***LXLE, Bodhi ***or*** Bento*** (versions based on Ubuntu 12.04 LTS).

Maybe you want to try ***ToriOS***, which is not yet released, but a very promising ultra light weight distro also based on Ubuntu 12.04 LTS.

---

### Post by cindylo on 2014-12-13
While this is true it should still get past the blinking white cursor and to the actual boot menu. Also it has 4.5gb of ram, a 8400GS and a Athlon 64 X2 3800+ CPu so it should run ubuntu.

---

### Post by sudodus on 2014-12-14
Thats good, your computer is more powerful than what is described in that link. So it is a good idea to try standard Ubuntu, but I think it is still worthwhile to try Xubuntu. You might like it.

The blinking cursor might be caused by problems between the graphics driver and the graphics chip/card. Try boot options according to post #2.

It that helps, and you get at least some low resolution graphics, try to install an nvidia driver via the ***Software Center***.

If only text mode, try the following command

```
sudo apt-get install nvidia-[TAB]
```

where [TAB] means that you press the TAB key to get possible completions of the command line. I get the following completions in Ubuntu 12.04.5 LTS, where I have high-lighted manually the drivers, which I think are worth trying first (I use nvidia-304, actually NVIDIA 304.125 for GeForce GT 430/PCIe/SSE2). But any of the drivers might work in your case, even some experimental or updates version.

```
[COLOR=#ff0000]nvidia-173[/COLOR]                        nvidia-331-updates-uvm            nvidia-current-updates-dev
nvidia-173-dev                    nvidia-331-uvm                    nvidia-experimental-304
nvidia-173-updates                [COLOR=#ff0000]nvidia-96[/COLOR]                         nvidia-experimental-304-dev
nvidia-173-updates-dev            nvidia-96-dev                     nvidia-experimental-310
[COLOR=#ff0000]nvidia-304[/COLOR]                        nvidia-96-updates                 nvidia-experimental-310-dev
nvidia-304-dev                    nvidia-96-updates-dev             nvidia-opencl-dev
nvidia-304-updates                nvidia-cg-toolkit                 nvidia-prime
nvidia-304-updates-dev            nvidia-common                     nvidia-settings
[COLOR=#ff0000]nvidia-319[/COLOR]                        nvidia-compute-profiler           nvidia-settings-304
nvidia-319-dev                    nvidia-cuda-dev                   nvidia-settings-304-updates
nvidia-319-updates                nvidia-cuda-doc                   nvidia-settings-319
nvidia-319-updates-dev            nvidia-cuda-gdb                   nvidia-settings-319-updates
[COLOR=#ff0000]nvidia-331[/COLOR]                        nvidia-cuda-toolkit               nvidia-settings-experimental-304
nvidia-331-dev                    [COLOR=#ff0000]nvidia-current[/COLOR]                    nvidia-settings-experimental-310
nvidia-331-updates                nvidia-current-dev                nvidia-settings-updates
nvidia-331-updates-dev            nvidia-current-updates            

```

Let us hope that someone who is running linux with the same or a similar graphics chip as you will reply and give advice: ***nvidia Geforce 8400GS***

---

### Post by cindylo on 2014-12-14
That chip works fine from experience in the past unless it changed, and apparently the system just won't boot from USB. I burned a elementaryOS cd and it booted that fine. Now I have to find a way to burn ubuntu onto a CD.

---

### Post by sudodus on 2014-12-14
The Ubuntu desktop iso file is too big for a CD. You need a DVD (or try again with USB).

---

### Post by cindylo on 2014-12-14
Or I could go with an older iso of ubuntu and update it. They also have CD ready ISOs for 12.04 or 12.10, can't remember which.

---

### Post by sudodus on 2014-12-14
What you can do is to make a Lubuntu CD (I think Lubuntu 14.04.1 LTS is still CD sized).

Or you can start from the Ubuntu ***mini.iso***, but only in BIOS mode. It cannot be install alongside Windows in UEFI mode. I guess your computer is running old enough to run in BIOS mode, so maybe it is the best alternative. You can install ***all desktop environment flavours as well as Ubuntu Server*** from the mini.iso.

See this link (Lubuntu, but it works also for the other flavours)

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

---

