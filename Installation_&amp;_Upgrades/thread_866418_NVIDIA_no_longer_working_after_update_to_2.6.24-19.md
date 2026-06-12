---
title: "NVIDIA no longer working after update to 2.6.24-19"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by witchicon on 2008-07-21
I'm running ubuntu studio 8.04. A few days ago, the update to 2.6.24-19 kernel came down. After that, I can't seem to make the nvidia drivers work anymore. The computer just boots into low graphics mode. nv will work, but doesn't perform very well....
I've tried envyng, same result.
I've tried installing NVIDIA drivers with "sh NVIDIA-Linux-x86-173.14.09-pkg1.run". and "nvidia-xconfig", but still same result.
I've tried "aptitude install nvidia-glx-new.", still the same result.
The odd thing, is that I've tried booting into each of the earlier kernels, and doing these fixes, but that doesn't work either, even though nvidia was working fine before the update. I've tried both 2.6.24-19-rt and 2.6.24-19-generic. I'm totally out of ideas. Any advice? 
Thanks!

---

### Post by overdrank on 2008-07-21
> **witchicon said:**
> I'm running ubuntu studio 8.04. A few days ago, the update to 2.6.24-19 kernel came down. After that, I can't seem to make the nvidia drivers work anymore. The computer just boots into low resolution mode. nv will work, but doesn't perform very well....
I've tried envyng, same result.
I've tried installing NVIDIA drivers with "sh NVIDIA-Linux-x86-173.14.09-pkg1.run". and "nvidia-xconfig", but still same result.
I've tried "aptitude install nvidia-glx-new.", still the same result.
The odd thing, is that I've tried booting into each of the earlier kernels, and doing these fixes, but that doesn't work either, even though nvidia was working fine before the update. I've tried both 2.6.24-19-rt and 2.6.24-19-generic. I'm totally out of ideas. Any advice? 
Thanks!

