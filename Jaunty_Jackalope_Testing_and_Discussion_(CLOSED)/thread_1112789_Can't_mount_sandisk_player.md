---
title: "Can't mount sandisk player"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2009-04-01
Gremlins are coming out of the woodwork now for me, it seems.

Usually I have no problem with my sandisk player but it won't mount in Jaunty. It just disconnects immediately.

Apr  1 07:28:39 adam-desktop kernel: [ 2252.321686] usb 2-1.5: USB disconnect, address 6
Apr  1 07:28:45 adam-desktop kernel: [ 2258.920099] usb 2-1.5: new high speed USB device using ehci_hcd and address 7
Apr  1 07:28:46 adam-desktop kernel: [ 2259.068340] hub 2-1:1.0: unable to enumerate USB device on port 5
Apr  1 07:28:56 adam-desktop kernel: [ 2269.932808] usb 2-1.5: new high speed USB device using ehci_hcd and address 8
Apr  1 07:28:58 adam-desktop kernel: [ 2271.200526] usb 2-1.5: configuration #128 chosen from 1 choice
Apr  1 07:28:58 adam-desktop kernel: [ 2271.224537] scsi7 : SCSI emulation for USB Mass Storage devices
Apr  1 07:28:58 adam-desktop kernel: [ 2271.224877] usb-storage: device found at 8
Apr  1 07:28:58 adam-desktop kernel: [ 2271.224880] usb-storage: waiting for device to settle before scanning


I have had this problem before a long time ago with previous Ubuntu versions but was fixed in the updates.

---

### Post by Nisuspi on 2009-04-01
I have a similar problem with mine - but I can usually get it working by unplugging it and switching the USB Mode on the player (under settings) to MTP, rebooting the player and then changing it back to MSC again.

---

### Post by gnomeuser on 2009-04-01
If you have the verison of hal-info installed mentioned here:
[https://bugs.edge.launchpad.net/ubuntu/+source/hal-info/+bug/345249](https://bugs.edge.launchpad.net/ubuntu/+source/hal-info/+bug/345249)

Then all the ground work should be in place, that being said there is something profoundly screwed up with regards to the Sansa Fuze in Jaunty. I tested mine with Jaunty yesterday it while it mounted and was detected using MTP copying files over using banshee (libmtp) failed horribly in most cases.

Same is not true for Fedora 11, so I suspect it is time to dig for that difference causes this.

---

### Post by sonicb00m on 2009-04-01
> **Nisuspi said:**
> I have a similar problem with mine - but I can usually get it working by unplugging it and switching the USB Mode on the player (under settings) to MTP, rebooting the player and then changing it back to MSC again.

I did try that but it didn't work.

I can get rhythmbox to connect to the player in MTP mode and play file (but the tag info isn't being read).

It still won't mount and neither can i force it to mount as the device isn't appearing in /dev/

---

### Post by sgosnell on 2009-04-01
Lots of things that worked in the alphas seem to have been broken in the beta.  I've resisted installing the beta on anything I need.  I did try running the live CD, and wireless doesn't work.  I didn't try my Fuze, but it does work on alpha 6, and on the .29 kernel.  Looks like the dev team has a lot of work to do getting things back right.  I think I'm going to stay on the .29 kernel, where everything works.

---

### Post by Brandel Valico on 2009-04-05
Was able to get mine mounted. Not sure exactly what made it start to do so. I installed Amarok,Banshee,and Qlix all in an attempt to do so. I installed them in the above order and it wasn't until the last one I was able to have it auto mount by leaving it plugged in and turning it off then back on. Now it auto mounts perfectly (have yet to do a reboot to see if it will do so then also) Again I'm unsure why this worked but hopefully it can help point more knowledgeable people in the right direction

Forget to mention my Sandisk is the sansa version vo1.01.11a it shows up in my lsusb list as SanDisk Corp. Sansa Clip (mtp)
having played around some more I can confirm that it seems to be Qlix that did it. As after a reboot I had to open Qlix and while it was attempting to detect my player again turn it on and off to have it mount it properly.

---

### Post by sonicb00m on 2009-04-10
[https://bugs.launchpad.net/ubuntu/+bug/345916](https://bugs.launchpad.net/ubuntu/+bug/345916)

Removing the file talked about here worked for me.

---

