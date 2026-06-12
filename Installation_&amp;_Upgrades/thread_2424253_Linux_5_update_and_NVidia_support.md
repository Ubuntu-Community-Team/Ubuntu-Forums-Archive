---
title: "Linux 5 update and NVidia support?"
date: 2019-08-05
forum: Installation &amp; Upgrades
---

### Post by newb-linux-user1 on 2019-08-05
Hi, 

I booted up Linux today and discovered I was no longer operating with a dual screen configuration. After a bit of hair-pulling and not finding a solution within Ubuntu (ie at the desktop),  I rebooted, then selected boot options from the grub screen (I run a dual boot system) , where I discovered that Linux had been updated to 5.x from 4.18.x.

Choosing the 5.x version (also the default Linux boot option) resulted in the single screen @1024x768 issue once again.

I then rebooted and chose the 4.18.x version and voila, I was back in business with a pair of 1920x1024 screens.

Can anyone explain what's going on with Linux 5 that's killing off my dual screen, and perhaps point me to a solution? I'd like to stay up-to-date, but my workflow really requires more than one screen, and far more than a 1024x768 display.

I'm also quite "newb" in Linux, so it's no easy task for me to debug this stuff, which indeed is why I'm here instead of simply solving it and moving onto more important matters.

Software and Updates (in the Linux 5.x version) did not show any new updates for the graphics engine. In fact, it said everything was up-to-date.

