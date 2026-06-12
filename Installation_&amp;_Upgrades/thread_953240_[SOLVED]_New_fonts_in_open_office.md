---
title: "[SOLVED] New fonts in open office"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by beidache on 2008-10-19
Hey guys Im new in Ubuntu and I just started to learn about it my problem is that I want to use fonts in open office like arial, times new roman, etc, and I dont have any idea how to install it, can someone help me? and please step by step cuz I dont understand well the ubuntu. thanks. 
By thew way my open office is 2.4

---

### Post by Rhubarb on 2008-10-20
Those fonts can be easily installed by installing the msttcorefonts package.
Open up a terminal (Applications --> Accessories --> Terminal), and type this in:
```
sudo aptitude install msttcorefonts
```
You'll be prompted for your password, enter this in, then answer yes to any prompts that may come up.
It is also possible to install msttcorefonts from the Synaptic Package Manager (System --> Administration --> Synaptic Package Manager).

If you have .ttf files you wish to install, you can create a folder called **.fonts** and put the .ttf font files in that folder.  Then your user is able to use those fonts.

---

### Post by beidache on 2008-10-20
Thaks very useful

---

