---
title: "Ubuntu update overrides Windows bootloader"
date: 2015-08-14
forum: Installation &amp; Upgrades
---

### Post by soxterix on 2015-08-14
Some time ago I tried to install Windows 7 and Ubuntu alongside on HP Probook 450 and I had difficulties I've never had before. I installed Windows 7 and then Ubuntu 14.04 and when I chose Windows 7 from GRUB list I got black screen with white strips. I know Windows was loaded because you could hear proper sound and you could type your password and press enter and you were logged in. But the screen was still black with those strips. When you chose Ubuntu everything worked fine. I still don't know what caused this problem.
I couldn't figure what to do so I installed Ubuntu and then Windows 7 and started to use Windows bootloader. Everything worked fine till now. Now when you choose Windows from the list you got Windows login screen.
But recently I updated Ubuntu and it removed my Windows bootloader and again when I choose Windows I get black screen with strips. I wonder if you have and suggestions what I can do about it? I mean I can use Windows repair disc and reset Windows bootloader but it's going to be onerous to do this everytime I have to update Ubuntu.

---

### Post by oldfred on 2015-08-16
What video is your system using?
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

