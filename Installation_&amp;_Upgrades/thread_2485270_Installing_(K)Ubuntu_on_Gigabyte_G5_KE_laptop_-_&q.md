---
title: "Installing (K)Ubuntu on Gigabyte G5 KE laptop - &quot;nouveau 0000:01:00.0: DRM: failed&quot;"
date: 2023-03-24
forum: Installation &amp; Upgrades
---

### Post by summerrain1 on 2023-03-24
Hello, 1st post here.

When I boot from a freshly written USB stick with Kubuntu 22.04 in an attempt to install it as a dual boot after just having installed Windows 10 on half of the internal SSD, in the usual Linux start log, it will get stuck at:[COLOR=#232629][FONT=-apple-system]

[/FONT][/COLOR]```
[FAILED] Failed to start Ubuntu live CD installer
"nouveau 0000:01:00.0: DRM: failed to idle channel 0 [DRM]:"

```

I only found suggestions like these that revolve around installing drivers on an already existing installation, which seem less helpful for my scenario with a bootable USB stick: [https://superuser.com/questions/1750975/nouveau-00000100-0-drm-failed-to-idle-channel-0-drm](https://superuser.com/questions/1750975/nouveau-00000100-0-drm-failed-to-idle-channel-0-drm) .

Is there a way that I can persuade this thing to boot, and install Kubuntu on my laptop?

---

### Post by MAFoElffen on 2023-03-26
It is trying to tell you that your NVidia GPU has more capabilities that the open sourced Nouveau driver can support. That will be fine, once the third party NVidia driver is installed.

When the LiveUSB goes to boot, it will first go to a Grub2 Boot menu. Press <E>, to get into an edit mode. <Arrow-Down> until you get to the line that starts with "linux". <Arrow-Right> until you get to where is says "quiet". Replace the word "quiet" with "nomodeset". Press <Cntrl><X> to continue booting. Use the "Try" option to insure everything runs OK.

After you start the installer, it will come to a screen asking the type of install- Full or Minimal. At the lower portion of that screen, it will have options to download updates during the installation, and to install drivers form third party sources. Ensure that you select the checkbox to Install drivers from third party sources, and it will install your video driver.

---

### Post by summerrain1 on 2023-12-09
Thanks, now trying this again after months being busy with other stuff.

I did the steps you listed, and the only difference in output to before is that, when giving me "[COLOR=#000000][FONT=&amp][FAILED] Failed to start Ubuntu live CD installer", it will *not* also list the nouveau thing - it will simply fail and say nothing about why.

Could I somehow tickle some more info out of it?[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-12-09
Try using the Grub2 option for Try or Install with Safe-graphics?

---

### Post by summerrain1 on 2023-12-10
same as before.

---

### Post by MAFoElffen on 2023-12-10
Did you try with since your GPU is "newer", did you Kubuntu 23.10 (until 24.04 is released)?

---

### Post by summerrain1 on 2023-12-12
Hrm, I guess I'd wait for the next LTS release that I'd rather have on there, though I guess my USB stick can stomach one more erase cycle to "Try..." the in between one, just to check :)

---