Hi and welcome, You may try what PmDematagoda suggested here
[http://ubuntuforums.org/showthread.php?t=864202](http://ubuntuforums.org/showthread.php?t=864202)

---

### Post by witchicon on 2008-07-22
It's working now!
I did disable the nv and nvidia_new, as per the instructions you sent:

[http://ubuntuforums.org/showthread.php?t=864202](http://ubuntuforums.org/showthread.php?t=864202)

But it still wasn't working. 
Finally I decided to try to undo everything I had done, and start over. 
I'll describe the steps I took in case it's helpful to someone else:

I uninstalled the aptitude installation of nvidia-glx:
```

sudo aptitude purge nvidia-glx && sudo aptitude clean nvidia-glx
```
and 
```

sudo aptitude purge nvidia-glx-new && sudo aptitude clean nvidia-glx-new

```
just to make sure that still wasn't in there.
and I got rid of anything from envyng:
```

envyng --uninstall-all

```
then I shutdown X:
```

sudo /etc/init.d/gdm stop

```
and ran the nvidia installer:
```
sudo sh NVIDIA-Linux-x86-173.14.09-pkg1.run

```

And everything works great now!
Thanks!

---

### Post by fcr on 2008-07-25
> **witchicon said:**
> It's working now!
I did disable the nv and nvidia_new, as per the instructions you sent:

[http://ubuntuforums.org/showthread.php?t=864202](http://ubuntuforums.org/showthread.php?t=864202)

But it still wasn't working. 
Finally I decided to try to undo everything I had done, and start over. 
I'll describe the steps I took in case it's helpful to someone else:

I uninstalled the aptitude installation of nvidia-glx:
```

sudo aptitude purge nvidia-glx && sudo aptitude clean nvidia-glx
```
and 
```

sudo aptitude purge nvidia-glx-new && sudo aptitude clean nvidia-glx-new

```
just to make sure that still wasn't in there.
and I got rid of anything from envyng:
```

envyng --uninstall-all

```
then I shutdown X:
```

sudo /etc/init.d/gdm stop

```
and ran the nvidia installer:
```
sudo sh NVIDIA-Linux-x86-173.14.09-pkg1.run

```

And everything works great now!
Thanks!

I have exactly the same problem. I tried all of the above. I even switched to nv and removed all of the binary modules and libraries and tried both EnvyNG again and the nVidia installer from their web - uninstalling before the next attempt. No joy.

I tried going back to the 2.6.24-18 kernel and modules. I tried going back to earlier nVidia drivers both with the 24-18 and the 24-19 kernels. Still no luck.:(

So I am stuck with the nv drivers until someone come up with a fix. At least the nv drivers work.

- Fred

---

### Post by stchman on 2008-07-25
> **witchicon said:**
> I'm running ubuntu studio 8.04. A few days ago, the update to 2.6.24-19 kernel came down. After that, I can't seem to make the nvidia drivers work anymore. The computer just boots into low graphics mode. nv will work, but doesn't perform very well....
I've tried envyng, same result.
I've tried installing NVIDIA drivers with "sh NVIDIA-Linux-x86-173.14.09-pkg1.run". and "nvidia-xconfig", but still same result.
I've tried "aptitude install nvidia-glx-new.", still the same result.
The odd thing, is that I've tried booting into each of the earlier kernels, and doing these fixes, but that doesn't work either, even though nvidia was working fine before the update. I've tried both 2.6.24-19-rt and 2.6.24-19-generic. I'm totally out of ideas. Any advice? 
Thanks!

What type of Nvidia card do you have?  If it is a 9xxx series then the restricted drivers will not work as they are 169.12 drivers.

---

### Post by sdennie on 2008-07-25
> **witchicon said:**
> It's working now!
I did disable the nv and nvidia_new, as per the instructions you sent:

[http://ubuntuforums.org/showthread.php?t=864202](http://ubuntuforums.org/showthread.php?t=864202)

But it still wasn't working. 
Finally I decided to try to undo everything I had done, and start over. 
I'll describe the steps I took in case it's helpful to someone else:

I uninstalled the aptitude installation of nvidia-glx:
```

sudo aptitude purge nvidia-glx && sudo aptitude clean nvidia-glx
```
and 
```

sudo aptitude purge nvidia-glx-new && sudo aptitude clean nvidia-glx-new

```
just to make sure that still wasn't in there.
and I got rid of anything from envyng:
```

envyng --uninstall-all

```
then I shutdown X:
```

sudo /etc/init.d/gdm stop

```
and ran the nvidia installer:
```
sudo sh NVIDIA-Linux-x86-173.14.09-pkg1.run

```

And everything works great now!
Thanks!

Now that you are using the manually installed driver, you will have to re-install them every time there is a kernel update.  However, you can prevent that and have them auto-installed for new kernels using this guide: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

---

### Post by fcr on 2008-07-28
> **stchman said:**
> What type of Nvidia card do you have?  If it is a 9xxx series then the restricted drivers will not work as they are 169.12 drivers.
I have a 7600GS. It worked with the restricted drivers until the last update to the 2.6.24-19 kernel.

---

### Post by gwoods on 2008-07-29
The upgrade broke my system as well. I fixed it by logging in via low res mode and then reinstalling both the nvidia-glx-new and nvidia-kernel-common packages via the synaptic package manager.

---

### Post by fcr on 2008-07-29
> **gwoods said:**
> The upgrade broke my system as well. I fixed it by logging in via low res mode and then reinstalling both the nvidia-glx-new and nvidia-kernel-common packages via the synaptic package manager.

I tried that as well. I tried Envy, uninstalled it. Tried the driver from nVidia, uninstalled it. I cleaned up everything before each trial. Even removed the restricted modules. No luck. :(

The driver was listed in the hardware drivers and was enabled but did not succeed in starting. There was no message remotely connected with this in any of the error logs. I could see the kernel try to start the driver three times before it gave up and prompted to start in low res.

I am just using nv for now to watch videos but I miss the hardware acceleration. But I did get PulseAudio to play via alsa to IEC958 so I achieved something.:)

- Fred

---

### Post by gwoods on 2008-07-30
You're right my first try didn't do it. So then also reinstalled the linux-restricted-modules-2.6.24-19-generic and that worked. When it is working correctly I see an NVidia splash screen when X starts up.

---

### Post by fcr on 2008-08-01
> **gwoods said:**
> You're right my first try didn't do it. So then also reinstalled the linux-restricted-modules-2.6.24-19-generic and that worked. When it is working correctly I see an NVidia splash screen when X starts up.

I tried what you suggested. I even tried nvidia-glx instead of nvidia-glx-new in case the driver was relating to the gforce4 on the motherboard instead of the 7600GS in the AGP slot.

SOLVED: The 7600GS card's auxiliary power circuits had stopped working so the card always dropped into non-accelerated mode. Apparently it must have stopped working on the same day that the kernel was updated. Maybe the reboot caused it. :-(

The Linux drivers do not notify this. I had to boot into Windows to discover this. Hope that the card is still under guarantee. One less thing that is driving me crazy. :-)

---

