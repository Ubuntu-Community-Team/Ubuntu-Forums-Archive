---
title: "[SOLVED] how to switch from nvidia to nv?"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by astrophoenix on 2008-11-01
I ran dist-upgrade from hardy to intrepid. I have an nvidia card in this machine. now X won't run, telling me:

(EE) No drivers available.

Fatal server error:
no screens found


so I tried changing the line in my xorg.conf file which read

```

Driver          "nvidia"

```

to 

```

Driver          "nv"

```

but I still get the same message.

how do I switch to the free driver??

---

### Post by bford16 on 2008-11-01
> **astrophoenix said:**
> I ran dist-upgrade from hardy to intrepid. I have an nvidia card in this machine. now X won't run, telling me:

(EE) No drivers available.

Fatal server error:
no screens found


so I tried changing the line in my xorg.conf file which read

```

Driver          "nvidia"

```

to 

```

Driver          "nv"

```

but I still get the same message.

how do I switch to the free driver??

I had a similar problem when I upgraded today. It seems I already had installed the nvidia-glx-173 drivers, and Intrepid recommends the nvidia-glx-177 drivers.  After several attempts, I realized that the problem was CAUSED by having the 173 driver installed.  So I fired up Synaptic (Settings, Administration, Synaptic), and completely removed everything to do with the 173 driver.  I also removed all the "modaliases" packages, although I am not sure it mattered.  While I was searching for things to remove, I noticed that I have "linux-restricted-modules-2.6.24-21."  Since Intrepid uses the 2.6.27-7 kernel, I decided to remove the 2.6.24 modules, too.

Once I had removed all that stuff, I restarted the computer, and installed the 177 driver via synaptic.  I also reinstalled all the modaliases. Now I have the 'nvidia' driver back, and all is well.

I hope this helps.

If you still want to install the 'nv' driver, you can get it by installing the 'xserver-xorg-video-all' package. But you should not need it.

---

### Post by astrophoenix on 2008-11-01
thanks.

turns out my machine is still running the 2.6.24 kernel.

so I installed linux-generic-2.6.27-7

when I reboot into that, though, it seems to be unable to mount my encrypted lvm2 partition (Which is my /).

so I think now I need to solve the problem of why lvm2 is not working, then I can use the 2.6.27 kernel, and I bet my X will work again.

---

### Post by astrophoenix on 2008-11-04
[solution in this post, just click]("http://ubuntuforums.org/showthread.php?p=6103307#post6103307")

---

