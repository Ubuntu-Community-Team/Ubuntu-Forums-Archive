---
title: "New install with broken x"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by wushuFreak on 2008-02-16
I am not sure where this problem lies. 

I have a fresh install of 7.10. 

My basic hardware specs are:
Biostar nForce 4 SLI system board
2x nVidia 7900 GT in SLI


When I boot into or startx, my screen goes black (there is still output, but it is black). when I ctrl alt F1, I get:

```

Starting up ...
[   33.664468] PCI: Cannot allocate resource region 3 of device 0000:05:00.0
[   33.664504] PCI: Cannot allocate resource region 3 of device 0000:04:00.0
[   33.747155] PCI: Error while updating region 0000:01:0a.0/0 (fe900000 != 00900000)
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/6f68346e-2a75-4daa-8194-cb116c507f8f) = sda2(8,2)
kinit: trying to resume from /dev/disk/by-uuid/6f68346e-2a75-4daa-8194-cb116c507f8f
kinit: No resume image, doing normal boot...

```

I also looked at xorg.conf and one of my GPUs was not listed, so I added it. This had no effect.

I did try searching a bit on the forum and google, but I really don't even know where to start. I would be grateful if someone could point me in a direction.

Thank you

---

### Post by PmDematagoda on 2008-02-16
Did you install the Nvidia driver?

---

### Post by wushuFreak on 2008-02-16
oops. 

I missed the obvious.

I will search for instructions on this.
Thank you

---

### Post by PmDematagoda on 2008-02-16
You can install the drivers using:-
```
sudo apt-get install nvidia-glx-new
```
enable them using:-
```
sudo nvidia-settings --config enable
```

That should fix your problem, but they may not work with SLI, in any case you can try it.

---

### Post by pbcartwright on 2008-02-16
I also have an nvidia card, and my xorg.conf video adapter section looks like this:
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

if you need to boot without using the nvidia driver configured, I always change :
Driver "nvidia"
to
Driver "nv"
then I can get back into X, though it is slower ...
you might also look into installing envy, it automatically configures nvidia drivers for Ubuntu:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by wushuFreak on 2008-02-16
That did the trick!

Thanks again.

I am still getting the error messages I listed in the first post. Everything appears to be working, though. Any ideas what these messages mean?

---

### Post by PmDematagoda on 2008-02-16
> **wushuFreak said:**
> That did the trick!

Thanks again.

I am still getting the error messages I listed in the first post. Everything appears to be working, though. Any ideas what these messages mean?

That seems to be a message that is normal in most(maybe all) Ubuntu installs. Does the startup splash screen work without any errors?

---

### Post by wushuFreak on 2008-02-16
Everything seems to be working great!

I am definitely of from the "if it ain't broke..." school. I just wanted to be certain these messages did not indicate a serious issue that might crop up later.

---

