---
title: "dual boot"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by el3ktr1k on 2011-03-30
On my laptop I have windows vista installed and decided to give Ubuntu 10.10 a try so I created a live CD. I installed Ubuntu alongside existing OS. When I rebooted I had an option of different operating systems to choose from. I believe it was the vista boot menu but I could be wrong. Ubuntu was highlighted by default. How can I change this so vista boots by default. Can you give instructions for both the vista and unbuntu boot menu since I'm not sure which one it was? Thank you

---

### Post by oldfred on 2011-03-30
Welcome to the forums.

This assumes you do not have wubi:

If you have Vista and a Vista recovery, are the titles reversed? That often happens with grub's os-prober and Vista. Do not start to run recovery by mistake.

I have not used these but they are recommended gui tools.

This will also let you change the titles:
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

Startup manager (SUM) in synaptic will allow you to set boot default and the timeout even with grub2.
the quick and easy to make a default boot:

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

---

