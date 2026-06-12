---
title: "Which nVidia package to install?"
date: 2013-04-25
forum: Installation &amp; Upgrades
---

### Post by PeterTaps on 2013-04-25
Folks,

In the past, I use to install "nvidia-current" as the package for my nvidia card. Now, I am building a new system and plan to have XBMC on it.

XBMC wiki suggests the following:

[COLOR=#000000][FONT=sans-serif][FONT=monospace]
[COLOR=#C20CB9]**apt-cache search**[/COLOR] nvidia **|** [COLOR=#C20CB9]**grep**[/COLOR] glx[/FONT]
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Looking at the listed versions from the command above enter the following command substituting 185 if you desire a different version:[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif][FONT=monospace]
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-get install**[/COLOR] nvidia-glx-185 nvidia-settings mesa-utils libvdpau-dev[/FONT]
[/FONT][/COLOR]

I just installed Ubuntu 13.04 minimal server.

When I search for glx package, it returns "glx-alternative-nvidia" to me. There is no nvidia-glx-nnn package.

Should I install "nvidia-current" or "glx-alternative-nvidia" package?

Regards,
Peter

---

### Post by oldfred on 2013-04-26
I do not have minimal, but what do these show. Not sure if sudo needed or not.

 #To see available versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*

---

### Post by papibe on 2013-04-26
Hi PeterTaps.

Could you post the result of these commands?
```
lspci -nnk | grep -iA2 vga

sudo lshw -C display
```

AFAIK, you need 2 packages: the proper driver and libvdpau1.

Regards.

EDIT: libvdpau1 is the good one. vdpau-va-driver is optional.

---

### Post by PeterTaps on 2013-04-26
Thank you for your help.

For now, I have installed "nvidia-current."

Here is the output of lspci -nnk | grep -iA2 vga

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF116 [GeForce GTS 450 Rev. 2] [10de:1245] (rev a1)
        Subsystem: ZOTAC International (MCO) Ltd. Device [19da:3178]
        Kernel driver in use: nvidia

And here is the output of sudo lshw -C display

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF116 [GeForce GTS 450 Rev. 2] [10de:1245] (rev a1)
        Subsystem: ZOTAC International (MCO) Ltd. Device [19da:3178]
        Kernel driver in use: nvidia


Regards,
Peter

---

### Post by papibe on 2013-04-26
Then, you need to make sure you have the vdpau driver installed:
```
sudo apt-get install libvdpau1
```
That should do it.

Let us know how it goes.
Regards.

NOTE: XBMC and S/mplayer can work directly with libvdpau1. You may install vdpau-va-driver if you are going to use VLC.

---

### Post by PeterTaps on 2013-04-30
Thank you for your help. I have now installed both libvdpau1 and vdpau-va-driver.

Regards,
Peter

---

