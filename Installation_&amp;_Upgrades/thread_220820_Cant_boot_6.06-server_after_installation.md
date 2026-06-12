---
title: "Cant boot 6.06-server after installation"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by zpon on 2006-07-22
I have just installed the server version, on a old 350MHz box (2,1 GB HD), but when it starts to boot, it suddenly stops, and reboot instead. I have tried both LAMP and regular installation.

I'm new to ubuntu, so i hope some one can help me

---

### Post by SkyNet2029 on 2006-07-22
Have you tried choosing a different kernel during the installation? Why I ask this:
The only time I have ever had Ubuntu stop booting halfway and do a quick reboot was when I had chosen to put a 686 kernel image with a 350MhzAmd K2.
I was and am still, stuck using the 386 (2.6.
15-23-386) which seems to work nicely.

---

### Post by zpon on 2006-07-22
> **SkyNet2029 said:**
> Have you tried choosing a different kernel during the installation?
No, how do i chose another kernel during the installation?

---

### Post by SkyNet2029 on 2006-07-22
Once you go through the 'Complete Installation' process, at or near the tail-end of it, you should be prompted to choose which kernel to use, provided your deb-conf priorities are set to 'low'. 
*You can select 'Change deb-conf priority' during the installation, at least whenever you run it as 'expert-server'.

Kind of a pain because it will prompt you to answer everything, usually the default is acceptable depending on what you are going to doing with your server, hardware usage, etc., but with maximum control you get that prompt. At least its a server install, and not the full boat though, if you choose to reinstall. The other way is to just boot into your old kernel if its still there, and see what used to work, kernel-wise, on your machine, and use that as a baseline for upgrading the kernel to something workable.
I had to manually specify the 
'linux-kernel-2.6.15-23-386' to get things running here.

---

### Post by zpon on 2006-07-22
> **SkyNet2029 said:**
> Once you go through the 'Complete Installation' process, at or near the tail-end of it, you should be prompted to choose which kernel to use, provided your deb-conf priorities are set to 'low'. 
*You can select 'Change deb-conf priority' during the installation, at least whenever you run it as 'expert-server'.

Kind of a pain because it will prompt you to answer everything, usually the default is acceptable depending on what you are going to doing with your server, hardware usage, etc., but with maximum control you get that prompt. At least its a server install, and not the full boat though, if you choose to reinstall. The other way is to just boot into your old kernel if its still there, and see what used to work, kernel-wise, on your machine, and use that as a baseline for upgrading the kernel to something workable.
I had to manually specify the 
'linux-kernel-2.6.15-23-386' to get things running here.
Okay, do you chose expert-mode by pushing "F6" twice? I'll give it a try

---

