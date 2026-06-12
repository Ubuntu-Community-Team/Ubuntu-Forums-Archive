---
title: "Compiz misbehaving on Radeon 9000 Mobility"
date: 2010-03-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by blueturtl on 2010-03-14
When ever I zoom in using the magnifying glass tool (or out to view all the workspaces simultaneously) the screen goes really dark, almost like there was no backlight on. This also happens when I switch between workspaces (for the duration of the switching). When viewing the desktop at regular zoom level everything is ok.

The display brightness controls still work when the image is dark, but even the brightest setting is too dim to be usable.

This is on a Dell Latitude D600 notebook.

Has anyone else experienced a similar issue?

---

### Post by blueturtl on 2010-03-14
Seems to be a kernel issue because while testing resume/suspend with the mainline kernel, this issue is gone.

---

### Post by blueturtl on 2010-03-15
Well I went and filed a bug report and while I was filling in the required attachments the problem seems to have fixed itself.

For those who want to read the full bug report it is here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539163](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539163)

The way I fixed the problem was I first added the "nomodeset" to the default boot parameters in
/etc/default/grub

I then did a sudo update-grub and rebooted.

Brightness worked but the display got corrupted so I removed the "nomodeset" from the parameters, updated grub once again, rebooted -- and now the issue seems to have vanished. :confused:

*What* is going on here?!

---

### Post by Seren on 2010-03-15
Since today, I can't boot with

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

Plymouth freeze, and I can't even start in rescue. Appending "nomodeset" to the kernel command line solve temporarily the problem (thank to this thread for the idea).

As you said something is probably broken in the driver or the kernel.

I remember updating xserver-xorg-video-ati last night...and few other related X packages.

---

### Post by blueturtl on 2010-03-16
Apparently this modesetting thing is a new kernel feature:

[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

### Post by blueturtl on 2010-03-24
Can anyone on a Dell D600 confirm this bug? I would like to make sure I don't have a faulty machine here.

edit: There is a link to my bug report a few posts back, under it you will find video capture of the bug that you can compare to see if your symptoms are the same.

---

### Post by blueturtl on 2010-04-24
And the solution was... drumroll please:

Go to Compiz settings, General settings, deselect Lighting.

It is a video driver bug.

---

### Post by BrokeMahPC on 2010-04-24
My screen goes dark if I try to use the rain effect, it doesn't rain, - you have to deselect water effects to return it to normal.
I'm told this is also a video driver bug. Tried turning of lighting to see if that had any effect - nope!

---

