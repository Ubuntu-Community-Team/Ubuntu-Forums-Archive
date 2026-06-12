---
title: "Help with OpenGL in an old laptop"
date: 2019-05-14
forum: Installation &amp; Upgrades
---

### Post by bigotinho on 2019-05-14
Hi, I installed Lubuntu 18.0.4 in this 9 year old hp laptop: [https://support.hp.com/au-en/document/c02246342](https://support.hp.com/au-en/document/c02246342)
I tried to play a game I got on steam but it doesn't run at all. This is the log from the game:

```

Desktop is 1366 x 768 @ 60 Hz
Unable to find a supported OpenGL core profile
Failed to create valid graphics context: please ensure you meet the minimum requirements
E.g. OpenGL core profile 3.2 or later for OpenGL Core renderer
[Vulkan init] extensions: count=2
[Vulkan init] extensions: name=VK_EXT_debug_report, enabled=0
[Vulkan init] extensions: name=VK_EXT_debug_utils, enabled=0
Vulkan error VK_ERROR_INCOMPATIBLE_DRIVER (-9) file: ./Runtime/GfxDevice/vulkan/VKContext.cpp, line: 313
Vulkan detection: 0
No supported renderers found, exiting
/home/garcia/.local/share/Steam/steamapps/common/Fantasy Strike/FS_Linux.bin() [0xbc7757]
/home/garcia/.local/share/Steam/steamapps/common/Fantasy Strike/FS_Linux.bin() [0x9d26a0]
/home/garcia/.local/share/Steam/steamapps/common/Fantasy Strike/FS_Linux.bin() [0x990d1e]
/home/garcia/.local/share/Steam/steamapps/common/Fantasy Strike/FS_Linux.bin() [0x451a71]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xe6) [0x7f77d27bbb96]
/home/garcia/.local/share/Steam/steamapps/common/Fantasy Strike/FS_Linux.bin() [0x45d4f0]
 
(Filename:  Line: 590)

```

So I went to [https://01.org/linuxgraphics/downloads/2018q1-intel-graphics-stack-recipe](https://01.org/linuxgraphics/downloads/2018q1-intel-graphics-stack-recipe)
for a driver but my hardware is not in the sported hardware list.

The video driver I got is i915.

And this is what I get from the system profiler:
[ATTACH=CONFIG]283268[/ATTACH]

---

### Post by Impavidus on 2019-05-15
The program complains that it needs at least openGL version 3.2. [This site](https://community.khronos.org/t/opengl-version-for-intel-gma-4500/69648) tells me that your graphics unit only supports openGL 2.1. So it's not going to work. The game needs features in your hardware that aren't present.

---

### Post by bigotinho on 2019-05-15
Thanks, I guess that's it :/

---

