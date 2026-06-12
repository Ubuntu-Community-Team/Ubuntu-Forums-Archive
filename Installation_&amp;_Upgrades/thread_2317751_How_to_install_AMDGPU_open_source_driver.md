---
title: "How to install AMDGPU open source driver?"
date: 2016-03-19
forum: Installation &amp; Upgrades
---

### Post by spectatorx on 2016-03-19
I'm reading some interesting news about AMDGPU open source driver and i would like to give it a try but it is not so easy to find any info on how to install it, could anyone provide me any instructions?
Also, does it require specific kernel version like fglrx or can i install latest kernel and use it with AMDGPU driver? My gpu is radeon r9 380 4GB.

---

### Post by sandyd on 2016-03-19
Only natively supported in Ubuntu 15.10 at the moment.:
```

sudo apt-get install xserver-xorg-video-amdgpu libdrm-amdgpu1
```

Reboot, and check the Xorg logs to see if it loaded.

FGLRX must be removed prior to installing. If you have installed fglrx in the past, ensure that /etc/X11/xorg.conf is removed.

---

### Post by spectatorx on 2016-03-20
Yesterday i have installed this driver following its instructions:
[http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Beta-Driver-for-Vulkan-Release-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Beta-Driver-for-Vulkan-Release-Notes.aspx)
After reboot screen goes into standby mode and doesn't wake up when system desktop is loaded already (i know it is loaded because i can hear system startup sound). I'm not sure what causes this, from my experience i assume it may be related to my crt display connected to gpu with vga/d-sub cable and dvi->d-sub adapter.

After cleaning system off this driver (sudo amdgpu-pro-uninstall) i tried your suggestion. System boots ok, display wakes up on load, checked xorg logs and driver seems to be running but steam is unable to start(visible in running processes but i do not see its interface).

Currently i came back to fglrx provided by system. Anyway, thanks for your answer :-)

P.S.
To be specific all this is going on on xubuntu 15.10 amd64, amd fx-8320, gigabyte r9 380 G1 4GB.

---

### Post by grahammechanical on 2016-03-20
You should read this. In fact everyone using AMD/ATI video adapters should read these. Things are going to get worse before they get better.

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)

[http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04](http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04)

[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-March/016315.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-March/016315.html)

[URL="https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/"]https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/

[/URL]Regards

---

### Post by spectatorx on 2016-03-20
Thx for links, i've read about it already as soon as this was published.

Little off-topic, soon, within 2-3 weeks i will finally switch display to lcd panel with 1920x1080 resolution, freesync and i'm going to have it connected via display port. Any known issues with amd cards and display port on both, fglrx and open source drivers?

---

### Post by grahammechanical on 2016-03-20
You say that you presently have a CRT monitor? Well, when you switch to a digital display and connect via HDMI/Display Port you should find that Sound Settings will give you an output option to play sound through the video adapter to the speakers in the monitor. At least it does with my Nvidia card.

Regards

---

### Post by spectatorx on 2016-03-20
The display which i am going switch to is samsung S24E370DL, it doesn't have built-in speakers so this doesn't apply to this case :-)

My crt is lg f700b, old, still working and rocking! :D

---

### Post by mastablasta on 2016-03-21
you still have the output available. it might have a plug for speakers.

in any case thpse with sliglty older Radeon models (like me) are not going ot have it easy. the RAdeon driver is still 20-30 % worse, AMDGPU will not support these chips aynway.

---

### Post by P-I H on 2016-03-21
I think there are 2 ways to use amdgpu, either to upgrade/install the development version of Ubuntu 16.04, or to follow this instruction to install amdgpu-pro on Ubuntu 14.04.04.
[http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Beta-Driver-for-Vulkan-Release-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Beta-Driver-for-Vulkan-Release-Notes.aspx)
There is also information on this site
[http://www.phoronix.com/scan.php?page=article&item=amd-gpu-pro&num=1](http://www.phoronix.com/scan.php?page=article&item=amd-gpu-pro&num=1)

I'm using the development version of Ubuntu 16.04, which works fine on a Radeon R9 380 4GB.

---

### Post by spectatorx on 2016-04-13
I got new display which i mentioned in my posts in this thread, plugged it with display port cable, now everything works properly with amd gpu-pro driver, desktop wakes up after boot and no issues which were present before.

---

