---
title: "Does manually installing HWE depend on your hardware and/or software configuration?"
date: 2015-07-29
forum: Installation &amp; Upgrades
---

### Post by roler2 on 2015-07-29
I went ahead and manually installed HWE on Lubuntu 14.04. Not a good idea. A lot of the Programs stopped working and the ones that did work started to freeze. The Programs that were uninstalled by the HWE upgrade actually would not install, or did not install properly. The computer took twice as long to boot up and was very slow. Both Firefox and Chrome were very very slow. When I tried to reboot back to the default 3.13 kernel I got a black screen.

So I reformatted and reinstalled from scratch. Not a good idea. I also tried the Vivid HWE, which apparently just became available. Same exact issues. 

I have an old P4. Plenty of RAM. Great computer. Just not great with the HWE upgrade. Or maybe the software is not compatable with the HWE upgrade.

So. . .does the HWE upgrade depend on the hardware and/or software configuration?

Now I have to reinstall all over again, however this time I will stick with the default kernel. Unless there is a way to make sure all of the Programs work correctly with the HWE.

Also, apparently qt5 does not work with the HWE upgrade and will not reinstall after the upgrade, neither with the Utopic or the Vivid HWE. Tried and failed with both HWE.

---

### Post by dino99 on 2015-07-29
Do you really need that HWE feature ?

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

---

### Post by grahammechanical on 2015-07-29
Are you running a proprietary video driver? The HWE upgrade will bring in the latest (from the perspective of the Ubuntu maintainers) proprietary video drivers and you may find that these later video drivers no longer support your video adapter. I found that to be true in my case.

Early on in the year I tried to be an early adapter of Linux kernel 4.0 and every time I installed it the OS broke. There was a failure to compile the Nvidia driver and that was happening because the newer Nvidia drivers no longer supported my Nvidia GT220 card.

Here I am running the 15.04 development version and it has Linux kernel 4.0.4 but I use Nvidia 304 driver which is now called a legacy driver. I cannot use later Nvidia drivers. Oh, and thanks to the Ubuntu maintainers who patched something or other so that the 304 driver works with Linux kernel 4.0.4

I am of the opinion that that when upgrading the hardware stack (HWE) or upgrading to a newer version of Ubuntu which has the new hardware stack, that it is always best to do the upgrade using the open source video driver.

Regards.

---

