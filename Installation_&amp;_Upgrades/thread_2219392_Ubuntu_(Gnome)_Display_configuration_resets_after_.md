---
title: "Ubuntu (Gnome): Display configuration resets after reboot/logout"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by damien_d on 2014-04-23
Dear all,

I have just upgraded from 13.10 to 14.04.  I have a triple monitor setup using an AMD/ATI HD7700:

```

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde PRO [Radeon HD 7750 / R7 250E]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]

```

Under 13.10 (and previous versions), I was using the proprietary drivers. Currently in 14.04, these drivers are giving me grief (see [1]), so I am switching to the FOSS Xorg drivers. Besides, now that the device is supported, it is nice to do the "right thing" :) 

I used the "additonal drivers" tool to change to the Xorg driver. GNOME reports that it is using the Gallium driver (as expected).   My problem comes when configuring the displays.

By default, the screens are not configured in the desired order. I can use the "Screen Display" tool to rearrange the screens to the desired configuration and have them applied correctly.

When I log out or reboot, this configuration is not kept.  Instead, when logging in, the screen flashes a couple of times as though it is trying to find the right display driver.  Gnome-shell then appears as normal with the default configuration.

Is there a way I can prevent the display from resetting each time I logout/login?  It is rather annoying and (as a separate issue) the bottom panel shell extension I have installed disapears when reconfiguring the screen. Accordingly, the workaround of simply adjusting the display each time is not desirable.

  -- Damien







[1] [http://askubuntu.com/questions/453999/ubuntu-14-04-gnome-ati-amd-hd7750-proprietary-drivers-not-workin](http://askubuntu.com/questions/453999/ubuntu-14-04-gnome-ati-amd-hd7750-proprietary-drivers-not-workin)

---

