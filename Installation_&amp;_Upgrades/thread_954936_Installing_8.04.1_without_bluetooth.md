---
title: "Installing 8.04.1 without bluetooth"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by Ole Juul on 2008-10-21
How do I install Kubuntu 8.04 without bluetooth? Is there a way, or do I have to buy a bluetooth device in order to install this version? I ask because there seem to be many others with the same problem and no solution that I could find :). If it is not possible to do it, I would like to know.

---

### Post by cariboo on 2008-10-21
What problems are you having with Bluetooth. The bluetooth files installed are part of the default installation, If you don't have any bluetooth devices the service isn't enabled.

Jim

---

### Post by Ole Juul on 2008-10-21
Thankyou Jim for responding. This computer has no bluetooth devices but has a parallel port printer, non-wireless USB devices, and ethernet. It has an AMD Semperon 3300+ with Award BIOS and 2GB RAM.

This desktop has been running MS-XP-SP3 (which I know nothing about:( ) and I just added a 500GB harddrive so the person could use Linux and still access their old files on the original drive and thus make an easy transition.

When I try to install Kubuntu 8.04.1 it just hangs at a point where it is searching for Bluetooth devices. Perhaps there is a version of Kubuntu without the (apparently broken) Bluetooth enabled?

---

### Post by louieb on 2008-10-21
More likely its a bad CD burn. It just takes a few twisted bits in the wrong place to give some weird results.  
Run the check media for defects option.
Burn the iso at slow speed - I usually burn an iso at 2x and no faster that 4x.

---

### Post by Ole Juul on 2008-10-21
Thanks. I'll burn another ISO at slow speed and report back.

---

### Post by Ole Juul on 2008-10-21
I just burnt another CD at 2X, ran "checkCD" upon booting in the host (XP) computer, and clicked install. Same thing. It hangs on starting Bluetooth. At that point I hit Ctrl-C, just in case it would help it move on, but it's just stuck there.

Any other suggestions? Perhaps install an earlier version and upgrade.... I'm stumped.:confused:

UPDATE:
1.   After unplugging ALL USB periferals and using a PS2 keyboard, I got the same result.
2.   I then tried to load 6.06.1 instead, hoping to upgrade from there. That too was unsuccesful but gave a few more hints. It failed on "Loading hardware drivers ..." and instead of hanging on "Starting Bluetooth services ..." it hung right after that on "hcid sdpd". I don't know what that means and since it was hung, I gave it the three finger salute. Upon stopping services, it hung on "Stopping Bluetooth services ...".
3.   I have a feeling that this is not a Bluetooth problem as such. Perhaps this AMD processor, or mother board, or BIOS, is just not compatible with Linux and is doomed to run XP - though it does seem unusual to have to buy a new MB just to install Linux.
4.   Thanks to those that responded. :) I will rephrase the question in a more meaningful manner and repost soon.

---

### Post by Henk Koekoek on 2008-12-07
> **Ole Juul said:**
> When I try to install Kubuntu 8.04.1 it just hangs at a point where it is searching for Bluetooth devices. Perhaps there is a version of Kubuntu without the (apparently broken) Bluetooth enabled?

I have the exact same problem, with Ubuntu 8.10.

I'm trying to run Ubuntu without installing, on a computer with Windows XP installed, but it hangs on the same point as Ole Juul.

I've burned two cd's, both failed. I also have the same error when cancelling as Ole Juul in his update (pt. 2): "Upon stopping services, it hung on "Stopping Bluetooth services ...""

---

### Post by Blizzo on 2008-12-10
> **Henk Koekoek said:**
> I have the exact same problem, with Ubuntu 8.10.

I'm trying to run Ubuntu without installing, on a computer with Windows XP installed, but it hangs on the same point as Ole Juul.

I've burned two cd's, both failed. I also have the same error when cancelling as Ole Juul in his update (pt. 2): "Upon stopping services, it hung on "Stopping Bluetooth services ...""



Same problem here, I installed Ubuntu 8.10 inside Vista, it stops at ''Starting Bluetooth'' nothing I can do except hit the power button it seems...then it freezes at ''Stoping Bluetooth''

Tried 2 cd's for 8.10 and tried 8.04 as well....

Confused Linux n00b here...

---

### Post by Henk Koekoek on 2008-12-10
> **Blizzo said:**
> Same problem here, I installed Ubuntu 8.10 inside Vista, it stops at ''Starting Bluetooth'' nothing I can do except hit the power button it seems...then it freezes at ''Stoping Bluetooth''

Tried 2 cd's for 8.10 and tried 8.04 as well....

Confused Linux n00b here...

I got it to work by disconnecting all usb-devices, letting Ubuntu load, and reconnect them.

---

