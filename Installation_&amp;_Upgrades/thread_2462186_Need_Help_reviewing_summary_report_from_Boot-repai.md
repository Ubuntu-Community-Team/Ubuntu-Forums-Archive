---
title: "Need Help reviewing summary report from Boot-repair"
date: 2021-05-15
forum: Installation &amp; Upgrades
---

### Post by spinalshock on 2021-05-15
I tried installing Steam on my Ubuntu 20.04, and it showed up a warning saying essential packages will be removed.
Being a windows user I've never faced this situation before, so I tried responding by Yes, do as I say.
However soon I could no longer open terminal. And on trying to restart, it no longer booted normally.
To fix this I saw ubuntu help site and attempted boot-repair, and this is the dump I get.

[https://paste.ubuntu.com/p/w5D2gTbtQc/](https://paste.ubuntu.com/p/w5D2gTbtQc/)

Clicking on recommended repair gave me the error

"grub-efi-amd64-signed purge cancelled. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]"

Can someone please help me out on what needs to be done? I have some important uncommitted work I'm unable to access due to which I'm reluctant to attempt a clean install.

---

### Post by oldfred on 2021-05-15
I have never installed Steam, so do not know what it wanted to uninstall.

Your configuration looks correct for UEFI install.

What error(s) are you getting?
What brand/model system? What video card/chip?

Can you boot to grub menu & then recovery mode?
Since one install in UEFI mode, you have to press escape between UEFI/BIOS & grub menu to get grub menu. If UEFI fast boot on, you may not have time to press any key & then "cold" boot, not "warm" reboot required.

---

### Post by scorp123 on 2021-05-15
> **oldfred said:**
> I have never installed Steam, so do not know what it wanted to uninstall.

It usually doesn't do that, as far as I am aware.

---

### Post by scorp123 on 2021-05-15
> **spinalshock said:**
>  Can someone please help me out on what needs to be done? I have some important uncommitted work I'm unable to access due to which I'm reluctant to attempt a clean install.

If you can boot into a live session mode (e.g. from the installation DVD / USB stick, select the option for the Live Session ... NOT the installer) you could mount what used to be your **/home** partition and retrieve those files, copy them away. Then install again... And next time: Please don't simply say "Yes" to anything if you don't fully understand the question or the consequences. Especially if you get a warning about important stuff getting removed.

---

### Post by spinalshock on 2021-05-15
Currently using Acer Swift 3 laptop
Other system configuration details are as below:

[ATTACH=CONFIG]288476[/ATTACH]

While the laptop boots up, it automatically enters grub menu after the acer logo where I'm shown 3 options: 

Ubuntu
Advanced options for Ubuntu
and a final option to enter the Bios

Is the recovery mode you speak of a part of the advanced options?

---

### Post by spinalshock on 2021-05-15
Yes, I'll take care to read stuff carefully next time.

What is a live session mode and how do I access it? The moment I boot using a USB stick, it asks me the option of Try Ubuntu (which I entered to use boot-repair) and Install Ubuntu (Which I assume allows me to fresh install, so I have not tried it yet).

---

### Post by spinalshock on 2021-05-15
I downloaded the .deb file from steam website, and followed with the installation. Post which this fiasco happened. Had never faced such a scenario before with Windows application installations where things broke abruptly..

---

### Post by spinalshock on 2021-05-15
> **scorp123 said:**
> If you can boot into a live session mode (e.g. from the installation DVD / USB stick, select the option for the Live Session ... NOT the installer) you could mount what used to be your **/home** partition and retrieve those files, copy them away. Then install again... And next time: Please don't simply say "Yes" to anything if you don't fully understand the question or the consequences. Especially if you get a warning about important stuff getting removed.

Great thanks a lot, with this I was able to get the files I needed and backed them up.

Now I will attempt the recovery option and see if it manages to fix the issues. When I attempted the recovery option last time, it asked for my username and password in a full screen terminal style window. While I know my password, the username is giving me troubles. from an old screenshot I have, I can see the following in the terminal window:

```
wealthy@wealthy-Swift-SF314-52
```

That leads me to believe wealthy should be the username, however using it with my password gives me an incorrect login error..

---

### Post by oldfred on 2021-05-15
Did you update UEFI, which often is requried & then that reset UEFI settings to defaults.
I keep a list for my motherboard as it has multiple settings, some required, some optional that I prefer that always get reset. Now older so UEFI updates are not usually available anymore. 

Acer Swift 3
[https://ubuntuforums.org/showthread.php?t=2427570](https://ubuntuforums.org/showthread.php?t=2427570)

---

### Post by mikewhatever on 2021-05-15
Steam is not known to remove any essentional packages, but if that is what happened, the boot repair tool is unlikely to help. You'll need to use chroot, and reinstall whatever was removed.
It would also be interesting to know how was Steam installed.

---

### Post by spinalshock on 2021-05-15
> **spinalshock said:**
> 
That leads me to believe wealthy should be the username, however using it with my password gives me an incorrect login error..

It is actually causing a login loop. It shows a change very briefly and immediately asks for credentials again, making it seem like they were incorrect.

---

### Post by oldfred on 2021-05-15
I found steam in Ubuntu repository and it shows it wants to uninstall a lot of my software.
And it wants :i386 or 32 bit, so that may be the conflict as I do not have any 32 bit apps installed.

---

### Post by spinalshock on 2021-05-15
I used the same steps inside Try Ubuntu to try and replicate what had happened, however to my surprise nothing broke and steam got installed successfully.
The previous message of following stuff will be removed was not shown.. which leads me to believe that there might have been some conflict with something I might have installed for work? Or is it because those things already no longer exist for them to be removed?

---

### Post by spinalshock on 2021-05-15
This might have been the issue. In my system information settings I see a 64bit os. how do I resolve such issues in the future?

---

### Post by spinalshock on 2021-05-15
> **oldfred said:**
> I found steam in Ubuntu repository and it shows it wants to uninstall a lot of my software.
And it wants :i386 or 32 bit, so that may be the conflict as I do not have any 32 bit apps installed.

This might have been the issue. In my system information settings I  see a 64bit os. how do I resolve such issues in the future?

---

### Post by oldfred on 2021-05-15
Most software has updated to 64 bit.
If Steam updated, that would resolve issue. 
I think if I really wanted Steam, I would create another install, just for it, so I could have all my other 64 bit apps without conflict.

---

### Post by mikewhatever on 2021-05-15
Just tried it, many 32bit packages are installed, which is expected, but nothing is removed. Very strange indeed.
```

~$ sudo apt-get -s install steam
[sudo] password for asus: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  gcc-10-base:i386 libatomic1:i386 libbsd0:i386 libc6:i386 libcrypt1:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libelf1:i386 libexpat1:i386 libffi7:i386 libgcc-s1:i386 libgl1:i386
  libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libglvnd0:i386 libglx-mesa0:i386 libglx0:i386 libgpg-error-l10n
  libgpg-error0:i386 libidn2-0:i386 libllvm11:i386 libpciaccess0:i386 libsensors5:i386 libstdc++6:i386 libtinfo6:i386 libudev1:i386
  libunistring2:i386 libvulkan1:i386 libwayland-client0:i386 libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386
  libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-randr0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386
  libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxinerama1:i386 libxshmfence1:i386 libxss1:i386 libxxf86vm1:i386
  libzstd1:i386 mesa-vulkan-drivers:i386 steam-devices zlib1g:i386
Suggested packages:
  glibc-doc:i386 locales:i386 lm-sensors:i386 libnvidia-gl-390:i386 | libnvidia-gl-435:i386 | libnvidia-gl-440:i386
The following NEW packages will be installed:
  gcc-10-base:i386 libatomic1:i386 libbsd0:i386 libc6:i386 libcrypt1:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libelf1:i386 libexpat1:i386 libffi7:i386 libgcc-s1:i386 libgl1:i386
  libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libglvnd0:i386 libglx-mesa0:i386 libglx0:i386 libgpg-error-l10n
  libgpg-error0:i386 libidn2-0:i386 libllvm11:i386 libpciaccess0:i386 libsensors5:i386 libstdc++6:i386 libtinfo6:i386 libudev1:i386
  libunistring2:i386 libvulkan1:i386 libwayland-client0:i386 libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386
  libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-randr0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386
  libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxinerama1:i386 libxshmfence1:i386 libxss1:i386 libxxf86vm1:i386
  libzstd1:i386 mesa-vulkan-drivers:i386 steam:i386 steam-devices zlib1g:i386
0 upgraded, 58 newly installed, 0 to remove and 8 not upgraded.

```

---

### Post by tea for one on 2021-05-15
> **spinalshock said:**
> I downloaded the .deb file from steam website, and followed with the installation. Post which this fiasco happened. Had never faced such a scenario before with Windows application installations where things broke abruptly..

This may be the clue.....

Steam deb file from the Steam website -v- Steam from the repository

---

