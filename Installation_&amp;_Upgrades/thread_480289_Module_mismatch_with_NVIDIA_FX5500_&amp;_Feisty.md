---
title: "Module mismatch with NVIDIA FX5500 &amp; Feisty"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by charles.figura on 2007-06-21
Okay, so I upgraded my desktop machine (with an NVIDIA GeForce FX5500 video card) from edgy to feisty.  RIght away, a problem shows up - instead of starting up X/KDE on bootup, I get the following message on console:

kinit: name_to_dev_t(/dev/disk/by-uuid/59321e46-5854-4666-84fc-055c7a684235) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/59321e46-5854-4666-84fc-055c7a684235
kinit: No resume image, doing normal boot...

and I get a login prompt - no X, but no X errors/warnings, either.  So I login, type 'startx', and I get an X error that tells me that my NVIDIA driver module is not the same version as my kernel module.  I know that you've got to have the linux-restricted-modules that matches your kernel (2.6.20-16, in my case).  I've tried each of the nvidia-glx packages ('plain', -legacy, -new) with different combinations of driver versions downloaded from NVIDIA.  The bizarre thing is that I've managed to match versions up, do a manual 'startx', and it works!  Until I reboot, and get the same result - the kinit problem, and the module mismatch when I try to start X manually.

I'm about at my wit's end here.  I know that the different nvidia-glx packages specify different NVIDIA driver versions.  Looks like nvidia-glx-new specifies 1.0-9755, nvidia-glx specifies 1.0-9631.  But when I install those drivers, it tells me that it wants 1.0-7184 when I reboot!

Does anyone have any ideas?  On either the kinit problem or on my X problem?

---

### Post by Lutin on 2007-06-21
I too am having problems with an apparent mismatch of nvidia drivers. I am using Edgy (6.10) and had managed to manually install the nVidia binary driver version 1.0-9755. Everything was working fine. Then I did an update via my newly installed ADSL/Broadband connection and now Ubuntu will not start straight into the Gnome desktop.

Now when the machine starts up it gives an error "Failed to start the X server.....". Inspecting the error log gives this - "nvidia kernel module has the version 1.0-7184 but this X module has the version 1.0-9755....".

However, if I start the system in Recovery Mode and then do /etc/init.d/gdm stop

then, rmmod nvidia

then, modprobe nvidia

and finally /etc/init.d/gdm start

the nvidia spalsh screen comes up as it used to, the Gnome desktop log in comes up and I'm back into the desktop. But, there are two error message boxes - "CPU fequency scaling unsupported" (it was okay previously) and "Internal error - failed to initialize HAL". Other than that I am back where I was before.

Hopefully, this will help someone with more knowledge than I have to point me in the direction of a solution. Thanks in advance.

---

### Post by charles.figura on 2007-06-21
Lutin -

Your comments did the trick.  I tried your rmmod/modprobe idea (should have thought of that before) and x started up just fine, but again, when rebooting, same old thing happened.  Ok, rmmod/modprobe again,I went into synaptic, made sure that the old versions (nvidia-glx, nvidia-glx-legacy) were removed (complete removal), rebooted - no joy, same thing.  One more time - this time, go into
/lib/linux-restricted-momdules/2.6.20-16-generic (or whatever kernel you're running is), and look around.  I had three separate directories in there - nvidia, nvidia_legacy, and nvidia_new.
Got rid of nvidia and nvidia_legacy, left nvidia_new.

Works like a charm now.  Boots just fine.

Good luck!

---

### Post by Lutin on 2007-06-22
Charles

Thanks fof the tip. I too found an nvidia-legacy sub-directory. Deleted it as you suggested and now back to where I was, but with an updated system.

Thanks again for the tip. Happy Ubuntu-ing:D

---

### Post by Mad_Max_1412 on 2007-07-04
> **Lutin said:**
> I too am having problems with an apparent mismatch of nvidia drivers. I am using Edgy (6.10) and had managed to manually install the nVidia binary driver version 1.0-9755. Everything was working fine. Then I did an update via my newly installed ADSL/Broadband connection and now Ubuntu will not start straight into the Gnome desktop.

Now when the machine starts up it gives an error "Failed to start the X server.....". Inspecting the error log gives this - "nvidia kernel module has the version 1.0-7184 but this X module has the version 1.0-9755....".

However, if I start the system in Recovery Mode and then do /etc/init.d/gdm stop

then, rmmod nvidia

then, modprobe nvidia

and finally /etc/init.d/gdm start

the nvidia spalsh screen comes up as it used to, the Gnome desktop log in comes up and I'm back into the desktop. But, there are two error message boxes - "CPU fequency scaling unsupported" (it was okay previously) and "Internal error - failed to initialize HAL". Other than that I am back where I was before.

Hopefully, this will help someone with more knowledge than I have to point me in the direction of a solution. Thanks in advance.

I've got the same error (nvidia kernel version 1.0-7184 but x module is 1.0-9755) I would like to try your idea but firstly I need to know who to start in Recovery Mode.  I'm a newbie so I probably need more detailed instructions than a competent user.

---

