---
title: "Official Nvidia driver release with OpenGL 3.3/4.0"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kahumba on 2010-04-13
It's official folks:

[http://developer.nvidia.com/object/opengl_driver.html](http://developer.nvidia.com/object/opengl_driver.html)
[http://www.phoronix.com/scan.php?page=news_item&px=ODE0OA](http://www.phoronix.com/scan.php?page=news_item&px=ODE0OA)

Do you think the Canonical folks will include this latest version into the Lucid repos?

---

### Post by Seren on 2010-04-13
> **kahumba said:**
> It's official folks:

[http://developer.nvidia.com/object/opengl_driver.html](http://developer.nvidia.com/object/opengl_driver.html)
[http://www.phoronix.com/scan.php?page=news_item&px=ODE0OA](http://www.phoronix.com/scan.php?page=news_item&px=ODE0OA)

Do you think the Canonical folks will include this latest version into the Lucid repos?

It is past "feature freeze" so it is not likely.

However, it might be added to the "backport" repository or in a PPA in a while. (If there is no dependencies issue with X or kernel version).

---

### Post by philinux on 2010-04-13
The final freeze is on the 15th.
[https://wiki.ubuntu.com/FinalFreeze](https://wiki.ubuntu.com/FinalFreeze)

---

### Post by forcecore on 2010-04-13
i thought that driver upgrade is requirement always and do not belong to feature freeze, what if someone buys newer card like 4 months after Lucid and only new driver supports it????? I myself do not worry because i use only .run installers from provider but what about other people who use that Jockey clown thing for drivers.

---

### Post by kahumba on 2010-04-13
> **forcecore said:**
> ... i use only .run installers from provider but what about other people who use that Jockey clown thing for drivers.
afaik in Lucid you can't install the drivers from Nvidia's site anymore (because Canonical changed something starting with Lucid) so this is one more reason to upgrade the repo drivers now before Lucid goes gold and the Nvidia users start flooding the sub forums about why they can't take full advantage of their Fermi GPUs or complains from normal developers who wanna start developing for OpenGL 3.3/4.0 both of which are important in the 3D world and will become exponentially more important in the next years as Lucid is set to be supported for 3 years.

---

### Post by sdowney717 on 2010-04-13
I use the .run nvidia installer downloaded from the site.
It works. During the install, you get a symbolic error. It installs and everything works.
You install it when x is off, such as boot to recovery mode.

---

### Post by IanW on 2010-04-13
I think the freeze only applies to the main/universe/multiverse repos, so I expect the driver will show up in a PPA soon enough.
Probably [Nvidia-VDPAU]("https://launchpad.net/~nvidia-vdpau/+archive/ppa").

---

### Post by forcecore on 2010-04-13
i am sure Nvidia fixes that because most used distro in world comes to LTS status.

---

### Post by kahumba on 2010-04-13
> **forcecore said:**
> i am sure Nvidia fixes that because most used distro in world comes to LTS status.
If you're referring to not installing properly, then as [sdowney717]("http://ubuntuforums.org/member.php?u=209280") mentioned, it probably was just a temporary issue and now the installer only yields a warning, though I myself haven't tested it and don't know how Nvidia's driver installs/behaves on other Lucid setups.

---

### Post by sdowney717 on 2010-04-14
Just adding, you do have to blacklist nouveau in blacklist.conf to get the nvidia driver to work.

---

### Post by realzippy on 2010-04-14
> **sdowney717 said:**
> Just adding, you do have to blacklist nouveau in blacklist.conf to get the nvidia driver to work.

...hm,I have not blacklisted noueveau,nvidia just works...

---

### Post by sdowney717 on 2010-04-14
[http://ubuntuforums.org/showthread.php?t=1430888&page=4](http://ubuntuforums.org/showthread.php?t=1430888&page=4)
when I first tried installing nvidia 3 weeks ago, I could not until I blacklisted nouveau. Dont know if this has changed. I run the nvidia installer file directly from nvidia.
according to 3rdalbum you do this.

> 
Quote:
Originally Posted by sdowney717 View Post
So i switch to console
stop x
rmmod the nv driver
install nvidia driver

what to do if the driver fails and I need the nv driver back?
modprobe nv driver?
I will keep looking into this.

[QUOTE]No, the issue is the nouveau driver, not the nv driver. I don't think rmmod'ing the nouveau driver will actually work, because you'll get an error message that "nouveau module is busy".

You need to open the /etc/modprobe.d/blacklist.conf file, and add:

Code:

blacklist nouveau

to the bottom. Then reboot and you can install the nvidia driver.

If the Nvidia driver fails, you need to blacklist 'nvidia', unblacklist 'nouveau', and modify xorg.conf to use 'nouveau' as the driver.
__________________[/QUOTE]

---

### Post by IanW on 2010-04-14
I just installed "nvidia-current". This blacklisted nouveau for me.

---

