---
title: "Graphics card driver failed"
date: 2014-08-26
forum: Installation &amp; Upgrades
---

### Post by olly3 on 2014-08-26
Hello, I appear to have a problem with my graphics driver:

```
CPU:       Quad core AMD A8-6410 APU with AMD Radeon R5 Graphics (-MCP-) cache: 8192 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 15970.1            Clock Speeds: 1: 2000.00 MHz 2: 1000.00 MHz 3: 1000.00 MHz 4: 1000.00 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Mullins [Radeon APU A4-6000 with R2 Graphics] bus-ID: 00:01.0 
           X.Org: 1.15.1 drivers: ati (unloaded: vesa,radeon) FAILED: fbdev Resolution: 1366x768@76.0hz 
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits) GLX Version: 2.1 Mesa 10.1.0 Direct Rendering: Yes



```

Note the line "FAILED: fbdev Resolution: 1366x768@76.0hz " . Whenever I try to launch a game from Steam, nothing happens. I suspect this driver failure may be the cause. Unfortunately I don't know what to do about it. 

Any help would be greatly appreciated. 

Thanks in advance.

---

### Post by Yellow Pasque on 2014-08-27
I think that's just saying the fbdev driver failed to load (which is okay). The Steam issue is probably something else. Do you have libgl1-mesa-glx:i386 package installed for 32-bit support?

---

### Post by olly3 on 2014-08-27
Thanks for the reply.

Hmm I don't think so, but I'm not sure how to do it. I searched for[COLOR=#000000]libgl1-mesa-glx:i386 i the package manager, but it said that the package didn't include certain modules :/ Not really sure what this means[/COLOR]

---

### Post by Yellow Pasque on 2014-08-27
```
sudo apt-get install libgl1-mesa-glx:i386 libgl1-mesa-dri:i386
```
Then, try launching Steam from the terminal.

---

### Post by olly3 on 2014-08-27
Hi, I just upgraded the kernel to the latest stable release, 3.16.1 (64bit):
```
olly@olly ~ $ uname -aLinux olly 3.16.1-031601-generic #201408140014 SMP Thu Aug 14 04:15:26 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux



```

Now, when I boot up, I just get a blank screen. However, I can boot successfully in recovery mode. I wonder if anyone could help me resolve this, or should I simply go back to my old kernel?

N.B: The reason I decided to upgrade to the latest kernel is because my new laptop has a quite modern motherboard, so I though the latest kernel might resolve the issues I'm having with my graphics drivers; namely my inability to launch certain games in Steam. Some system info: ```
Machine:   System: Hewlett-Packard product: HP 15 Notebook PC version: 0975100000405F00001620180           Mobo: Hewlett-Packard model: 22CD version: 93.15 Bios: Insyde version: F.16 date: 05/30/2014
CPU:       Quad core AMD A8-6410 APU with AMD Radeon R5 Graphics (-MCP-) cache: 8192 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 15970.4 
           Clock Speeds: 1: 1000.00 MHz 2: 1400.00 MHz 3: 1600.00 MHz 4: 1000.00 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Mullins [Radeon APU A4-6000 with R2 Graphics] bus-ID: 00:01.0 
           X.Org: 1.15.1 drivers: ati (unloaded: vesa,radeon) FAILED: fbdev Resolution: 1366x768@76.0hz 
```

---

### Post by Yellow Pasque on 2014-08-27
> Gallium 0.4 on llvmpipe
Actually, it does look like you have a graphics issue if you're running on llvmpipe. Post your /var/log/Xorg.0.log

You may need better more recent drivers since your hardware is so new. [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

---

### Post by QIII on 2014-08-27
Hello!

Did you have the proprietary ATI driver installed?

If so, how did you install it?

---

### Post by QIII on 2014-08-27
After answering, I see that you had another thread -- and now your initial problem is compounded by an update.

Temügin is extremely knowledgeable and it might have been better to stick with the original line of assistance.

Let's see if we can keep this together now.

Threads merged.

---

### Post by olly3 on 2014-08-27
Hello.   (Sorry for the duplicate posting :oops: )

---

### Post by olly3 on 2014-08-27
> **Temüjin said:**
> Actually, it does look like you have a graphics issue if you're running on llvmpipe. Post your /var/log/Xorg.0.log

You may need better more recent drivers since your hardware is so new. [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

Thanks, I'll give that link a read. By the way, here is the terminal output when I attempt to launch a game:
```
ERROR: ld.so: object '/home/olly/.local/share/Steam/ubuntu12_64/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS64): ignored.Setting breakpad minidump AppID = 8930
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198078712374 [API loaded no]
Game removed: AppID 8930 "Sid Meier's Civilization V", ProcID 5069
```

EDIT: here is my /var/log/Xorg.0.log : [http://pastebin.com/zZxFky7x](http://pastebin.com/zZxFky7x)  (I'm afraid I just copied all of it because I don't know which bit is relevant)

---

### Post by grahammechanical on 2014-08-27
I am guessing that you have hybrid graphics. Can you confirm that?

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

Oh, by the way, booting with Recovery Mode>Resume will get you running on llvmpipe. It is used by Ubuntu 14.04 as an open source fall back video driver. But at least it is getting you to a working desktop.

Is this a new install? 

Regards.

---

### Post by Yellow Pasque on 2014-08-27
```
[    32.092] (EE) open /dev/dri/card0: No such file or directory
[    32.092] (EE) open /dev/dri/card0: No such file or directory
```

You have to find out what's causing the drm kernel module to fail. It could be that your computer needs a newer kernel than what's in Trusty and/or an updated firmware package. Check output of:
```
dmesg | grep -i radeon
```

---

### Post by olly3 on 2014-08-28
```
olly@olly ~ $ dmesg | grep -i radeon[    0.134541] smpboot: CPU0: AMD A8-6410 APU with AMD Radeon R5 Graphics (fam: 16, model: 30, stepping: 01)
[    2.136752] [drm] VGACON disable radeon kernel modesetting.
[    2.138597] [drm:radeon_init] *ERROR* No UMS support in radeon module!
[    7.831385] [drm] VGACON disable radeon kernel modesetting.
[    7.833178] [drm:radeon_init] *ERROR* No UMS support in radeon module!
[   13.984583] [drm] VGACON disable radeon kernel modesetting.
[   13.984590] [drm:radeon_init] *ERROR* No UMS support in radeon module!

```

I did try installing the latest kernel, but it didn't work; I could only boot in recovery.

---

### Post by olly3 on 2014-08-28
> **grahammechanical said:**
> I am guessing that you have hybrid graphics. Can you confirm that?

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

Oh, by the way, booting with Recovery Mode>Resume will get you running on llvmpipe. It is used by Ubuntu 14.04 as an open source fall back video driver. But at least it is getting you to a working desktop.

Is this a new install? 

Regards.

Yes I believe they are hybrid graphics. 

And yeah it's a new install. I'm dual booting 14.04 with windows8.1 on a new HP 15 notebook that I just got. To be honest the whole install has been a bit problematic. On my previous laptop, I had ubuntu dual booted with windows7, and everything worked out of the box more or less. But this install been more of a headache. First off, I had typical problems with EFI; grub wasn't appearing at boot up, so I had to rename some files to trick it into using grub. Then I had problems with the wireless and ethernet drivers, which I think I've now resolved. And now I have this graphics problem, in addition to having no ability to adjust screen brightness. My previous laptop had the brightness issue too and it was resolved by editing /etc/default/grub , but the same fix hasn't worked this time. I'm just hoping to get these little problems ironed out by the time I head back to uni in a couple of weeks :3

---

