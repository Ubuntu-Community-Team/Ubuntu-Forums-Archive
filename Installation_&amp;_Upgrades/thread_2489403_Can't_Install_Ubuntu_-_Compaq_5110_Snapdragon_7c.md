---
title: "Can't Install Ubuntu - Compaq 5110 Snapdragon 7c"
date: 2023-07-28
forum: Installation &amp; Upgrades
---

### Post by hugomarcelodasilva on 2023-07-28
Hello. I have a Compaq 5110 with Snapdragon 7c and Windows 11 64bits. I tried to install Ubuntu AMD64 via Etcher, Rufus, Yumi, Universal, Win32 Disk burners and others, but I can't boot my pendrive, which has 32GB free.
I tried to install the Ubuntu ARM64 ISO on the pendrive, and the device even starts, but only a GRUB screen is displayed, and when I click Try or Install Ubuntu, nothing happens. The screen goes black and the notebook appears to be on but no video.
I don't know what else to do, I need Ubuntu on this notebook.
What am I doing wrong?

This is the screenshot showing details of the notebook's factory system (attached).

---

### Post by MAFoElffen on 2023-07-29
You are on a journey where the path is not cleared yet...

Your first problem(in your description)  is that you are trying to boot an arm64 system off of an amd64 image. That is not going to work. (ever)

Next, the arm64 installer is not yet certified for the Qualcom Snapgragon 7c. There are some Debian experimental images:  [https://github.com/hexdump0815/imagebuilder/blob/main/systems/snapdragon_7c_woa/readme.md](https://github.com/hexdump0815/imagebuilder/blob/main/systems/snapdragon_7c_woa/readme.md)

If you read the 'special notes' section down the page, that work-in-progress description is in the very early stages still.

Linux Kernel 6.3 arm64 (newly) supports the Snapdragon 8 gen 2 processor... But just because you have a working kernel... you still need a boot-loader to load it. Things are still early for that processor.

---

### Post by TheFu on 2023-07-29
Just to shorten MAFoElffen's answer.  If you aren't prepared to learn about CPU and boot internals, I doubt you'll get this working this year and perhaps not in 2024.  Massive efforts can replace current skills, but only so much. You could prove me wrong.

If you want a practical answer, move on to a different hardware platform and save yourself months of effort and frustration.

BTW, I was a cross-platform C/C++ developer for a decade.  I wouldn't touch this system.  Well, actually, I wouldn't touch any Compaq/HP small computer, but that's a different bias based on bad corporate experiences.  Compaq used to engineer their own motherboards and BIOS. It was the "clone" industry standard for a long time, but soon it became a 1-off and had compatibility issues.  In 1999-2005, I ran into this directly that has me avoiding any small computers (Intel and smaller) from HP.  

They make find UNIX servers, however, even if their C++ standards interpretation is overly strict. That isn't what we are talking about here.

---

