---
title: "MXM:GUID detected in BIOS"
date: 2023-10-02
forum: Installation &amp; Upgrades
---

### Post by grafeno30 on 2023-10-02
Hello geeks,

I have installed Ubuntu Studio (with Kali the same thing happens to me with Ubuntu desktop I did not have any problems booting in safe graphics mode), the following message appears:

MXM: GUID detected in BIOS

My machine has the following hardware and software:

[IMG]https://drive.google.com/file/d/1Qk2tSPbPRQGAnDQNJl6bfx9lENxymG7a/view?usp=sharing[/IMG]
[https://lh3.googleusercontent.com/drive-viewer/AK7aPaDFApRwNTIpSxXspvmEvDIktype6wyUSnd6QTpb7PRwDLv8_XmU6CPShxDcgq3m9sdrUJnpMsvw8PZ_2GWOej8PzfrqwA=s1600](https://lh3.googleusercontent.com/drive-viewer/AK7aPaDFApRwNTIpSxXspvmEvDIktype6wyUSnd6QTpb7PRwDLv8_XmU6CPShxDcgq3m9sdrUJnpMsvw8PZ_2GWOej8PzfrqwA=s1600)
[IMG]https://drive.google.com/file/d/1Qk2tSPbPRQGAnDQNJl6bfx9lENxymG7a/view?usp=sharing[/IMG]
                                                                   
I think the problem is my graphics card (NVIDIA GeForce RTX 3060). I can't interact with anything, then the aforementioned message appears and the boot stops

Thanks in advance for your help

---

### Post by #&amp;thj^% on 2023-10-02
I seen this a few months back, I'm not effected but have a look: [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=1041743](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=1041743)

[https://gitlab.freedesktop.org/drm/nouveau/-/issues/246](https://gitlab.freedesktop.org/drm/nouveau/-/issues/246)

This is not a real warning, it's an informational message from the
nouveau driver that is being logged without a priority specified

Have you installed the nVidia driver?
EDIT: You also have a newish CPU i9-11900k that might need a kernel setting.

---

