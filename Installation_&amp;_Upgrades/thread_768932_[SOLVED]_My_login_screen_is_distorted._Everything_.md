---
title: "[SOLVED] My login screen is distorted. Everything in pushed down."
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Rytron on 2008-04-26
Hi,
Since I upgraded to Ubuntu 8.04, my login screen seems to be pushed down. Perhaps the resolution is wrong? With some login screens I cant even see the place where I have to input my username and password as these are not visable on the screen, they are pushed down.

My desktop resolution is perfect though.

Any solution?

Thanks.

---

### Post by UncleBark on 2008-04-27
If you have an nVidia card check the bottom of page one in this thread.  I had the same problem and this solved it for me.

[http://ubuntuforums.org/showthread.php?t=763107](http://ubuntuforums.org/showthread.php?t=763107)

Good luck!

---

### Post by Rytron on 2008-04-27
Hi UncleBark,
I used some of the code on that thread you linked to. No luck.

Could you post here the exact code / procedure to use?

Thanks.

---

### Post by graphix1 on 2008-04-27
I tried to up grade to 8.10 using the update feature in 7.10 and I got the same results. My desktop was about 10% of the original. I tried the panning key combinations and it did not work. I had to reinstall 7.10. Here is what I think happed. I too run a Nvidia card and when I first installed ubuntu I had the same problem. But I could pan to get to the various windows to complete the installation.I then went to Nvidia site and got the Linux driver and installed it. I could then leave the default of 800 X 640 and I went to 1024 x 768.It was at this resolution and with the Linux driver as my default I attempted the update.I believe this could be My problem.If the update did not pick up my Linux version of my Nvidia driver and restarted with the default driver at 800 x 640 would this have caused my problem. I could not get to the windows to complete the restart so the pan key commands did not work. I need to get this resoled as I have sent for the CD.I also am a rank beginner in Ubuntu.

---

### Post by mguevrem on 2008-04-27
Uhm I have the same problem.  

I was using Envy as an NVDIA card/driver manager.  Before upgrading I had Envy restore the default video driver for Ubuntu.  After the booting up in 8.04 I downloaded the latest version of EnvyNG to reinstall my NVIDIA driver. 

The login screen is still at the wrong resolution, I can barely see the login window and have no access to the shut down button.  

Anyone has a good idea how to fix this?  Should it be reported as a bug?

Cheers,

Mguevrem

---

### Post by UncleBark on 2008-04-27
The code I used was supplied by Fire_chief and it worked.

```
sudo dpkg-reconfigure xserver-xorg
sudo nvidia-xconfig 
```

There is a bug report on this issue here: .[#214704]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/214704")

I hope this helps.

---

### Post by Rytron on 2008-04-27
> **mguevrem said:**
> Uhm I have the same problem.  

I was using Envy as an NVDIA card/driver manager.  Before upgrading I had Envy restore the default video driver for Ubuntu.  After the booting up in 8.04 I downloaded the latest version of EnvyNG to reinstall my NVIDIA driver. 

The login screen is still at the wrong resolution, I can barely see the login window and have no access to the shut down button.  

Anyone has a good idea how to fix this?  Should it be reported as a bug?

Cheers,

Mguevrem


Press the F10 key to access shut down, restart, etc list.

---