If it matters (which I suspect it might) my system uses an NVidia GTX 1060 (6G)
And under the 4.18.x invocation it uses the NVIDIA drive metapackage from nvidia-driver-415
(also shows as the driver with 5.x , although there's no option to choose two monitors or change screen res)

BTW, the graphic engine under the Linux 5.x invocation (in details > about) shows a different graphics system, something called "Gallium", whereas under Linux 4.18.x (technically: Linux 4.18.0-25-generic x86_64) it shows GeForce GTX 1060 6GB/PCIe/SSE2

thanks in advance

---

### Post by CatKiller on 2019-08-05
> **newb-linux-user1 said:**
> I discovered that Linux had been updated to 5.x from 4.18.x.

You have deliberately opted-in to the Hardware Enablement Stack. The only reasons to do that are because you have newer hardware that requires it, or you particularly like testing new software.

> I'd like to stay up-to-date

Up-to-date means applying all the security patches. 4.15 (the 18.04 kernel) and 4.18 (the 18.04.2 kernel) will get exactly the same security patches as the 5.0 HWE kernel. For a work machine you really don't want to be shunted to a different kernel branch, which is why that's opt-in. You could stay on the initial 4.15 branch for the full five years of support, and you'd still get all the security updates. I have no idea if 5.0 is planned to be a default for a future point release, but the bug-testing of intrepid users running the HWE stack will help make that possible.

> If it matters (which I suspect it might) my system uses an NVidia GTX 1060 (6G)

It absolutely does.

The Nvidia proprietary driver requires a kernel module to be installed for the kernel that you're running. It used to be the case that you needed to reinstall that module for every single kernel update. Then DKMS was invented, which rebuilds the module on the fly when you update the kernel, and that helped enormously. However, it is still fragile to mismatches between compiler versions and options for both the computer where the driver was built and your computer where the kernel module is being built.

There are two approaches that should work. You can come off the HWE stack and stay with the 4.18 branch. That works for you, and you'll still receive all the security updates until it's time to upgrade to 20.04. The other option is to reinstall the Nvidia driver, which should rebuild the DKMS kernel module for you so that your driver can load again. If the installation fails, it may well give you further information that will help you fix it.

---

### Post by newb-linux-user1 on 2019-08-05
"[COLOR=#000000]You have deliberately opted-in to the Hardware Enablement Stack. The only reasons to do that are because you have newer hardware that requires it"[/COLOR]

[COLOR=#000000]Ah...I see... Yes, I don't recall choosing to on my own", specifically because getting the OS installed was difficult to start with, and my lack of experience within Linux really doesn't make me a good candidate for an "experimental" environment, so I'm guessing it was for some reason mandated or triggered due to a hardware element. And Afaik, I chose the stable option when I installed. In fact, I just had a look at the **Software & Updates** tool, and in the developer options tab, Pre-release updates (bionic-proposed) is unchecked, and Live Patch is off, so it must be due to some other setting or trigger.

In any case, thanks for the reply[/COLOR] and suggestions for resolving the issue.[COLOR=#000000] (and thank you for being so prompt. I honestly didn't expect such a quick reply... major kudos to you) 

Yes, I intend to stay on 4.18.x for now. With all due respect and _no insult intended_ to all those who involve themselves in the continuous development, I don't have time to "play" right now. Nor, to be honest, do I have proper Linux Skills. I'm a long way from being an asset to the Linux development team. I'll have to wait a while before I try installing a new graphics driver. Getting that one installed and working was a bit of a headache in the first place, and I can't afford more delays right now.

If I can ask one more followup question, how do I "come off the [/COLOR][COLOR=#000000]HWE stack' ?


[/COLOR]

---

### Post by CatKiller on 2019-08-05
> **newb-linux-user1 said:**
> [COLOR=#000000]If I can ask one more followup question, how do I "come off the [/COLOR][COLOR=#000000]HWE stack' ?[/COLOR]

There are three parts to the HWE stack: the newer kernel, the newer version of the X server, and the newer version of Mesa. They're all interrelated, and they're named in the package manager with *hwe*. If you have Synaptic installed, you can just search in there for "hwe". It's a very useful tool.

Assuming you're using the *generic* kernel (there are other options: I use the *lowlatency* kernel, for example) the package that you'd want to remove is probably the **linux-generic-hwe-18.04** package. That should also remove the respective -image, -headers, and -tools packages, too, and potentially HWE versions of the X server and Mesa.

You may also need to reinstall the **linux-generic** metapackage to ensure that you still get updates for your non-HWE kernel. Since you *do* still have the 4.18 kernel available to boot into, you probably still have that metapackage installed, but it's worth checking. The thing you want to avoid is removing *all* the kernels: that would mean that you wouldn't have anything to boot into at all, which is a pain. Fixable, but a pain. Also check that you have the **linux-image-generic**, **linux-headers-generic**, and **linux-tools-generic** metapackages installed if the HWE equivalents are being removed.

The same with the X server and Mesa packages: if it *does* remove any HWE packages, you want to make sure that you still have the non-HWE equivalents. I *think* those two parts depend on each other, and the kernel, but the kernel doesn't depend on those: you could have installed either just the kernel or the whole stack when you were having trouble installing the Nvidia driver previously.

With all of that done, you *should* be able to just carry on booting into the 4.18 branch, and still get all your security updates, without being pushed to a different kernel branch till 20.04. It probably took longer to type out what you need to do than it will take you to actually do it.

---

### Post by Impavidus on 2019-08-06
> **CatKiller said:**
> You have deliberately opted-in to the Hardware Enablement Stack. The only reasons to do that are because you have newer hardware that requires it, or you particularly like testing new software.

I wouldn't say "deliberately opted-in". If you install Ubuntu using the 18.04.2 live disk image, that happens automatically. The older 18.04.1 live disk image is available somewhere, but a bit harder to find and most new users wouldn't be aware of it.

The 4.18 kernel is dead now. You can either upgrade to 5.0 (to stay on the HWE stack) or downgrade to 4.15 (to drop out of the HWE stack). To downgrade, install (assuming you use the generic kernel) the package **linux-generic**. That should pull in some other packages, including linux-image-generic, linux-headers-generic etc. Reboot and use the grub menu to boot the 4.15 kernel. The 5.0 kernel will still be the default. Test it. If the 4.15 kernel works, you can remove the 5.0 and 4.18 kernels.

---

### Post by CatKiller on 2019-08-06
> **Impavidus said:**
> I wouldn't say "deliberately opted-in". If you install Ubuntu using the 18.04.2 live disk image, that happens automatically. 

Fair enough. I thought that the 18.04.2 image just gave you the updated versions that *had* been in the previous HWE stack, rather than putting new users on the upgrade treadmill. If I was mistaken on that, which does seem to be the case, that seems to me to be a bad decision from the Ubuntu devs.

---

