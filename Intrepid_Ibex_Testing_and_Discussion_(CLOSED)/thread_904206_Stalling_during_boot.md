---
title: "Stalling during boot"
date: 2008-08-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2008-08-29
Since the upgrade to the kernel is anyone else getting a problem with intermittent stalling during boot?

The boot process seems to run for an indeterminate time before stopping. The screen remains with the orange bar somewhere along the track. After a few attempts the boot will happen normally.

PC

---

### Post by plun on 2008-08-29
This bug got me this morning.

**Parallel fsck breaks boot when / is being fsck'd**

[https://bugs.edge.launchpad.net/ubuntu/+source/sysvinit/+bug/255563](https://bugs.edge.launchpad.net/ubuntu/+source/sysvinit/+bug/255563)

Mismatch with fsck and boot.

---

### Post by Foaming Draught on 2008-08-29
> **plun said:**
> 
**Parallel fsck breaks boot when / is being fsck'd**
Talk about onomatopoeia  :)

---

### Post by Gina on 2008-08-29
I'm getting that on my laptop - not seen it on my desktops (yet).  I'm on the point of checking out Intrepid on my laptop (when I have time) so this is a good starting point.  I haven't left it running Intrepid startup long enough for fsck to finish (thinking it had crashed), wanting to actually use the machine.  I just hold down the power button to abort the boot and then boot into Hardy.

---

### Post by caryb on 2008-08-29
Not related to kernel upgrade but mine stalls at configuring network for 2 minutes on every boot since Hardy. Because network mangler doesn't work on Kubuntu I need to have entry in the /etc/network/interfaces file for my wireless settings to get it to work.


Cary

---

### Post by roja on 2008-08-29
Yes, I have experienced this for a while, and since the last update tapping of the touchpad isn't working but the buttons are.

---

### Post by caryb on 2008-08-29
I can confer that the touchpad doesn't work on taping.


Cary

---

### Post by Peter09 on 2008-08-29
Looking further:

1. There is no disk activity when stalled.
2. After 4-5 failures to boot I remove the quiet option from the boot line. I did not get any text output, just the normal graphical boot, and it succeeded..... not sure if this was a one off or not.
3. I am getting some boots where I cannot connect to the wireless network, it requires a reboot to connect... is this related?

PC

---

### Post by Gina on 2008-08-29
Just run the update from Synaptic and now have kernel 27 (on P4 desktop).  Startup stalls early on for some time then - after many minutes - continues on in text mode but stops at "Starting Bluetooth" where it appears to hang forever (left it nearly an hour).  Crtl-Alt-Del starts shutdown and the text shows various things shuuting down until it gets to "Stopping Bluetooth" where even the shut down stops.  Ctrl-Alt-Del restarts the shutdown but again it stops dead at "Stopping Bluetooth".  Only a power-off will get out of it.

---

### Post by jbernardo on 2008-08-29
I've seen the stalling during boot on my Aspire One. Since I have the bootsplash disabled, I can see it hangs at the "Setting System Clock" log entry. When I remove the "Quiet" entry, it no longer hangs.

---

### Post by beartard on 2008-08-29
> **Gina said:**
> Just run the update from Synaptic and now have kernel 27 (on P4 desktop).  Startup stalls early on for some time then - after many minutes - continues on in text mode but stops at "Starting Bluetooth" where it appears to hang forever (left it nearly an hour).  Crtl-Alt-Del starts shutdown and the text shows various things shuuting down until it gets to "Stopping Bluetooth" where even the shut down stops.  Ctrl-Alt-Del restarts the shutdown but again it stops dead at "Stopping Bluetooth".  Only a power-off will get out of it.
That's exactly what I'm getting.  I can't boot into the new kernel.

---

### Post by BanjoBoy on 2008-08-30
> **beartard said:**
> That's exactly what I'm getting.  I can't boot into the new kernel.

Me too, on a Presario 2825 laptop.

Bent

---

### Post by Peter09 on 2008-08-30
I have looked at my system (Toshiba Satellite Pro) a bit further.

I discovered that the quiet option is appearing twice in the grub boot lines, once by itself and once in the initial boot line. Removing those and putting nosplash in allows me to see where it stalls. It appears to be consistent at the line.

sr 1:0:0:0 Attached scsci generic sg1 type 5

This appears to be an initialization problem as once it has succeeded it will boot ok. Performing a shutdown (rather than a power off) seems to put it back to 'problems'.

PC

---

### Post by Gina on 2008-08-30
Just tried updating again from kernel 26.5 using Synaptic and it's worked (now with kernel 27-2).  First restart failed to find /home but second time it started up fine - running it now on my P4 system.  Also updated my AMD64 system last night and that too installed kernel 27-2 and all booted up fine.

---

### Post by beartard on 2008-09-01
I think the new kernel is doing an fsck in the background on boot and won't find /home till that's finished.  If I'm right, I may have had to mount the partition manually the second time round.  The *-2 kernel enabled me to boot just fine, but I had to clear out old nvidia drivers first.

---

