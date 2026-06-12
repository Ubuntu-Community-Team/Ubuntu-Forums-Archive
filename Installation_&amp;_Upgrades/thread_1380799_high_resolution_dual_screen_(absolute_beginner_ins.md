---
title: "high resolution dual screen (absolute beginner inside)"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by coyotte26 on 2010-01-14
Hi everyone, 

I just registered because a few weeks back I decided, after many years of temptation to give a serious try to ubuntu. Needless to say, I am a complete beginner and has never typed a single line of script and hardly ever used a shell :P. So please be kind with me, I will learn but it will take time.

I have an HP NC6400 (dual core 2.0GHz, 4GB RAM, 320 GB HDD, ATI X1300 14" 1440*900) and a dell 2407 external screen with a resolution of 1920*1200 :KS. 
I have first tried ubuntu 9.10 but it just clearly gave me the finger with a complete freeze as soon as I would plug in the external screen. An experienced linux friend of mine who helped me with the installation had never seen a linux freeze before !! So I have downgraded to 9.04 with significant success because the external screen works but at a maximum resolution of 1280*800.

I would greatly appreciate anyone with any idea on how to get the full capacity of my screen to help me, step by step if possible.

Thanks, 

Sebastien.

PS : please forgive me if the post is not in the proper section and feel free to move it where ever appropriate.

---

### Post by dstew on 2010-01-14
First and easiest thing, check in System --> Administration --> Software Sources and make sure the "Proprietary drivers for devices (restricted)" repository is enabled (the box should be checked). If not, enable it (check the box), close the window, then click the Reload button on the next dialog box. If the restricted repository is enabled, check System --> Administration --> Hardware Drivers to see if there is a third-party driver available for installation. If so, install it.

Otherwise, to let us see what your setup is, open a terminal window (Applications --> Accessories --> Terminal) and enter on the command line```
sudo lshw -C display
```Post the output of this command to the forum.

---

