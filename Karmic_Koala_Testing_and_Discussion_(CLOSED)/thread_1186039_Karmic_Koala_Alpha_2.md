---
title: "Karmic Koala Alpha 2"
date: 2009-06-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hachaboob on 2009-06-12
Hi,

Everything seems to work quite well running from the Live CD until you actually install it.

Apart from issues getting grub installed the latest release of Karmic Koala works almost flawlessly with the Macbook 5,1. The following works out of the box:
* Trackpad with horizontal scrolling etc
* Volume adjustment 
* Previous track, Play/Pause, Next track keys in Rhythmbox
* Eject

What does not work without manual intervention:
* Audio
* Fan
* Wireless must be disabled/enabled again after Suspend to reconnect

**Screen Brightness Adjustment**

Install the nvidia-bl-dkms package from the Jaunty Mactel PPA

**Hotness**

You may want to manually set the RPM of the fan but I have found that installing the 185 NVidia driver seems to reduce the hotness using the very scientific Touch Test.

**Wireless**

1. Remove the built-in Broadcomm driver using "Hardware Drivers"
2. Edit /etc/modprobe.d/blacklist.conf and add the following:

```

blacklist b43
blacklist b43legacy
blacklist ssb

```

3. Install b43-fwcutter using Synaptic. It downloads the b43 firmware.

4. Download the attached Broadcomm STA driver (64 bit version) to ~/Downloads. I would have liked to provide the patched version of the driver but the license doesn't allow for distributing a modified version of it.

5. Create a new folder called "~/Downloads/hybrid-portsrc-x86_64-v5_10_91_9" and extract the contents of hybrid-portsrc-x86_64-v5_10_91_9.tar.gz to it.

6. Download the attached patch file to ~/Downloads and Patch the driver to allow it to compile against the 2.6.30 kernel:

```

cd ~/Downloads
patch -p0 < broadcom-sta-5.10.91.9-linux-2.6.30.patch.txt

```

7. Make and move the newly created LKM wl.ko to the right place and make it findable by modprobe:

```

cd ~/Downloads/hybrid-portsrc-x86_64-v5_10_91_9
make -C /lib/modules/2.6.30-9-generic/build M=`pwd`
sudo mv wl.ko /lib/modules/2.6.30-9-generic/kernel/drivers/net/wireless
sudo depmod

```

8. Edit /etc/modules and add the following:

```

wl

```

9. Reboot and hopefully you now have some battery draining wireless action!
 
That is all I have checked out so far as I haven't been using it for too long.

---

### Post by cyberdork33 on 2009-06-15
interesting patch. Is this submitted with a bug report anywhere?

---

### Post by hachaboob on 2009-06-16
Not that I am aware of. Its a patch I found on the Ubuntu Forums I think.

Wireless still is a bit flakey authenticating with WEP though.

---

### Post by cyberdork33 on 2009-06-16
> **hachaboob said:**
> Not that I am aware of. Its a patch I found on the Ubuntu Forums I think.

Wireless still is a bit flakey authenticating with WEP though.
I'd suggest filing a bug then, and attach the patch. That will get it started on the road to being included with Karmic.

---

