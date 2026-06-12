---
title: "ubuntu 9.04 -&gt; 9.10 failure"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by raev on 2009-10-19
Hi!
I just updated from 9.04 -> 9.10.
Now when i start ubuntu i don't end up at the "regular" log in screen but instead i end up with a terminal saying:

--------------------------------------------------------
usplash: Setting mode 1280x1024 failed
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768

Ubuntu karmic (development branch) *comp name* tty1

*comp name* login: _

--------------------------------------------------------

The screen is flashing frequently and the keyboard register keystrokes only at some intervals with the flashing screen.

This is when i use the standard kernel 2.6.31-14-generic

When i use kernel 2.6.28-15-generic the system boots up and i can log in.
Everything but the touch pad seems to be working "normally" what i can see.

PS: The computer is a dell xps m1330 and i have used ubuntu sice 7.04
And the nvidia 180 driver never worked for me in the 9.04 but the 173 did, allthough it works my friend who has an identical laptop but did install the 9.04 from scratch.

---

### Post by XsCode on 2009-10-21
I have exactly the same problem after downloading and installing using the 9.10 beta install currently available on the main Ubuntu page.  All I did was run the update Manager after rebooting after install.

---

### Post by NoDeity on 2009-10-21
I have the same issue and will watch this thread for a solution.

---

### Post by NoDeity on 2009-10-21
I should add that my issue is not exactly like that in the opening post.  I encounter the same problem with trying to use the 2.6.28-15-generic (which it wants to do automatically) but it works fine when I use the 2.6.31-14-generic kernel (exactly the opposite of raev).

---

### Post by nanog on 2009-10-22
From the description I think you are getting kicked back into tty because of a graphic driver issue. Xorg is failing and vesa/nv is not starting correctly. 

If its nvidia, you may have a problem with your driver. Dkms fails when you use non-standard nvidia packages (or have inadvertantly removed a kernel source dependency). 



This will tell you whether the nvidia dkms module is installed:
```
dkms status

```

Optional: 

```
sudo dkms remove -m nvidia -v nvidiamodule --all

```


Try reinstalling nvidia-glx-185 and rebooting.

Or you can issue:
```
dkms build nvidiakernelsourcepath
```

(Karmic has been running bug free for me on my m1330.)

---

### Post by XsCode on 2009-10-22
I reinstalled as I couldn't even log in due to the key presses not always being registered.  After reinstall I cancelled the partial-upgrade and just did the updates it would allow, but now I have a load of updates grayed out that won't install.

```
dkms status
```

```
The program 'dkms' is currently not installed.  You can install it by typing:
sudo apt-get install dkms
dkms: command not found

```

Also even though i can now boot to desktop, i still get the fstab errors mentioned in other posts.

Regards

---

### Post by Vanishing on 2009-10-22
from what you posted, i figured you are a intel graphic user.
did you follow some guide to enhance your grphic performance during jaunty? i think that is the problem.

yesterday i tried the new xserver-xorg-video-intel driver with uxa mode, same symptom. so i went back to older driver and enabled exa, everything's fine now, even compiz.
ps: im a intel mobile 945 user...

---

### Post by XsCode on 2009-10-22
I don't know if you were referring to me Vanishing, but no, i'm running an 8400m GT, but i've managed to solve the problem.

I didn't delete the old kernel (2.6.31-11-generic) when it asked so i tried booting into it and Voila! it worked, so following the nvidia theme put forward by nanog, I changed the graphics driver in xorg.conf to vesa and rebooted into 2.6.31-14-generic and it loaded gnome, so i then re-ran the driver installation again to build a module for this kernel (i always get the latest beta from nvidia's site) and all is working fine again :))

Thanks everyone for their help!

P.S. i couldn't get dkms to work at all... even a status?!

---

### Post by Vanishing on 2009-10-22
> **XsCode said:**
> I don't know if you were referring to me Vanishing, but no, i'm running an 8400m GT, but i've managed to solve the problem.

I didn't delete the old kernel (2.6.31-11-generic) when it asked so i tried booting into it and Voila! it worked, so following the nvidia theme put forward by nanog, I changed the graphics driver in xorg.conf to vesa and rebooted into 2.6.31-14-generic and it loaded gnome, so i then re-ran the driver installation again to build a module for this kernel (i always get the latest beta from nvidia's site) and all is working fine again :))

Thanks everyone for their help!

P.S. i couldn't get dkms to work at all... even a status?!

oh..no, im refering to the original thread poster..hehe

---

### Post by VMC on 2009-10-22
> **raev said:**
> Hi!
... The computer is a dell xps m1330 and i have used ubuntu sice 7.04
And the **nvidia** 180 driver never worked for me in the 9.04 but the 173 did, allthough it works my friend who has an identical laptop but did install the 9.04 from scratch.

> **Vanishing said:**
> from what you posted, i figured you are a intel graphic user.

Where did you come up with that conclusion?

---

### Post by Vanishing on 2009-10-22
> **VMC said:**
> Where did you come up with that conclusion?

cuz last time i tried to update my intel graphic driver, same problem arise..

---

### Post by XsCode on 2009-10-22
I've been asked to expand on my solution to this problem so......

Boot into the live disk and open a console.

Make a mount dir using 
```
sudi mkdir /mnt/hd
```

mount the chroot with 
```

mount --bind /dev /mnt/hd/dev
mount --bind /proc /mnt/hd/proc
mount --bind /sys /mnt/dh/sys
cp /etc/resolv.conf /mnt/hd/etc/resolv.conf
chroot /mnt/hd /bin/bash

```

So you should now be in your proper installation, so you can edit your xorg.conf with

```

sudo nano -w /etc/X11/xorg.conf

```

change the device line to vesa... so mine went from..

```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

```

to 

```

Section "Device"
    Identifier     "Device0"
    Driver         "vesa"
    VendorName     "NVIDIA Corporation"
EndSection

```

use ctrl+x then y to save and then reboot..... you **should** be able to boot to your desktop now.

i think? ;)

---

### Post by nanog on 2009-10-22
You need to install dkms and reinstall nvidia. I believe most m1330 come with nivdia.

---

