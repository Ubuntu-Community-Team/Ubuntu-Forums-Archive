---
title: "pvrusb2 not working in Intrepid Ibex (Hauppauge TV device)."
date: 2008-09-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by BanjoBoy on 2008-09-23
After upgrading to Intrepid Ibex (linux-2.6.27-4-generic and all previous 2.6.27 kernels) my Hauppauge WinTV USB2 device stopped working (using v4l and pvrusb2 kernel modules). If I attach the Hauppauge device the boot hang/freezes at "Starting bluetooth", if connecting it after the boot the pvrusb2 module never loads the device firmware and does not get the devices (/dev/video0 or /dev/radio0) up and running.

If I boot into kernel 2.6.26-5 it works.

Any advice on how to get it working in this new kernel/Ubuntu?

I have tried to create a bug report, but no one is helping, only one confirms the problem.

---

### Post by beartard on 2008-09-24
It's a known bug in the kernel that Ubuntu is shipping with Intrepid right now.  The status is "triaged" and of "medium" importance at launchpad, but I can't remember which bug it is right now.

I've asked about it on the linuxtv mailing list and have done some testing, only to find it's a problem with the current kernel, which is about as pre-release as you can get.  Hopefully the Ubuntu kernel team gets it worked out before the release date.  Other than that, the only other solution is to compile a custom kernel or use a 2.6.26-series kernel.

---

### Post by BanjoBoy on 2008-09-24
> **beartard said:**
> It's a known bug in the kernel that Ubuntu is shipping with Intrepid right now.  The status is "triaged" and of "medium" importance at launchpad, but I can't remember which bug it is right now.

I've asked about it on the linuxtv mailing list and have done some testing, only to find it's a problem with the current kernel, which is about as pre-release as you can get.  Hopefully the Ubuntu kernel team gets it worked out before the release date.  Other than that, the only other solution is to compile a custom kernel or use a 2.6.26-series kernel.

The link is [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262927]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262927").

I have done some testing and found that: I boot without the pvrusb2, then connect after login and it does NOT load the firmware into the Hauppauge device as it should. If I then turn on my external USB HDD it will not register, so maybe the problem is in the usbcore module, like the usb devices are not registered anymore. Normally at every connect/disconnect the usbcore with log a message, but the does not happens anymore.

I reboot again without both pvrusb2 and usb hdd connected, then connect the usb hdd, it register and works, then connect the pvrusb2 and now the firmware loads, but still does not work and create the /dev/video0 and /dev/radio0 devices.

---

### Post by beartard on 2008-09-24
The reason it does not create the devices in /dev is that the 1950 isn't re-loaded by the kernel properly after the firmware is loaded.

The way it works is like this:
1. device connects
2. kernel detects it
3. pvrusb2 loads firmware to the 1950
4. device is disconnected
5. device is reconnected with the firmware loaded
6. seeing a device with proper firmware, the kernel modules create the device nodes in /dev.

Something with the new ubuntu kernel messes up that last step.  It's a kernel problem, pure and simple, and the dev team are aware of it.  I've e-mailed Mike Iseley and Michael Krufky (linuxtv driver devs) about the problem and they agree.  You've done the right thing in filing a bug.  Unfortunately, it's one of those things we have to wait for the kernel team to work out...hopefully by next month.

---

### Post by BanjoBoy on 2008-09-24
> **beartard said:**
> The reason it does not create the devices in /dev is that the 1950 isn't re-loaded by the kernel properly after the firmware is loaded.

The way it works is like this:
1. device connects
2. kernel detects it
3. pvrusb2 loads firmware to the 1950
4. device is disconnected
5. device is reconnected with the firmware loaded
6. seeing a device with proper firmware, the kernel modules create the device nodes in /dev.

Something with the new ubuntu kernel messes up that last step.  It's a kernel problem, pure and simple, and the dev team are aware of it.  I've e-mailed Mike Iseley and Michael Krufky (linuxtv driver devs) about the problem and they agree.  You've done the right thing in filing a bug.  Unfortunately, it's one of those things we have to wait for the kernel team to work out...hopefully by next month.

It's not at the last step, because when it happens the whole usb system are messed up and it's not possible to connect/disconnect any usb devices anymore, so I think it at step 5 - the reconnect - the usbcore register the disconnect, but not any usb connects from any device, not just the pvrusb2, see my bug report <[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274159]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274159")> and <[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262927]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262927")>.

---

### Post by beartard on 2008-09-25
I just don't see the need for filing a duplicate bug report for a problem that's already been acknowledged by the kernel team.  They certainly know it's a problem.

---

